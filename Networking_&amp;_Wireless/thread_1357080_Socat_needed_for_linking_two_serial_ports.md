---
title: "Socat needed for linking two serial ports"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by ps2chiper on 2009-12-16
I need to link two serial ports together with a pseudo terminal output so i can record the communication between the devices. Can someone help me with writing the socat command for that? I only found the commands to link a serial port to ip address so far.

---

### Post by ps2chiper on 2009-12-19
How does this command look?
socat -x /dev/ttyS0 PTY,link=/dev/chooseyourname

---

