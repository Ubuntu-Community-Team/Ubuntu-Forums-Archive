---
title: "Skype Video Problem macbook 2.1 ubuntu 10.04"
date: 2011-04-16
forum: Multimedia Software
---

### Post by FireStorm102389 on 2011-04-16
Ok, I searched around an couldn't find anything like what I'm experiencing right now...

I have a macbook 2.1 and successfully installedubuntu 10.04 with no problems other than the headphone jac doesn't work and the iSight i had to follow instructions to make it work..however, I cannot use it in skype. It works with cheese and ekiga, but most of the people I chat with are on skype. The driver on skype says "built-in iSight (v4l2) whereas the skype says "built-in iSight (/dev/video0) when I go into the gstreamer-properties, for video it is selected as V4L2 and in the pipeline it reads (v4l2src device="/dev/video0")

When I click test it all works fine, its just that skype doesn't work with the camera. shows I have one, I click test in skype settings and the screen stays black and the green light showing its on turns on....and when I'm in a call i try to make it work and it flashes the green light and doesnt work at all... anyone know a solution or haing the same problem?

---

### Post by FireStorm102389 on 2011-04-16
ok, I just looked in my cheese program settings, and apparently its using the same thing as skype is for camera...so y is that working and in skype it isn't?

---

### Post by tigerZERO on 2011-04-16
I'm also having this problem, maybe the update to the headers screwed things up? Anyway, at first nothing would recognize the camera, even with isight.fw in /lib/firmware so I updated the isight-firmware-tools from mactel-support's PPA.

That allowed Cheese to access the camera, but Skype still can't run it. When I start video during a call, the light pops on for a second but turns right back off. The test in the options flips the light on indefinitely, but the screen remains black.

lsusb returns:
> 
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:021a Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by FireStorm102389 on 2011-04-17
alright, my fellow non-camera working friend...i went to check the skype forum and this link showed up...ur problem is exactly same as mine, here's what you need to do...
Open your terminal and type

 ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
Hit enter, sign in, and your good to go!

---

### Post by tigerZERO on 2011-04-19
Awesome, it worked straightaway! Thanks much, is this a permanent fix or do I have to launch from the terminal with this command every time?

---

### Post by FireStorm102389 on 2011-05-07
sorry it took so long to reply, and to answer your question, i honestly don't know. However, you can add an icon on your desktop or in your awn menu and change the command to that one and it will load like that without using terminal.

---

### Post by edfast on 2011-05-19
Hello,
 
latecomer to this thread, as to ubuntu, but with identical problem. Isight has been properly installed and shows up in Skype options, but screen remains black. Tried your fix, however, on my macbook 2,1 (Natty) the terminal returns:
 
ERROR: ld.so: object '/usr/lib/libv41/v411compat.so' from LD_PRELOAD cannot be preloaded: ignored.
 
No room for doubt there, I'm afraid.
 
You or anyone out there knows of a reason for this, or a solution?

---

### Post by josuf107 on 2011-12-26
> **edfast said:**
> Hello,
 
latecomer to this thread, as to ubuntu, but with identical problem.  Isight has been properly installed and shows up in Skype options, but  screen remains black. Tried your fix, however, on my macbook 2,1 (Natty)  the terminal returns:
 
ERROR: ld.so: object '/usr/lib/libv41/v411compat.so' from LD_PRELOAD cannot be preloaded: ignored.
 
No room for doubt there, I'm afraid.
 
You or anyone out there knows of a reason for this, or a solution?

I know this is old but if you're still having trouble you should try  copying and pasting this. 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
A few of the l's became 1's when you typed it  into the terminal.

---

### Post by ghostnix on 2012-02-03
This may have already been solved. But I thought of posting here for future reference.

I managed to get video working in skype (Linux Mint 12) using this command:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

---

### Post by MxGB on 2012-05-08
Just to add that in Precise 12.04, the equivalent command line for Skype is:
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by Moonigan on 2012-07-05
MxGB: THANK YOU!

---

