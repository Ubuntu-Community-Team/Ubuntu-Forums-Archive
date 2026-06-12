---
title: "sky2 driver issue"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by davidself1001 on 2011-05-02
I was having problems with sky2 periodically disconnecting so i loaded the sk98lin driver and it worked well until i had to do a reboot and when it came back up i was on sky2 again.  I did the install option of the driver installation and it showed sk98lin as the installed driver when i checked the config info.  Now when i try to reinstall it i get the following results and sky2 is listed as the driver.


root@david-desktop:/home/david/Desktop/DriverInstall# bash ./install.sh


Installation script for sk98lin driver.
Version 10.87.3.3 (Feb-01-2011)
(C)Copyright 2003-2010 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation	      3) generate makefile
2) generate patch     4) exit
Choose your favorite installation method: 1









Please read this carefully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel 
module. This script will do this automatically per default.
 
Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y










Create tmp dir (/tmp/Sk98IfkfKllPDBeHAbFmiHkPc)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.38-8-generic)                              [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (4)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (x86_64)                                            [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (kernel)                                         [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.5.2) (Kernel:4.5.2 == gcc:4.5.2)         [   OK   ]
Check sk98lin driver availability (loaded)                           [   OK   ]
Disconnect devices:  (done)                                          [   OK   ]
Remove driver (done)                                                 [   OK   ]
Check kernel header files (/lib/modules/2.6.38-8-generic/build)      [   OK   ]
Check sources for .config file (/lib/modules/2.6.38-8-generic/build/.[   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (lowmem)                                 [   OK   ]
Change IOMMU (enabled)                                               [   OK   ]
Create new .config file (done)                                       [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check modpost availability (available)                               [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check firmware availability (done)                                   [   OK   ]
Check kernel header version (not recognized)                         [  warn  ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (done)                                            [   OK   ]
Copy driver man page into /usr/share/man/man4/ (done)                [   OK   ]
Check the driver (done)                                              [   OK   ]
Delete old driver (done)                                             [   OK   ]
Copying driver (done)                                                [   OK   ]
Make dependency (done)                                               [   OK   ]
Delete temp directories (done)                                       [   OK   ]
All done. Driver installed and loaded.
To load the module manually, proceed as follows:
      Enter "modprobe sk98lin"

                                                     Have fun...
root@david-desktop:/home/david/Desktop/DriverInstall# modprobe sk98lin
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/kqemu, it will be ignored in a future release.


Any help would be greatly appreciated.

---

### Post by davidself1001 on 2011-05-03
So does installing a driver via the "installion" option live after a reboot or do i have to use the "patch" option for it to be permant?

---

### Post by mathia on 2011-05-08
Hi,
you must update the initramfs:
$ sudo rmmod sky2
$ sudo rmmod sk98lin
$ sudo modprobe sk98lin
$ sudo update-initramfs -u -k all
$ reboot
$ sudo lsmod | grep sk
sk98lin ...

please let me know, if it worked for you.

---

