# Vagrant Linux Development Environment

**Work in progress** This repository will be updated with useful features as time permits. Any and all feedback is appreciated.

Often times, developers would like to easily access a Unix/Linux environment to use the vast array of tools available on those platforms. The amount of power available from those tools allows developers to learn new things, disseminate knowledge, create more useful tools and libraries, and build rock-solid software. Unfortunately, developers with a Windows computer might find it more difficult to access such an environment. There are plenty of solutions out there that can ameliorate the difficulty:
   - VirtualBox - create a virtual machine to use whenever you need a Unix/Linux environment
   - Vagrant - quickly provision a virtual machine to use for development
   - Cygwin - a collection of GNU and open source tools which provide functionality similar to a Linux distribution, plus a POSIX emulation layer
   - Windows Subsystem for Linux (Bash on Windows) - an implementation of Linux syscalls by Microsoft in order to run a full Linux bash

Each of these options has pros and cons, and probably the most preferred option is Bash on Windows. The danger, however, is that since its a work in progress by Microsoft, there's always a chance that it won't have the functionality a developer might need - simply because the Linux syscall hasn't been implemented yet. 

This project uses Vagrant to build a Linux Development Environment (LDE) for Windows 10 users and makes use of other open source tools to create a smooth workflow. It's streamlined for a workflow where:
   - the user writes code using a text editor directly on Windows
   - the user can use Linux tools inside Vagrant to compile their code or perform other tasks

These goals are based off my experience writing side projects and as an undergrad at Cornell University, where some courses and project teams are, by nature, not geared towards Windows 10 users. Since this is based off of Vagrant, this solution should work on Windows 7, 8,  8.1 and 10. Known differences have been accumulated in the **Install** section, based off of user feedback. In addition, there's install steps for macOS/OS X users who are looking for something similar to what this offers.

## What does this add?

This project adds (at minimum) to following to your Windows computer:
   - VirtualBox - for running your LDE inside a virtual machine
   - Vagrant - to provision your LDE and manage some startup tasks

VirtualBox and Vagrant together build virtual machines where fine-tuning development environments can be kept separate from your main operating system install.

## Install

1. Install **VirtualBox** and the **VirtualBox Extension Pack** from [it's website](https://www.virtualbox.org/wiki/Downloads)
2. Install **Vagrant** from [it's website](https://www.vagrantup.com/)
   * **Note**: On Windows 7, Vagrant will hang during usage if PowerShell is not up to date. There's two options to alleviate the issue
      * You can upgrade PowerShell to it's most recent version before installing Vagrant (the most recent version). (*preferred*)
      * You can install Vagrant 1.9.6.
3. Open your terminal and run the following
   ```
   vagrant plugin install vagrant-vbguest
   vagrant plugin install vagrant-ansible-local
    ```
4. Clone this repository
5. `cd` into the repository and run the following commands:
   ```
   vagrant up
   vagrant reload
   ```

## How do I use this?

After completing steps 1 - 3 of the install process, you can repeat steps 4 and 5 as often as you'd like to setup a new LDE for a new project.

Once the LDE is fully provisioned, simply `vagrant ssh` and use the machine as you please. If you would like to have files on your system available to the VM, drop them into the LDE's folder - the directory is automatically shared inside the LDE at the **/vagrant** folder.

## Extra functionality

Look in the **extra** folder for guides on how to setup some extra features for your LDE.