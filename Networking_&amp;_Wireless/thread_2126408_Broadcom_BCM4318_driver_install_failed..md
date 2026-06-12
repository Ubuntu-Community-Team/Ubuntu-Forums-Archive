---
title: "Broadcom BCM4318 driver install failed."
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by ericyyao on 2013-03-17
I have a generic desktop which runs 12.04. It has a wireless card that used to work on 10.10. I tried to use "system settings" -> "additional driver" to install the driver after a fresh 12.04 install. It failed (kernel trap, unfortunately didn't record the trace). Rebooted and tried to follow the suggestions from other thread to reinstall from command line. The reinstall process hangs. Install and gdb trace below. Thanks in advance for help.

```
eric@lonepeak:~$ sudo apt-get install --reinstall bcmwl-kernel-source
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
eric@lonepeak:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...


-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-38-generic-pae (i686)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-38-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.


------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-38-generic-pae
Building for architecture i686
Building initial module for 3.2.0-38-generic-pae
Done.


wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-38-generic-pae/updates/dkms/


depmod....


DKMS: install completed.

***** reinstall process hangs here ***********

****** In another terminal ************


eric@lonepeak:~$ ps -ef | grep -i dpkg
root      2699  1630  0 22:14 pts/1    00:00:00 sudo dpkg --configure -a
root      2700  2699  0 22:14 pts/1    00:00:00 dpkg --configure -a
root      2701  2700  0 22:14 pts/1    00:00:00 /bin/sh /var/lib/dpkg/info/bcmwl-kernel-source.postinst configure 6.20.155.1+bdcom-0ubuntu0.0.1
eric      3837  3587  0 22:21 pts/2    00:00:00 grep --color=auto -i dpkg
eric@lonepeak:~$ sudo gdb --pid 2700
[sudo] password for eric: 
Sorry, try again.
[sudo] password for eric: 
GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2.1) 7.4-2012.04
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>.
Attaching to process 2700
Reading symbols from /usr/bin/dpkg...(no debugging symbols found)...done.
Reading symbols from /lib/i386-linux-gnu/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libselinux.so.1
Reading symbols from /lib/i386-linux-gnu/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libc.so.6
Reading symbols from /lib/i386-linux-gnu/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libdl.so.2
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
0x00efd416 in __kernel_vsyscall ()
(gdb) bt
#0  0x00efd416 in __kernel_vsyscall ()
#1  0x001c7943 in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0x08069ece in ?? ()
#3  0x08069f43 in ?? ()
#4  0x08056040 in ?? ()
#5  0x080562a7 in ?? ()
#6  0x0805682d in ?? ()
#7  0x0804f580 in ?? ()
#8  0x080592b5 in ?? ()
#9  0x0805951b in ?? ()
#10 0x0804a3f3 in ?? ()
#11 0x001294d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
#12 0x0804a4c5 in ?? ()
(gdb) q
A debugging session is active.


    Inferior 1 [process 2700] will be detached.


Quit anyway? (y or n) y
Detaching from program: /usr/bin/dpkg, process 2700
eric@lonepeak:~$ sudo gdb --pid 2699
GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2.1) 7.4-2012.04
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>.
Attaching to process 2699
Reading symbols from /usr/bin/sudo...(no debugging symbols found)...done.
Reading symbols from /lib/i386-linux-gnu/libutil.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libutil.so.1
Reading symbols from /lib/i386-linux-gnu/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libdl.so.2
Reading symbols from /lib/i386-linux-gnu/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libc.so.6
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /lib/i386-linux-gnu/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_compat.so.2
Reading symbols from /lib/i386-linux-gnu/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnsl.so.1
Reading symbols from /lib/i386-linux-gnu/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_nis.so.2
Reading symbols from /lib/i386-linux-gnu/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_files.so.2
Reading symbols from /usr/lib/sudo/sudoers.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/sudo/sudoers.so
Reading symbols from /lib/i386-linux-gnu/libpam.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libpam.so.0
Reading symbols from /lib/i386-linux-gnu/security/pam_env.so...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/security/pam_env.so
Reading symbols from /lib/i386-linux-gnu/security/pam_unix.so...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/security/pam_unix.so
Reading symbols from /lib/i386-linux-gnu/libcrypt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libcrypt.so.1
Reading symbols from /lib/i386-linux-gnu/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libselinux.so.1
Reading symbols from /lib/i386-linux-gnu/security/pam_deny.so...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/security/pam_deny.so
Reading symbols from /lib/i386-linux-gnu/security/pam_permit.so...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/security/pam_permit.so
Reading symbols from /lib/i386-linux-gnu/security/pam_cap.so...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/security/pam_cap.so
Reading symbols from /lib/i386-linux-gnu/libcap.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libcap.so.2
Reading symbols from /lib/i386-linux-gnu/security/pam_umask.so...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/security/pam_umask.so
Reading symbols from /lib/security/pam_gnome_keyring.so...(no debugging symbols found)...done.
Loaded symbols for /lib/security/pam_gnome_keyring.so
Reading symbols from /lib/security/pam_ck_connector.so...(no debugging symbols found)...done.
Loaded symbols for /lib/security/pam_ck_connector.so
Reading symbols from /lib/i386-linux-gnu/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libdbus-1.so.3
Reading symbols from /usr/lib/libck-connector.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libck-connector.so.0
Reading symbols from /lib/i386-linux-gnu/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1".
Loaded symbols for /lib/i386-linux-gnu/libpthread.so.0
Reading symbols from /lib/i386-linux-gnu/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/librt.so.1
0x006e4416 in __kernel_vsyscall ()
(gdb) bt
#0  0x006e4416 in __kernel_vsyscall ()
#1  0x00317d2d in select () from /lib/i386-linux-gnu/libc.so.6
#2  0x0804bc13 in ?? ()
#3  0x08050a78 in ?? ()
#4  0x0804adca in ?? ()
#5  0x002494d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
#6  0x0804b111 in ?? ()
(gdb) q
A debugging session is active.


    Inferior 1 [process 2699] will be detached.


Quit anyway? (y or n) y
Detaching from program: /usr/bin/sudo, process 2699
eric@lonepeak:~$ ps -ef | grep -i dpkg
root      2699  1630  0 22:14 pts/1    00:00:00 sudo dpkg --configure -a
root      2700  2699  0 22:14 pts/1    00:00:00 dpkg --configure -a
root      2701  2700  0 22:14 pts/1    00:00:00 /bin/sh /var/lib/dpkg/info/bcmwl-kernel-source.postinst configure 6.20.155.1+bdcom-0ubuntu0.0.1
eric      3850  3587  0 22:23 pts/2    00:00:00 grep --color=auto -i dpkg
eric@lonepeak:~$ sudo gdb --pid 2701
GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2.1) 7.4-2012.04
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>.
Attaching to process 2701
Reading symbols from /bin/dash...(no debugging symbols found)...done.
Reading symbols from /lib/i386-linux-gnu/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libc.so.6
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
0x00f95416 in __kernel_vsyscall ()
(gdb) bt
#0  0x00f95416 in __kernel_vsyscall ()
#1  0x00b849ee in wait4 () from /lib/i386-linux-gnu/libc.so.6
#2  0x00b849c7 in wait3 () from /lib/i386-linux-gnu/libc.so.6
#3  0x080506c5 in ?? ()
#4  0x080516ec in ?? ()
#5  0x0804c19e in ?? ()
#6  0x0804b209 in ?? ()
#7  0x0804b29e in ?? ()
#8  0x0804b209 in ?? ()
#9  0x0804b29e in ?? ()
#10 0x0804b50b in ?? ()
#11 0x0804b209 in ?? ()
#12 0x08051ba4 in ?? ()
#13 0x08049801 in ?? ()
#14 0x00ae64d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
#15 0x08049919 in ?? ()
(gdb) q
A debugging session is active.


    Inferior 1 [process 2701] will be detached.


Quit anyway? (y or n) y
Detaching from program: /bin/dash, process 2701
eric@lonepeak:~$ dmesg | grep -i fail
[   20.131819] wl driver 6.20.155.1 (r326264) failed with code 21
[   20.717103] init: failsafe main process (643) killed by TERM signal
eric@lonepeak:~$ sudo lspci -nn | grep 0280
03:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
eric@lonepeak:~$ uname -a
Linux lonepeak 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 i686 i386 GNU/Linux
```
eric@lonepeak:~$

---

### Post by wildmanne39 on 2013-03-17
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by ericyyao on 2013-03-17
netinfo.txt attached.

---

### Post by Hadaka on 2013-03-17
Hi, try this..

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43

```
thanks.

---

### Post by wildmanne39 on 2013-03-17
I see Hadaka beat me to it.:P

---

### Post by ericyyao on 2013-03-17
Thanks a lot for help. I somehow didn't work for me.

"sudo modprobe b43" hangs
gdb the pid appears to be hang too (can't get to gdb prompt).

What else should I try?

---

### Post by ericyyao on 2013-03-17
Even though the installation appeared to be hung, it seemed to have done the job. I rebooted the PC and the wireless card is working just fine. Thank you so much for help.

Could you explain what the difference is between the [COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source and [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]b43-fwcutter firmware-b43-installer? I really appreciate it![/FONT][/COLOR]

---

### Post by Hadaka on 2013-03-17
Hi, glad that worked for you. The difference between
the bcmwl and the b43 diver is the driver codeing that
controls the wifi card and is dependant on the type of
chip and other circuits on the card. Your card Broadcom 4318
[14e4:4318] requires the b43 driver. Please use thread tools to mark this
thread solved.
thanks.

---

### Post by ericyyao on 2013-03-17
Thanks again! Could you let me know how to mark it "resolved"? Under my thread tools, I have 3 options: show printable version, email this page, subscribe to this thread.

---

### Post by Hadaka on 2013-03-17
Hi, i think i heard it was not working correctly
so temp method is to sign back in..your thread
then edit the title and insert [SOLVED]
thanks.

---

### Post by wildmanne39 on 2013-03-17
Hi, I marked it solved for you.

---

