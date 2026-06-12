---
title: "Help with webcam in Skype, Ubuntu 9.10"
date: 2009-12-21
forum: Multimedia Software
---

### Post by pmulgaonkar on 2009-12-21
I have a webcam, an USB Ezonics Cam IV which worked fine in 9.04. In 9.10 it has strange behaviour that I cannot figure out.

In skype, after a reboot, the camera does not work. In the Skype config menu, the "test" button results in a blue square. Called parties get a black screen.

However, if I run Cheese, the camera works. And after that it works in Skype (until a reboot). So it looks like Cheese is loading something that causes the camera to start working. Can't figure out what it is, and how to load it myself directly.

Using lsusb, the camera reports as: 
```
Bus 003 Device 002: ID 0c45:613c Microdia PC Camera (SN9C120)

```

Any help would be much appreciated.

--p

---

### Post by pmulgaonkar on 2009-12-29
BUMP...

No hints? Anyone?

--p:(

---

### Post by pmulgaonkar on 2009-12-31
Should I post this is some other part of the Forums?

--p

---

### Post by Exploited1 on 2010-01-03
Hi everybody, hi pmulgaonkar, 

I am having a similar problem and haven't found a solution. 
I have 9.10 and skype version 2.1.0.47.
My integrated webcam is working just fine with Cheese and is not recognized with this VOIP service.

I am getting in the terminal after typing lsusb : 


Bus 002 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam


Hopefully anybody can help us.

---

### Post by bunnyhugh on 2010-01-03
Hi All,

This  is what worked for me.

I downloaded and installed the 64 bit deb from skype (don't believe this is true 64bit but 32bit with the required additional 32bit libraries)

Checked that the package lib32v4l-0 was installed.

Then used the "LD_PRELOAD" work around, found in the skype forums.

To check if this will work for you, assuming you have installed all the required libraries, open a terminal and at the prompt enter LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so and hit return, then skype and hit return.

Do the video test, if your webcam works you can change the skype menu command to the following:-

bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

so that it works from the menu.

Hope this is  of some help.

---

### Post by gradinaruvasile on 2010-01-03
If using the normal (32 bit) Ubuntu version the correct command is:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

in a terminal.

And the menu launcher:

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by whoboo on 2010-01-03
lsusb

Bus 003 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000

---------
2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
------------
lsmod |grep video
videodev               36736  1 gspca_main
v4l1_compat            14496  1 videodev

syslog:
Jan  3 19:07:44 householdone kernel: [  716.955560] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Jan  3 19:09:21 householdone pulseaudio[1622]: ratelimit.c: 81 events suppressed
Jan  3 19:09:30 householdone pulseaudio[1622]: ratelimit.c: 93 events suppressed
Jan  3 19:09:35 householdone pulseaudio[1622]: ratelimit.c: 1914 events suppressed
Jan  3 19:09:40 householdone pulseaudio[1622]: ratelimit.c: 2940 events suppressed
Jan  3 19:09:45 householdone pulseaudio[1622]: ratelimit.c: 3654 events suppressed

messages
84.068745] Linux video capture interface: v2.00
Jan  3 18:57:11 householdone kernel: [   84.456300] gspca: main v2.6.0 registered
Jan  3 18:57:12 householdone kernel: [   84.651362] gspca: probing 045e:00f5
Jan  3 18:57:12 householdone kernel: [   84.673012] sonixj: Sonix chip id: 11
Jan  3 18:57:12 householdone kernel: [   84.678978] gspca: probe ok
Jan  3 18:57:12 householdone kernel: [   84.679031] gspca: probing 045e:00f5
Jan  3 18:57:12 householdone kernel: [   84.679069] gspca: probing 045e:00f5
Jan  3 18:57:12 householdone kernel: [   84.679154] usbcore: registered new interface driver sonixj
Jan  3 18:57:12 householdone kernel: [   84.679171] sonixj: registered
Jan  3 18:57:14 householdone kernel: [   86.909892] usbcore: registered new interface driver snd-usb-audio

using Skype:  microphone doesn't work
using Skype:  nothing on video but green screen

video test in preferences/multimedia: green screen

Have added PRELOAD to skype command
have done [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

Help !!!!

---

### Post by frenchn00b on 2010-07-14
> **Exploited1 said:**
> Hi everybody, hi pmulgaonkar, 

I am having a similar problem and haven't found a solution. 
I have 9.10 and skype version 2.1.0.47.
My integrated webcam is working just fine with Cheese and is not recognized with this VOIP service.

I am getting in the terminal after typing lsusb : 


Bus 002 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam


Hopefully anybody can help us.


Has somehow a solution?

skype give GREEN COLORS 

and 

camorama it works


so the driver linux is ok, but skype sucks/

I have tried those versions, but no success :(

skype-debian_2.0.0.68-1_i386.deb
skype-debian_2.0.0.72-1_i386.deb
skype-debian_2.1.0.47-1_i386.deb

---

