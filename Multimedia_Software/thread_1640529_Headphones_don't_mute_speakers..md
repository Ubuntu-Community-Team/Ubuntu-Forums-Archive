---
title: "Headphones don't mute speakers."
date: 2010-12-07
forum: Multimedia Software
---

### Post by TheoJava on 2010-12-07
Right now I'm running Linux Mint 9. I was running Ubuntu 10.10, but wanted to try Mint out. Anyway, I have the same problem on both OS's. When I plug my headphones in, the computer will continue to play sound through both the headphones and the speakers.

At first I thought it might be a driver issue, but now I'm starting to wonder if that's not the case. My sound can be output through two different areas on the computer. The first is in the back of the tower, where a wire connects the sound to some speakers that are built into the screen. The part where I plug my headphones into is built into a part in the front of the tower, which also houses other hookups, like usb ports.

Any thoughts as to how to fix this? I can submit additional info as needed.

---

### Post by TheoJava on 2010-12-08
Bump

---

### Post by Yellow Pasque on 2010-12-08
So jack sensing isn't working. What computer do you have and what is output of:
```
aplay -l
```

---

### Post by TheoJava on 2010-12-08
It's an HP Pavilion desktop, and the output is:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by TheoJava on 2010-12-09
Also, I loaded up Sysinfo, and checked under sound card. This is what it showed:

Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev01)
Subsystem: Hewlett-Packard Company Device 2a5e

---

### Post by TheoJava on 2010-12-09
bump

---

### Post by TheoJava on 2010-12-10
Am I not following this boards etiquette very well or did I post my problem on the wrong board?

---

### Post by joo-25 on 2010-12-11
I had the same problem in mint 9, I work on Toshiba L650

please help *_*

---

### Post by Mr_G on 2010-12-11
I use a toshiba l640d and the sound does not play from the headphones.

While searching the forums this is wat I found.

[http://ubuntuforums.org/showthread.php?t=1608661](http://ubuntuforums.org/showthread.php?t=1608661)

So if you are using Maverick then you may want to compile your own kernel for OSS support.

I am going to try it ...............it may or may not help but it's worth a try

---

### Post by TheoJava on 2010-12-11
I'm not sure that applies to me though, because Mint 9 is based on Ubuntu 10.04, not 10.10.

---

### Post by Yellow Pasque on 2010-12-11
> **Mr_G said:**
> So if you are using Maverick then you may want to compile your own kernel for OSS support.
This is unrelated to the topic (jack sensing).

---

### Post by TheoJava on 2010-12-13
bump.

---

### Post by TheoJava on 2010-12-16
Lalala

---

### Post by Brain Fire on 2011-02-13
I have the exact same problem with almost the same computer (mine's a laptop). I think the problem here is that there needs to be a driver written for our computers. But anyway, I think I have found a solution, I went into "System > Preferences > Sound" I clicked on the "Output" tab then changed "Connector:" from "Analog Speakers" to "Analog Output".

The audio has been muted to the built-in speakers (whether or not the headphones are plugged in) and the headphones continue to work.

I hope this works for you too!

---

