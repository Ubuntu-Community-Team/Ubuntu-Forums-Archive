---
title: "Adobe Reader Read Out Loud doesn't work"
date: 2014-10-02
forum: Multimedia Software
---

### Post by Daniyal_Javani on 2014-10-02
Hello
Could you please help me to solve this problem?
I'm newbe!
Is there any alternative software for view pdf with TTS feature?

[PHP]vahid@vahid-VirtualBox:~$ sudo apt-get install libgnome-speech7
[sudo] password for vahid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-speech7 is already the newest version.
The following packages were automatically installed and are no longer required:
  libbonobo2-0:i386 libidl0:i386 liborbit-2-0:i386 liborbit2:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 143 not upgraded.
vahid@vahid-VirtualBox:~$ sudo /var/lib/dpkg/info/acroread.postinst configure 
sudo: /var/lib/dpkg/info/acroread.postinst: command not found
vahid@vahid-VirtualBox:~$ sudo apt-get install libgnome-speech7:i386 libespeak1:i386 libportaudio2:i386 libasound2-plugins:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins:i386 is already the newest version.
libespeak1:i386 is already the newest version.
libportaudio2:i386 is already the newest version.
The following packages were automatically installed and are no longer required:
  libbonobo2-0 libidl0 liborbit-2-0 liborbit2
Use 'apt-get autoremove' to remove them.
Suggested packages:
  festival:i386
The following packages will be REMOVED:
  libgnome-speech7
The following NEW packages will be installed:
  libgnome-speech7:i386
0 upgraded, 1 newly installed, 1 to remove and 143 not upgraded.
Need to get 0 B/42.6 kB of archives.
After this operation, 16.4 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 165943 files and directories currently installed.)
Removing libgnome-speech7 (1:0.4.25-5ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package libgnome-speech7.
(Reading database ... 165925 files and directories currently installed.)
Preparing to unpack .../libgnome-speech7_1%3a0.4.25-5ubuntu2_i386.deb ...
Unpacking libgnome-speech7 (1:0.4.25-5ubuntu2) ...
Setting up libgnome-speech7 (1:0.4.25-5ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
vahid@vahid-VirtualBox:~$ sudo /var/lib/dpkg/info/acroread.postinst configure sudo: /var/lib/dpkg/info/acroread.postinst: command not found


[/PHP]

---

