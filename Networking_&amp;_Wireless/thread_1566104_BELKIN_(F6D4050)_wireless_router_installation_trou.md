---
title: "BELKIN (F6D4050) wireless router installation troubles (KarmicKoala 9.10)"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by fhgshfdg on 2010-09-01
Hello everyone! Thanks for taking the time to read my thread and help me solve a problem I've been having ever since I first installed Ubuntu. I'm running KarmicKoala 9.10 partitioned with Windows XP on my Dell Dimension 8300.

I'm having an impossible time installing the drivers to (or maybe just getting the computer to recognize the hardware) my Belkin F6D4050v2. I have the driver installation disc that came with the product and have been attempting to install rt2870.inf using ndisgtk. The problem is, once I "Install New Driver" and select the rt2870.inf file I'm prompted with a "Unable to see if hardware is present" message. After clicking OK, it reads:
[B]
rt2870[/B]
Hardware present: Yes

Yet it is still not recognizing its presence or just not picking up a signal. I know the router works correctly using these drivers on Windows XP because I use it frequently.

Using the lsusb command I get an output of:
Bus 001 Device 003: ID 050d:935b Belkin Components
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc.
etc.

What should I do to get this thing up and running?!!

---

### Post by dineshs on 2010-09-02
Have you seen this?
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by fhgshfdg on 2010-09-24
So I got the wireless adapter to work. However, I'm not having trouble with Firefox! The network manager confirms the ra0 wireless connection is enabled and the Ubuntu/Firefox/Google homepage loads, but when I attempt to access any website I'm greeted with the horrifying "server not found" page. Any ideas why this might be happening? Did I not install it correctly?

---

### Post by CatoYounger on 2010-10-04
Hey man, how exactly did you get the wireless adapter working?

---

### Post by dineshs on 2010-10-05
please post the result of```
ping 4.2.2.1 -c3
```

---

