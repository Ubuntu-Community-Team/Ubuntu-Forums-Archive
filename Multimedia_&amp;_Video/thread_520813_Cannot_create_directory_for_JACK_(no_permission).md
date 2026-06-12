---
title: "Cannot create directory for JACK (no permission)"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by paletti on 2007-08-08
I got a problem when trying to start the JACK server. Any ideas? Cheers! 

Here's the output:

08:19:24.424 Startup script...
08:19:24.427 artsshell -q terminate
can't create mcop directory
Creating link /home/paletti/.kde/socket-paletti-laptop.
08:19:24.736 Startup script terminated with exit status=256.
08:19:24.738 JACK is starting...
08:19:24.740 jackd -dalsa -dhw:0 -r44100 -p1024 -n2
08:19:24.748 JACK was started with PID=8580 (0x2184).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot create /dev/shm/jack-1000 directory (Permission denied)
cannot create server sockets
cannot create engine
08:19:24.811 JACK was stopped successfully.
08:19:24.813 Post-shutdown script...
08:19:24.815 killall jackd
jackd: no process killed
08:19:25.044 Post-shutdown script terminated with exit status=256.
08:19:26.846 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by benerivo on 2007-08-08
Could you create the directory yourself by typing ```
sudo nautilus
``` then making the required folder, then running JACK again. This may only be a partial fix as it sounds as though it may attempt to do other things that require root permission. A way round that may be to run the program itself as root.

---

### Post by paletti on 2007-08-09
Thanks for your reply Benerivo! I added the folder manually but like you said it didn't work... everytime it displays the same error (no permission) when I ty to start jackserver.
I tried the following (although I'm not really a whiz with the terminal):

paletti@paletti-laptop:~$ sudo -i
root@paletti-laptop:~# /usr/bin/qjackctl
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: no locale found: /usr/share/locale/qjackctl_en_NZ.UTF-8.qm

Did I do something wrong? Maybe it has something to do with an error in /etc/udev/rules.d/42-madfuload.rules ... But I don't know, the thing is that my M-Audio Ozone is recognised in ubuntu and displayed in the device manager. Hmm...

---

### Post by paletti on 2007-08-11
Anybody?

---

