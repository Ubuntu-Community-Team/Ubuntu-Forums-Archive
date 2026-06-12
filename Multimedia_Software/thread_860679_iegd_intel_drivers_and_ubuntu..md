---
title: "iegd intel drivers and ubuntu."
date: 2008-07-15
forum: Multimedia Software
---

### Post by the_jlx on 2008-07-15
So would anyone care to translate this into ubuntu terms?
since theese directories dosent exsist nor do i find aything that would be even remotley right.
and being whit out open gl and 3D sucks big time.
i appreciate any help i can get. before i am going back to that crappy windows. (arrggh)

                    Xorg -version
                4. Copy the IEGD driver binary, intel_drv.o, from the IEGD_5_1_Linux/Driver/
                    <xserver name> directory to the X-Server’s modules/drivers directory. The
                    default installation directory is /usr/X11R6/lib/modules/drivers. This location
                    can vary by distribution so check your system for the proper path. For example, if
                    you are installing to an XFree86 version 4.3 X-Server, type the following
                    commands:
                    cd .../IEGD_5_1_Linux/Driver/XFree86-4.3/
                    cp intel_drv.o /usr/X11R6/lib/modules/drivers
                5. Copy the necessary port driver files (*.so files in the .../IEGD_5_1_Linux/
                    Driver/<xserver name> directory) to the X-Server lib/modules directory. The
                    default installation location is /usr/X11R6/lib/modules. This location can vary, so
                    check your system for the proper path. Once the required port drivers have been
                    copied, you can specify them in the PortDrivers option in the Device section of
                    the config file. For more information on specifying the PortDrivers option, refer to
                    Table 21, “Supported Driver Options” on page 136. For example, to copy all the
                    port drivers, type the following command:
                    cp *.so /usr/X11R6/lib/modules
                6. Copy the port control client libraries (libXportctl.a and libXportctl.so.1.0)
                    and the driver control client libraries (libXiegdctl.a and libXiegdctl.so.1.0)
                    and the escape control libraries (libXiegd_escape.a and libXiegd_escape.so.1.0)
                    from the IEGD_5_1_Linux/Driver/<xserver name> directory to the X-Server
                    library directory. The default installation location is /usr/X11R6/lib . For example,
                    cp libXportctl.a libXportctl.so.1.0 libXiegdctl.a libXiegdctl.so.1.0
                    libXiegd_escape.a libXiegd_escape.so.1.0 /usr/X11R6/lib
                7. In the X-Server library directory, create symbolic links for the port control and
                    driver control library aliases:
                    cd /usr/X11R6/lib
                    ln -s libXportctl.so.1.0 libXportctl.so
                    ln -s libXportctl.so.1.0 libXportctl.so.1
                    ln -s libXiegdctl.so.1.0 libXiegdctl.so
                    ln -s libXiegdctl.so.1.0 libXiegdctl.so.1
                    ln -s libXiegd_escape.so.1.0 libXiegd_escape.so
                    ln -s libXiegd_escape.so.1.0 libXiegd_escape.so.1
                8. Copy the port control and driver control include files (portctl.h and iegdctl.h) to
                    the XFree86 include/extensions directory. The default installation location is /
                    usr/X11R6/include/X11.
                    cd .../IEGD_5_1_Linux/Driver/XFree86-4.3
                    cp portctl.h iegdctl.h /usr/X11R6/include/X11
                9. Copy the port control and driver control man pages (IntelPortCtl.3x and
                    IntelDriverCtl.3x) from the IEGD_5_1_Linux/Documents/<xserver name> to
                    the X-Server man/man3 directory. The default installation location is /usr/X11R6/
                    man/man3. For example,
                    cd .../IEGD_5_1_Linux/Documents/XFree86
                    cp IntelPortCtl.3x IntelDriverCtl.3x /usr/X11R6/man/man3
               10. Create the following hard links in the X-Server man/man3 directory:
                    cd /usr/X11R6/man/man3
                    ln IntelPortCtl.3x IntelPortCtlQueryExtension.3x
                    ln IntelPortCtl.3x IntelPortCtlQueryVersion.3x
                                                               Intel® Embedded Graphics Drivers and Video BIOS v5.1
June 2006                                                                                               User’s Guide
Document Number: 274041-009US                                                                                   127
                                                                          Linux* Installation and Configuration
                     ln  IntelPortCtl.3x IntelPortCtlPortControl.3x
                     ln  IntelPortCtl.3x IntelPortCtlGetPortAttributes.3x
                     ln  IntelPortCtl.3x IntelPortCtlSetPortAttibutes.3x
                     ln  IntelPortCtl.3x IntelPortCtlReadPortAttibutes.3x
                     ln  IntelPortCtl.3x IntelPortCtlWritePortAttibutes.3x
                     ln  IntelPortCtl.3x IntelPortCtlQueryPort.3x
                     ln  IntelPortCtl.3x IntelPortCtlQueryPorts.3x
                     ln  IntelPortCtl.3x IntelPortCtlGetPortMode.3x
                     ln  IntelPortCtl.3x IntelPortCtlGetPortModes.3x
                     ln  IntelPortCtl.3x IntelPortCtlSetPortMode.3x
                     ln  IntelPortCtl.3x IntelPortCtlSetPortModes.3x
                     ln  IntelPortCtl.3x IntelPortCtlAllocPort.3x
                     ln  IntelDriverCtl.3x IntelDriverCtlQueryExtension.3x
                     ln  IntelDriverCtl.3x IntelDriverCtlQueryVersion.3x
                     ln  IntelDriverCtl.3x IntelDriverCtlPortControl.3x
                     ln  IntelDriverCtl.3x IntelDriverCtlGetDriverInfo.3x
                 11. From the IEGD_5_1_Linux/Documents directory, copy the driver man page,
                     intel.4, to the man/man4 directory. The default installation location is /usr/
                     X11R6/man/man4. This location can vary by distribution so check your system for
                     the proper path. For example:
                     cd .../IEGD_5_1_Linux/Documents/XFree86
                     cp intel.4 /usr/X11R6/man/man4
                 12. Patch the agpgart module with the Intel extensions:
                     To patch the Linux 2.4.2x and SuSE kernel with the GART changes:
                     1. cd into the kernel source directory (e.g., cd /usr/src/linux-2.x.xxx)
                     2. Execute the patch command. For example:
                     patch -p1 < .../IEGD_Patches/Driver/agpgart.patch-2.x.xxx
                     To update the kernel:
                     1. cd to the kernel source directory (e.g., cd /usr/src/linux-2.x.xxx)
                     2. Execute the make modules command.
                        make modules
                     3. Install the modules.
                        make modules_install'
                     To patch a Linux 2.6.xxxx kernel with the GART changes for Fedora Core 2 kernels:
                     1. cd into the kernel source directory (e.g. cd /usr/src/linux-2.6.5-1.358)
                     2. Execute the patch command as follows:
                         patch -p1 < .../IEGD_Patches/Driver/agpgart.patch-2.6.xxxx
                     To update the kernel:
                     1. cd to the kernel source directory (e.g. cd /usr/src/linux-2.6.5-1.358)
                     2. Since the agpgart is built-in by default in Fedora Core 2, it needs to be
                     configured to install it as a module before updating the kernel.
                     make menuconfig
Intel® Embedded Graphics Drivers and Video BIOS v5.1
User’s Guide                                                                                          June 2006
128                                                                            Document Number: 274041-009US
Linux* Installation and Configuration
                     From the configuration menu, select Device Drivers, then Character Devices.
                     Scroll down to /dev/agpart. Change the disposition to M (for Module). Exit from
                     the configuration menu and save your changes.
                     3. Execute the make modules command:
                        make modules
                     4. Install the modules:
                        make modules_install
                     5. Build the kernel
                        make install
                     6. Run the following commands for the linux-2.6.xxxx kernel:
                        modprobe agpgart
                        modprobe intel-agp
                     Also, to ensure the modules are loaded after a reboot, add the following line to the
                     /etc/modprobe.conf file:
                     alias char-major-10-175 intel-agp
                 13. Modify your XF86Conf or Xorg.conf file to include a device section for this driver
                     and a Monitor section for your display. See Section 8.4 for details on the driver
                     configuration and the list of supported options. The default installation location for
                     this file is
                     /etc/X11
                 14. Set the LD_LIBRARY_PATH environment variable as follows:
                     export LD_LIBRARY_PATH=/usr/X11R6/lib:/usr/lib/qt-3.1/lib (for Redhat
                     9)
                     export LD_LIBRARY_PATH=/usr/X11R6/lib:/usr/lib/qt-3.3/lib (for Fedora
                     Core 2)
                     The /usrlib/qt-3.1/lib path is required for running the Runtime Configuration
                     GUI (see Section 8.5.1, “Runtime Configuration GUI (IEGDGUI)” on page 144).
8.4              Configuration
                 The Intel Linux driver is for use with the integrated graphics of Intel chipsets on the
                 Embedded Intel Architecture roadmap. The driver supports 8-, 16- and 24-bit pixel
                 depths, dual independent head setup (only with the Intel® 852GME, Intel® 852GM,
                 Intel® 855GME, Intel® 915GM, Intel® 915GM, Intel® 945G, and Intel® 945GM
                 chipsets), flat panel, hardware 2D acceleration, hardware cursor, the XV extension, and
                 the Xinerama extension.

---

### Post by bornagainpenguin on 2009-05-23
/bump

---

### Post by Dlambert on 2010-07-09
Its only supported in fedora, red hat, but not ubuntu

---

### Post by Godwyn on 2010-07-17
> **Dlambert said:**
> Its only supported in fedora, red hat, but not ubuntu
acording to the faq:
**[ Are there any plans to provide a new  IEGD Linux installer that supports all POR Linux distributions?]("javascript:ToggleShowHideContent('faqs-linux-q5-content',%20'faqs-linux-q5-toggle');")**

 				 					No, IEGD v10.3 has an installer/uninstaller for Fedora 7. Please  refer to IEGD User’s Guide for installation instructions on other  supported Linux distributions.


and acording to the userguide:



7.3.6.2 Installing the IEGD Driver for Ubuntu
Platform: Intel® Atom™
System Memory: 1Gbyte DDR2 533 MHz
Video Memory: 8 Mbytes Stolen Memory, 256 Mbytes Aperture Memory (Support from
ECG BIOS version 0.17 and above)
Display Interface: CRT (1400x1050)
OS: Ubuntu 8.04.1 Hardy
X-Window: Xorg-server 1.4.1
Kernel: 2.6.24.3
Software Required:
• Driver: the latest IEGD driver
• Helix: splay-plugin-atlas-01.2.0
(Download from [https://helix-client.helixcommunity.org/Releases](https://helix-client.helixcommunity.org/Releases))
• UMG Codecs: 1.8.8.22 (contact your Intel representative for the file)
• WMV Codecs: Helix Windows Media Integration Project ([https://helixclient](https://helixclient).
helixcommunity.org/2005/devdocs/windowsMedia.html - Download source
code and compile binary for asfff.so, avc1.so, dmp4.so, wma9.so,
wmarender.so, wmerender.so)

---

### Post by Godwyn on 2010-07-17
in adition here are the installation notes for ubuntu.

Installation Steps
1. Make sure the software listed above is on your hard drive before proceeding to the
next step.
2. Boot up the target Intel® Atom™ system.
You will see the fastar login prompt. Just log in as root and no password is required.
3. Refer to “Editing the Linux* OS Configuration File Directly” on page 180 to edit
/etc/X11/xorg.conf file to work with IEGD.
4. Start the X server:
startx
5. Copy driver binary, where <driver> is the IEGD_10_3_1_Linux/driver directory:
cd <driver>/Xorg-xserver-1.4
cp iegd_drv.so /usr/lib/xorg/modules/drivers
cd /usr/lib
ln –sfv libexpat.so.1.5.2 libexpat.so
ln –sfv libexpat.so.1.5.2 libexpat.so.1
cd <driver>/Xorg-xserver-1.4
cp *.so /usr/lib/xorg/modules
cp libXiegd_escape.so.2.0.0 /usr/lib
cp libGL* /usr/lib
6. Enable DRI:
mkdir /usr/lib/dri
cp iegd_dri.so /usr/lib/dri
7. Link the library:
cd /usr/lib
ln -s libXiegd_escape.so.2.0.0 libXiegd_escape.so
ln -s libXiegd_escape.so.2.0.0 libXiegd_escape.so.2
ln -sfv libGL_ga.so.1.2 libGL.so
ln -sfv libGL_ga.so.1.2 libGL.so.1
ln –sfv libexpat.so.1.5.2 libexpat.so.0
8. Perform patching:
cd <driver>/IKM
./install.sh
Note: If a permissions error is displayed, do a chmod +x install.sh or try using the command
sudo bash ./install/sh
depmod –a
modprobe iegd_mod
startx
The driver and 3D should be up and running now.
9. Make sure the installation is pointing to Tungsten and not MESA:
glxinfo | grep "vendor"
Failure on this will cause 3D and VA to fail.

---

