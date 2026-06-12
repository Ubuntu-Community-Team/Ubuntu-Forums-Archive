---
title: "Bluetooth headphones problem: A2DP only working as root"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by HeadBeeGuy on 2007-04-25
Hello!

I've followed the instructions at the bluetooth-alsa project page ([http://bluetooth-alsa.sourceforge.net/]("http://bluetooth-alsa.sourceforge.net/")) to get A2DP working with my Bluetooth headphones, and it works quite well, but only under one condition: I have to run A2DPD as root. If I run it without sudo, I get the following sequence of errors:

A2DPD[01:12:22.239]: a2dp_make_listen_socket: (errno=13:Permission denied)Cannot bind socket 6 for psm 25
A2DPD[01:12:22.239]: main_loop: Cannot get AVDTP socket
...
A2DPD[01:12:23.243]: main_loop: (errno=98:Address already in use)Cannot get UNIX socket

The bluetooth-alsa page says that "it's not advised to run (a2dpd) as root", so I'd rather not, if I can get it to work any other way. I assume I just need to twiddle some permissions somewhere, but it's the "somewhere" that gets me! Any advice or recommendations would be very gratefully received.

Thanks!

---

### Post by pete on 2007-04-27
I'm getting the same behavior.

I had this working fine under Edgy (i.e., could run a2dpd non-root), but can't get it going under Feisty.

---

### Post by Meir on 2007-04-29
I am having the same problem as you guys aswell (see [http://ubuntuforums.org/showthread.php?t=426501)](http://ubuntuforums.org/showthread.php?t=426501)). Is it actually working for you as root? Is the new device listed in xmms?

---

### Post by pete on 2007-04-29
a2dpd *is* working for me when I run it as root.  Can't say as to whether it shows up as a device in xmms or not, since I use VLC for this purpose. 

However, it works like a charm in VLC, so long as I'm running at as root.  If I leave off the "sudo", I get the same "main_loop: (errno=98:Address already in use)Cannot get UNIX socket" error you're getting.  So far, no amount of Googling has turned up any useful information.

---

### Post by Coopster on 2007-04-29
I found the problem, but I don't know the solution.  a2dpd tries to create the connection on bluetooth ports 23 and 25, which are reserved for superuser.  I'll file a bug, from my research, it looks like the proper way to do what they were doing involves some SDP calls, but they use constant numbers.

---

