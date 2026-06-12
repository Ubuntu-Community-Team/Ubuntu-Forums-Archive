---
title: "Mythtv protocol mismatch"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by stinkypudding on 2007-06-18
I've had mythtv up and running for several months, using the following installation guide for feisty:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Yesterday it stopped working, and I'm not sure what if anything I did wrong.   The error I'm getting is a protocol mismatch between the frontend and backend servers.

Can anyone help me fix this?

Here is my terminal output:

ryanr@ubuntu:~$ mythtv
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-06-18 21:45:56.919 Using runtime prefix = /usr/local
2007-06-18 21:45:56.924 DPMS is active.
2007-06-18 21:45:56.937 New DB connection, total: 1
2007-06-18 21:45:56.941 Connected to database 'mythconverg' at host: localhost
2007-06-18 21:45:56.942 Total desktop dim: 1280x720, with 1 screen[s].
2007-06-18 21:45:56.955 Using screen 0, 1280x720 at 0,0
2007-06-18 21:45:56.970 max_width: 1280 max_height: 720
2007-06-18 21:45:56.971 Total desktop dim: 1280x720, with 1 screen[s].
2007-06-18 21:45:56.972 Using screen 0, 1280x720 at 0,0
2007-06-18 21:45:56.975 Switching to square mode (G.A.N.T.)
2007-06-18 21:45:56.996 Using the Qt painter
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-06-18 21:45:57.477 Joystick disabled.
2007-06-18 21:45:57.540 New DB connection, total: 2
2007-06-18 21:45:57.548 Connected to database 'mythconverg' at host: localhost
2007-06-18 21:45:57.814 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-06-18 21:45:57.834 Protocol version mismatch (frontend=30,backend=31)

---

### Post by stinkypudding on 2007-06-22
Is there a way to remove my mythtv binaries, and start all over again?  Everytime I try to remove and purge my mythtv configuration, my binaries remain, which I think is causing the protocol mismatch?   Can someone please help?

---

### Post by stinkypudding on 2007-07-04
I think I may have found the problem.   I have mythtv set up in both /usr/bin, and /usr/local/bin.    Could this be the reason for the protocol mismatch?   If so, how can I fix which one is started when I startup mythtv?

---

### Post by superm1 on 2007-07-04
This would definitely be the reason for a protocol mismatch.  Take out anything in /usr/local/bin/ and /usr/local/lib with myth in the name.

---

### Post by stinkypudding on 2007-07-04
That worked!   Fabulous, thank you.

---

