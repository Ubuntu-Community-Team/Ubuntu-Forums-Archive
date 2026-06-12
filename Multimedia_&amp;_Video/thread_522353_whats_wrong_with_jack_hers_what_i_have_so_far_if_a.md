---
title: "whats wrong with jack hers what i have so far if anyone can help"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by JParkus on 2007-08-10
This is only part of what i have tried looking through the forums

This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *error* Access of CD device /dev/cdrom resulted in error: Input/output error


parkus@ubuntu:~$ qjackctlX Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: no locale found: /usr/share/locale/qjackctl_en_US.UTF-8.qm
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty

here is the /ect/qt3/qt_plugins_3.3rc
[usr]
lib/kde3/plugins/styles/plastik.so=30306^e3^ei686 Linux g++-4.* full-config^e2006-09-29T20:06:31^e
lib/qt3/plugins/imageformats/libqmng.so=30307^e3^ei686 Linux g++-4.* full-config^e2007-04-10T23:58:43^e
lib/qt3/plugins/inputmethods/libqimsw-multi.so=30307^e3^ei686 Linux g++-4.* full-config^e2007-04-10T23:58:43^e
lib/qt3/plugins/inputmethods/libqimsw-none.so=30307^e3^ei686 Linux g++-4.* full-config^e2007-04-10T23:58:43^e
lib/qt3/plugins/inputmethods/libqsimple.so=30307^e3^ei686 Linux g++-4.* full-config^e2007-04-10T23:58:43^e
lib/qt3/plugins/inputmethods/libqxim.so=30307^e3^ei686 Linux g++-4.* full-config^e2007-04-10T23:58:43^e


JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

parkus@ubuntu:~$ This is free software, and you are welcome to redistribute it
bash: This: command not found
parkus@ubuntu:~$ under certain conditions; see the file COPYING for details
bash: under: command not found
Warning: unknown mime-type for "the" -- using "application/*"
Warning: unknown mime-type for "file" -- using "application/*"
Warning: unknown mime-type for "COPYING" -- using "application/*"
Warning: unknown mime-type for "for" -- using "application/*"
Warning: unknown mime-type for "details" -- using "application/*"
Error: no such file "the"
Error: no such file "file"
Error: no such file "COPYING"
Error: no such file "for"
Error: no such file "details"
parkus@ubuntu:~$ 
parkus@ubuntu:~$ JACK compiled with System V SHM support.
bash: JACK: command not found
parkus@ubuntu:~$ loading driver ..
bash: loading: command not found
parkus@ubuntu:~$ creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
bash: 1024: command not found
bash: nomon: command not found
bash: swmeter: command not found
bash: 2: command not found
bash: 48000: command not found
bash: hw:0: command not found
bash: 0: command not found
bash: 0: command not found
bash: 32bit: command not found
bash: creating: command not found
bash: -: command not found
parkus@ubuntu:~$ control device hw:0
bash: control: command not found
parkus@ubuntu:~$ the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
The program 'the' is currently not installed.  You can install it by typing:
sudo apt-get install the
Make sure you have the 'universe' component enabled
bash: the: command not found
parkus@ubuntu:~$ cannot load driver module alsa
bash: cannot: command not found
parkus@ubuntu:~$ no message buffer overruns
bash: no: command not found
parkus@ubuntu:~$ sudo apt-get install the
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  regina3
Suggested packages:
  the-doc
The following NEW packages will be installed:
  regina3 the
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 510kB of archives.
After unpacking 1364kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe regina3 3.3-4 [226kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe the 3.1-4 [284kB]
Fetched 510kB in 1s (309kB/s)  
Selecting previously deselected package regina3.

---

### Post by fredj on 2007-08-11
Reading through it's all very confusing. From the System menu select Administration->Synaptic
Package Manager. Search for and uninstall jack and qjackctl.
Then reboot and go into Synaptic package manager again. Search for jack and qjackctl and install
them again. Start qjackctl from the Applications menu, go into setup and setup jack.
Open the status window and watch for xruns.
Any problems or questions post again.

---

### Post by JParkus on 2007-08-11
I know its alot to look at after a reinstall and a reboot its works thank you

---

