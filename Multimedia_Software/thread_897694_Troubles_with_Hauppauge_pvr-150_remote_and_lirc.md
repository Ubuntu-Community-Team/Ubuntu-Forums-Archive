---
title: "Troubles with Hauppauge pvr-150 remote and lirc"
date: 2008-08-22
forum: Multimedia Software
---

### Post by scottodell on 2008-08-22
I am running Ubuntu 8.04 with MythTV, and I simply can't get my pvr-150 silver remote to work. I have read many threads with similar problems, but most seem to be rooted in installation errors of ivtv or lirc.

When I run 'dmesg | grep ivtv', there are no errors reported, and the v4l-cx2341x-enc.fw firmware file is loaded.

Before I configure my lirc settings through mybuntu control center or dpkg-reconfigure lirc, the only /dev/lirc* file is /dev/lircd (a socket). However, when I configure lirc for 'Hauppauge TV Card' the character device /dev/lirc0 shows up with an X badge on it. When I configure lirc to remote control 'none' the file disappears. 

When I run irw or sudo cat /dev/lirc0, I can get no output. I'm pretty well stumped and would appreciate any help.

MythTV is working great with the keyboard controls and I'm positive my remote is sending IR signals.

---

### Post by wolfen69 on 2008-08-22
do you have the MCE edition?

---

### Post by scottodell on 2008-08-22
The box says that the remote is not compatible with Windows XP Media Center Edition.

---

