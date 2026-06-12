---
title: "Acer Crystal Eye Webcam unrecognized"
date: 2011-09-24
forum: Multimedia Software
---

### Post by insecure hyena on 2011-09-24
Hi community here I am asking for help!
My problem is that suddenly the webcam (previously recognized) "disappeared from my system". The system I'm talking about is an Acer Aspire 4920 running the last release of Xubuntu (Natty Narwhal or if you prefer 11.04).
As I said the webcam, that previously was correctly detected by programs like Skype or guvcview, seems to be vanished from the laptop.
It doesn't appear in /dev where it must be present under the name of video0 and by running lsusb I only get the following results:

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What should I do know? Please someone help me...I'm really frustrated by this problem

---

### Post by insecure hyena on 2011-09-24
Guys I put the laptop to sleep and after the resume the webcam show itself once again! Here the results of the lsusb command:

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 022: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I confirm that now under /dev there's the video0 entry.
Now I'm really afraid to test if it really works...the last time that I tried with guvcview after it showed it "went offline" and than it "disappeared" from the system.
If there's some one able to explain what is happening here please intervene.

---

### Post by no2498 on 2011-09-25
this may or may not be the problem
look in your startup programs for any webcam program that comes on at startup and turn them off
restart the computer
and did you make this a bin/bash file the last time
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype



#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

---

### Post by insecure hyena on 2011-09-25
At first thanks you for your intervention ;) !
I think that what you explained is what (don't ask me how!!!) happened when a few days ago I put the laptop to sleep after disabling skype at startup...Yes I startup skype at boot :D!
However now it's all solved...so I mark this thread [SOLVED] :)!

P.S: if anyone have the same problem try what suggested by no2489. It wasn't necessary for me but the concept behind the codelines he wrote is correct! So thank you no2489 ;)

---

