---
title: "Ralink 3026 driver"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by eyesvalue on 2011-02-01
Ello,
 
I am trying to install the driver for Ralink 3026 chipset.
I have followed all the instructions here [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1654876](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1654876)
 
However when I get to the make command, I get this output
 
make -C tools
make[1]: Entering directory `/home/noah/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/noah/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/noah/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/noah/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.26-2-openvz-amd64/build SUBDIRS=/home/noah/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make: *** /lib/modules/2.6.26-2-openvz-amd64/build: No such file or directory. Stop.
make: *** [LINUX] Error 2
 
 
 
Any help would be appreciated.
Utmost

---

