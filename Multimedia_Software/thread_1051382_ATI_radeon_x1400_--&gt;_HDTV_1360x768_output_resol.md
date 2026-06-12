---
title: "ATI radeon x1400 --&gt; HDTV 1360x768 output resolution(SVGA)"
date: 2009-01-26
forum: Multimedia Software
---

### Post by konradpiskorz on 2009-01-26
I am trying to get the output of my radeon x1400 card to output the native resolution of 1360x768 to my new TV through the VGA output.

I would just like to mention that ati and xorg simply do not seem to like each other.

First off in the catalyst control center, the TV allows a maximum resolution of 1280x800 which is the maximum resolution of my laptop lcd.  No matter what I do I can not select a higher resolution in ubuntu.

I've tried adding modes to xorg.conf and nothing every happens.  The utility aticonfig simply does not work.  It always fails regardless of what command you enter.  My guess is xorg and ati are fighting for control and Im the one who ends up losing.

Now I'm 95% sure that the ati proprietary drivers from ati's website are being loaded.  I say 95% as I don't know how to tell exactly what driver is being loaded, however the fglrx drivers should be.

What could it be?  Editing xorg.conf either does nothing, or breaks X.  Aticonfig simply doesn't work.  Could there be kernel problems?  Do I need to recompile it?  Could ati and x be fighting for control? Is that why aticonfig doesn't work.  Did I just install the drivers incorrectly?

Sigh
Konrad

---

### Post by konradpiskorz on 2009-01-27
Added Info

Following this how-to to fix my sound : [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I noticed along the way that while installing something(dont know what)

```
fglrx: Multiple versions in DKMS. Unsure what to do. Resolve manually.
```

As far as I can tell DKMS stands for Dynamic Kernel Module Support.  So somethings up with my kernel perhaps?

---

### Post by konradpiskorz on 2009-01-27
After perusing the xorg syslog files I found a simple work-around.  The EDID code was being transmitter properly for the 1360x768 resolution, just being set as a "Future Possible Mode".

I dont know what that means.  But it meant that my video card knew it could do it, it just didnt want to with my laptop monitor on.


So the Solution (With proprietary fglrx ati driver)

1) Start X normally with TV connected.
2) In amdcccle -->  Switch TV on to clone mode.  
3)                  Turn off(Disable) Laptop LCD.  
4) Restart X (Ctrl+Alt+BkSpc)
5) Tv is now available in 1360x768 modes :)

Not exactly what I had in mind... but it will do for now :P  Perhaps there is another way to set the desktop size of the TV bigger than 1280x800 (1280x720 visible) when the laptop LCD is on..

I am marking this solved even though it is only a workaround.  If anyone posts a better way I would be happier, but this is ok for now.

---

