---
title: "Help with AM1771"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by thetruth on 2006-07-04
Hi guys

This is my first post.

I have been a Windows user for many years and now I decided to switch . I am new to Linux and thanks to my Brother in France  he helped me with few tips and Since then over 2 weeks now I can say that LINUX is the best OS. it has not crached  and even my young son refuse to go back to Windows and thank God i do not have to hear  him screaming "Daddy MY PC crashed lol".
I have one problem with my PC Wireless. it has a min-pci AM1771. I hav efound the driver but can not install it

I got stucked at this
-==================
1.2) Loading the device driver

      A) Copy the device driver and applications into a directory on the machine to be used
         (Nautilus.o, Nshell and HttpServer).
How and where?????????????????????
========================================
this my output on (lspci) on terminal 
0000:02:02.0 RF controller: Advanced Micro Devices [AMD] Am 1771 MBW [Alchemy] ( rev 04)
tihad@tihad-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

-==========================================

This is the full installation readme.txt
Thanks

MY laptop is working fine with wireless after changing bits and pieces and I would really love to have the PC wireless aswell.
Please remember i am newbie
Kind regards
------------------------------------------------------


I. Installation
---------------

 1.1) Installation on the target machine

      Untar the Nautilus Linux ``tgz'' file:

          $> tar -xvzf source_linux_ST6.0.tgz

      This will generate the following directories:

          source_linux_ST6.0/Include/
          source_linux_ST6.0/Linux/
          source_linux_ST6.0/MacCore/
          source_linux_ST6.0/Tools/
          source_linux_ST6.0/Applications

      Login as super user on the machine where the driver shall be installed and started
      (it is assumed the hardware is already plugged in). Open a terminal connected to the
      target machine

 1.2) Loading the device driver

      A) Copy the device driver and applications into a directory on the machine to be used
         (Nautilus.o, Nshell and HttpServer).

          When the device driver was already running on your system:

            a) Check whether the device driver is already running on your system.
               The command lsmod  gives an overview about the
               loaded modules on the system.

            b) If the device driver is loaded, remove the older driver using:
               rmmod Nautilus. Before removing the device driver,
               make sure, there's no network interface connected to driver, i.e. close
               an existing network interface before removing the device driver. Assuming
               eth1 is the network interface used by the device driver the
               command would be: ifconfig down eth1.

      B) To install the new Nautilus driver change to the directory the driver was copied to
         and use: insmod Nautilus.o to load the device driver module. The driver
         creates a network interface using the first unused interface number. For example: If the
         system is equiped with one other network card using device eth0, the Nautilus device driver
         will use eth1 for its interface created.

      C) For Nshell IOCTL calls of all applications a device node is required. To create it, issue:

            mknod /dev/nautilus0 c `grep nautilus /proc/devices | cut -d " " -f 1` 0
            ln -s /dev/nautilus0 /dev/nautilus

         You need to do this only once for each system in use. A shell script generating the device
         entries above can be found in the Linux/Tools directory of the source distribution.

 1.3) Connect to the network interface

      For easy switching between Nshell and System-shell it's recommended to
      open a second terminal for communication with the operating system and
      a third terminal to watch the system log where trace messages of the
      device driver are directed to.

      A continous system log (usually /var/log/messages) can be shown by watching the
      tail of this file. Issue the following command:

          tail -f /var/log/messages

      Connect the network interface with Nautilus and configure the interface IP address.
      The address 192.168.1.1 is used here as example. Use the system shell
      for giving the command:

          ifconfig eth1 192.168.1.1

      In the example above, eth1 stands for the network interface created,
      when the device driver was loaded. This is depending on your
      system. The name, especially the number, may be different.

      The correct connection of the interface can be verified by displaying the network interface
      configuration. Use the following command:

          ifconfig eth1

      This will print you an overview about all connected network interfaces e.g:

          eth1      Link encap:Ethernet  HWaddr 00:01:02:03:04:05
                    inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
                    inet6 addr: fe80::201:2ff:fe03:405/10 Scope:Link
                    UP BROADCAST MULTICAST  MTU:1500  Metric:1
                    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                    collisions:0 txqueuelen:100
                    RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



II. Platform Configuration for building Nautilus
------------------------------------------------

 2.1) Set-up the environment

      Change to the Linux build directory.

          $> cd source_linux_ST6.0/Linux

      Do start a new bash in your command window even if your default shell is already
      set to use bash.

          $> bash

      Source the respective target platform setup script. If compiling for MIPS or XScale, the
      HardHat 2.0 cross compiling tool chain is expected to be installed on the compile
      system. The compiled Kernel sources for the MIPS or XScale target need to be installed at
      the location specified in the respective *_personal.settings file (complete MIPS
      or XScale file system). Settings for this location and for instance for the install target
      directory can be changed in *_personal.settings files.

          $> source ./x86_setup.script

      or

          $> source ./mips_setup.script

      or

          $> source ./xscale_setup.script


 2.2) Configure Nautilus

      Configuration for Nautilus is done using special {\tt make} targets. The setup is done in three steps:

          - Setting up the target platform
          - Setting up the target hardware interfaces
          - Select debug or release version

      The following make targets are available:

          $> make help
          .. help .................. print this screen
          .. compile ............... build this directories target
          .. depend ................ rebuild dependencies
          .. qac ................... collect code metrics and prepare summaries            \
                                     (runs on Solaris only)
          .. set_platf_x86 ......... set target platform to x86 (preceeded by clean and HW \
                                     interface de-selection)
          .. set_platf_au1 ......... set target platform to MIPS Au1xxx (preceeded by      \
                                     clean and HW interface de-selection)
          .. set_platf_xsc ......... set target platform to Xscale (preceeded by clean     \
                           and HW interface de-selection)
          .. set_soc_acc_px2_idp ... set target platform to Xscale Accelent (preceeded by  \
                                     clean and HW interface de-selection)
          .. set_soc_cog_csb226 .... set target platform to Xscale Accelent (preceeded by  \
                                     clean and HW interface de-selection)
          .. set_pci_on ............ enable PCI hardware interface (preceeded by clean)
          .. set_pci_off ........... disable PCI hardware interface (preceeded by clean)
          .. set_sdio_on ........... enable SDIO hardware interface (preceeded by clean)
          .. set_sdio_off .......... disable SDIO hardware interface (preceeded by clean)
          .. set_cf_on ............. enable CF hardware interface (preceeded by clean)
          .. set_cf_off ............ disable CF hardware interface (preceeded by clean)
          .. set_sram_on ........... enable SRAM hardware interface (preceeded by clean)
          .. set_sram_off .......... disable SRAM hardware interface (preceeded by clean)
          .. all ................... build this module and all sub modules
          .. clean ................. clean this module and all sub modules regarding all   \
                                     aspects
          .. set_debug ............. turn on debug mode for compilation                    \
                                     (preceeded by clean)
          .. set_release ........... turn off debug mode for compilation                   \
                                     (preceeded by clean)
          .. debug ................. turn on debug mode; rebuild this module and all sub   \
                                     modules
          .. release ............... turn off debug mode; rebuild this module and all sub  \
                                     modules

      For building on x86 systems use the following configuration:

          $> make set_platf_x86 set_pci_on set_release

      or

          $> make set_platf_x86 set_pci_on set_debug

      For MIPS Pb1500 use:

          $> make set_platf_au1 set_pci_on set_release

      or

          $> make set_platf_au1 set_pci_on set_debug


 2.3) Compile the driver and applications}

      Compile the Nautilus AMD WLAN driver and applications:

          $> make

      Install the driver and applications:

          $> make install

      Driver and applications will be copied to the target directories specified
      in the *_personal.settings file.

-----------------------------------------------------------------------

---

