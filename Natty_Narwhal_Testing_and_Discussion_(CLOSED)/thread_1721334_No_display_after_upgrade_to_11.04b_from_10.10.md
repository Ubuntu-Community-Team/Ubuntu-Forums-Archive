---
title: "No display after upgrade to 11.04b from 10.10"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by caish5 on 2011-04-04
Can anyone help me with this?

I just did an upgrade to 11.04 and lost all display after the flashing cursor on boot.
I finally went into grub and added a "nomodeset" in there.
Now i can use the computer but the resolution is all wrong and my display is not detected.
I have the following graphics chipset.
0:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)

Thanks

---

### Post by rykel on 2011-04-04
@caish5: Which line did you add "nomodeset" to? Also, what is the kernel version that worked for you - at least with regards to booting up a GUI?

---

### Post by cariboo on 2011-04-04
There is a new version of Xorg-xserver, the previous driver doesn't work with it, and so far there isn't an updated one. Unity 3D won't work, but you can install Unity 2d from the repositories.

---

### Post by caish5 on 2011-04-04
@rykel - I added the nomodeset between "ro and "quiet" on the commands before boot line.

The kernel is 2.6.38-7-generic

@cariboo907 - Is that likely to change before final release?

---

### Post by cariboo on 2011-04-04
I really doubt it, I don't think there is anyone working on it.

---

### Post by caish5 on 2011-04-04
You know this whole Unity thing is starting to worry me. Apart from some rather odd usability issues, they're gonna break compositing support that i've had ever since it was invented. 

Now I could go buy a graphics card, but why would I if it's a six monthly moving target. I just got my 5.1 sound back with Maverick!

---

### Post by cariboo on 2011-04-04
Have you tried the i915 driver? that should work with your graphics chipset, boot into recovery mode, and select failsafeX from the menu. once at the low graphics desktop, try and insert the module:

```
sudo modprobe i915
```

if you don't get any errors, reboot, and see what happens.

---

### Post by caish5 on 2011-04-04
Tried it. No errors.
After reboot the result is the same. Boots up fine but no display just blank screen.

---

### Post by cariboo on 2011-04-04
Can you drop to a terminal, by pressing Ctrl-Alt-F1? Do you have an /etc/X11/xorg.conf?

---

### Post by caish5 on 2011-04-05
Dropping to a terminal also results in a blank screen.
If I try to Ctrl-Alt-F1 after starting the  failsafe session i can see a variety of terminal looking screens but none with a login prompt.
There is no /etc/X11/xorg.conf

---

### Post by caish5 on 2011-04-05
Just made a discovery.
If I use a VGA cable rather than my usual HDMI the computer boots fine, compositing, correct res, monitor detection and all.
I'd like to get the HDMI working if possible though as it does make for a sharper image.

---

### Post by caish5 on 2011-04-05
After a bit of googling i found this post..
[http://forums.whirlpool.net.au/archive/1503017](http://forums.whirlpool.net.au/archive/1503017)

Turns out if plug the TV into both VGA & HDMI I can see the info for both outputs.
Then it's just a matter of making the hdmi one default, disabling and finally unplugging the VGA connection.

Weird but Solved!

---

