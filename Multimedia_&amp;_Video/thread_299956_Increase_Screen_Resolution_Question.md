---
title: "Increase Screen Resolution Question"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by cdinoz on 2006-11-15
I have my Ubuntu box connected to my 40" LCD tv - currently at a resolution of 1024*768 with my old ATI9200se graphics card - running on Edgy (also havent been able to install the full ATI drivers yet - that is another issue)

The TV res can support 1360*768

Is there anyway I can increase the resolution to fully fit my TV?

---

### Post by Leonivek on 2006-11-15
> **cdinoz said:**
> The TV res can support 1360*768

Is there anyway I can increase the resolution to fully fit my TV?

Have you tried a:
```
**sudo dpkg-reconfigure xserver-xorg**
```
...and following the steps?

---

### Post by cdinoz on 2006-11-28
Excellent - cheers for that - will now give me my native resolution for my TV of 1366x768

:KS

---

### Post by Leonivek on 2006-11-28
No problem! :)

---

### Post by cdinoz on 2007-04-25
Re-Opening an old thread of mine in regards to screen resolution.

I have just upgraded to Feisty - now when I try to reconfigure xserver - and go through the motions of selecting the ATI input - the xserver no longer auto detects my graphics card nor auto detects the monitor and when I go through the motions the monitor goes out of range and the picture dissappears.

I am currently running the vesa drivers as neither fgrlx or ati seem to work

Any clues on how I get back my full screen res (currently running at a squished 1024*768 max.)

Would really love my 1360*768 back

I am still running using my old ATI9200se g/card

---

### Post by cdinoz on 2007-04-25
Bump anyone..???

---

### Post by strabes on 2007-04-28
You should simply be able to add the correct resolutions to the "Device" section of your /etc/X11/xorg.conf and then restart X with ctrl+alt+backspace.

---

