---
title: "Belkin N Basic USB Adapter not working in 10.04"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by slint69 on 2011-01-18
I've been reading some of the previous threads but still have not been able to make the adapter work.

Here's where I got stuck.  I was able to install ndsiwrapper and the GUI.  I found the driver (net8192su.inf) on the disk which came with the adopter and installed the driver using the GUI for ndsiwrapper.  Unfortunately I get a message "invalid driver" after I installed it? 

Anyone have any suggestions?

---

### Post by walt.smith1960 on 2011-01-18
Yup, I think I do :D. This looks like the same chipset as the TrendNet TEW-649UB.  Here is the fix that has worked on a couple different machines/distros

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

You shouldn't need Ndiswrapper or Windows drivers.  I don't know if having Ndiswrapper installed will cause a conflict with the Linux driver or not.

---

### Post by slint69 on 2011-01-18
Thank you for pointing me in the right direction. :).  I try to follow the thread but got stuck again.  It was not exactly clear to me where to start.  Admittedly I am very new to this, so perhaps this is a bit over my head. 

Here is what I got.  Note the error at the end that the directory does not exist:
___________________________________________________________________________________
stefan@stefan-desktop:~$ udo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/

The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
stefan@stefan-desktop:~$ 
stefan@stefan-desktop:~$ 
stefan@stefan-desktop:~$ sudo apt-get install udo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  udo
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 177kB of archives.
After this operation, 532kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe udo 6.4.1-1 [177kB]
Fetched 177kB in 1s (158kB/s)
Selecting previously deselected package udo.
(Reading database ... 145108 files and directories currently installed.)
Unpacking udo (from .../archives/udo_6.4.1-1_i386.deb) ...
Processing triggers for man-db ...
Setting up udo (6.4.1-1) ...
stefan@stefan-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
stefan@stefan-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
stefan@stefan-desktop:~$ wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
--2011-01-18 22:31:41--  [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
Resolving launchpadlibrarian.net... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31817 (31K) [application/octet-stream]
Saving to: `rtl8192sfw.bin.gz'

100%[======================================>] 31,817      25.0K/s   in 1.2s    

2011-01-18 22:31:43 (25.0 KB/s) - `rtl8192sfw.bin.gz' saved [31817/31817]

stefan@stefan-desktop:~$ gunzip rtl8192sfw.bin.gz
gzip: rtl8192sfw.bin already exists; do you wish to overwrite (y or n)? y
stefan@stefan-desktop:~$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
mv: cannot move `rtl8192sfw.bin' to `/lib/firmware/RTL8192SU/': Not a directory

---

### Post by walt.smith1960 on 2011-01-19
[I]stefan@stefan-desktop:~$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
mv: cannot move `rtl8192sfw.bin' to `/lib/firmware/RTL8192SU/': Not a directory[/I]

Part of the problem is that there isn't an "RTL8192SU" folder, you need to create one.  Being a GUI sorta guy I just do ```
gksu nautilus
```then navigate to lib/firmware and create the RTL8192SU folder. Move the extracted .bin file into the newly created folder, reboot and enjoy. Do use caution when using Nautilus as a sudo user -- make sure the path is correct.

---

### Post by slint69 on 2011-01-20
walt.smith1960 thank you very much for your guidance. :D   I created the folder and removed ndiswrapper, rebooted and voila, the adopter picked up the network and I am off and running into the world of Ubuntu.

---

### Post by walt.smith1960 on 2011-01-20
duplicate-please remove

---

### Post by walt.smith1960 on 2011-01-20
duplicate--please remove

---

### Post by walt.smith1960 on 2011-01-20
> **slint69 said:**
> walt.smith1960 thank you very much for your guidance. :D   I created the folder and removed ndiswrapper, rebooted and voila, the adopter picked up the network and I am off and running into the world of Ubuntu.

I'm glad it worked for you.  This seems like a pretty good chip set to use with linux.  Ath9k ones are a nice choice as well, and both will be supported at install with 11.04.  Could you mark the thread as solved?  That may help others with the same problem.

---

