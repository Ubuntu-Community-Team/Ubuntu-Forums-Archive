---
title: "Galaxy GeForce 7950GT AGP - problems"
date: 2009-11-25
forum: Multimedia Software
---

### Post by KingBongo on 2009-11-25
Hi. Today I got my new Galaxy (Nvidia) GeForce 7950GT AGP card. I managed to get a picture on my TV via S-Video into SCART (used in Europe). Driver 185. I have a few issues though.

1. I have no color. I suspect the reason is that the card recognizes the TV as NTSC (60Hz) instead of PAL (50Hz) since 60Hz is displayed in the Nvidia X Server Settings. How to change that? I couldn't find a way to change that easily anywhere, neither in the X Server Settings nor in the xorg.conf file. Do I have to alter the "HorizSync" and "VertRefresh"? If "yes" to what?

2. The fan seems more noisy than I expected, even under virtually no load. It runs at a constant speed no matter what. I tried changing the speed in NVclock just to get some reaction. Nothing. Is that normal? How to fix that?

I deliberately bought an Nvidia card to avoid problems, but here we go.

Help please!

---

### Post by KingBongo on 2009-11-26
I managed to solve the no color issue. The solution was simple. I just plugged the S-Video cable into another contact on the TV. For some reason I got color right away.

But the other problem is still open! The graphics card fan seems to be running at full speed all the time, even if the temperature is only like 50 degrees C. The data in NVclock indicates the fan should be running very slowly (less than 20% Duty Cycle), but that is simply not true. I cannot change the Duty Cycle either, or more precisely I can change it, but the fan does not react.

Can you control/alter the fan speed on this card? How? Help please!

---

### Post by KingBongo on 2009-11-26
I REALLY need some help here.

---

### Post by KingBongo on 2009-11-27
Ok. I believe the loud and uncontrollable fan of the 7950GT AGP is either fundamentally driver related (never worked), or that the new Linux Kernel (Ubuntu 9.10, Kernel 2.6.31.x) cracked a previously working driver. If so, I hope Nvidia and/or the Linux Community is/are working on this.

I have read that years back people have had problems with loud fans, but that was then. I don't know about now. 

So my questions are: Did somebody get the 7950GT AGP to fully work (I am most interested in a working fan control)? Did you get any of the 7-series AGP cards to fully work? Which xBUNTU version did you run? What did you do to make it work?

---

### Post by PariahVayne on 2009-11-27
Use nvclock from the repos to see if you can manually alter the fan speed. 

Try this;

```
sudo aptitude install nvclock
```Then;

```
nvclock -f -F 60
```

See if that works.

---

### Post by KingBongo on 2009-11-27
PariahVayne:
Thank you! But I already tried that, see above. Doesn't work. NVclock says the fan speed has changed, but the fan itself does not react, :(

---

### Post by PariahVayne on 2009-11-27
> **KingBongo said:**
> PariahVayne:
Thank you! But I already tried that, see above. Doesn't work. NVclock says the fan speed has changed, but the fan itself does not react, :(

Oh THAT ok. I have seen about this before and there doesn't seem to be an answer for it (although as I haven't had this problem so I haven't fully looked into it). It may be that your card may have a voltage problem with the fan, but it's more than likely THAT Linux issue, or less likely a driver issue, but I doubt it.

Out of curiousity, is there anyway you could test it on Windows?

---

### Post by KingBongo on 2009-12-01
PariahVayne:
Things like this is what keeps Linux from mass-acceptance. People like you and me can live with things like this, but what about average Joe?

Anyway. Since the 7950GT AGP is a few years old, I don't expect a general solution to this fan problem ever. Instead, here is how you "solve" problems in Linux, :p I used a soldering iron and connected a potentiometer in series with the fan. Now it is as quiet as the wind!

Please be careful if you want to do this yourself! After you have been turning the knob you MUST closely watch the temperature of your GPU until a stationary condition has been reached. Try stressing the card with the applications you normally use and be sure not to overheat! Do this at your own risk! Be careful, I cannot stress this enough.  

PS. At least I was able to solve this problem in some way. I have been playing around with an ATI HD3850 AGP before. I gave up on that one (which is a shame since that card supposedly is significantly better). I couldn't make it work. Annoying!

---

