---
title: "Nvidia 8600M GT How to disable the powermizer?"
date: 2009-06-07
forum: Multimedia Software
---

### Post by DeusExM1 on 2009-06-07
Hey Everyone,

I found out that the reason why compiz runs very poorly on my computer is because the powermizer is enabled for my video card. I want to disable it (im turnning Jaunty). I have tried the solutions i found on google but nothing worked. Some of them were outdated. What should i do?

---

### Post by Gausian on 2009-06-07
You turn it off by running 
```
gksudo nvidia-settings
```

go into the last option called nvidia settings configuration and un-check powermizer, then save.

how do you know that you're problem is powermizer if you havent turned it off for comparison yet?  Im not sure why you're getting poor performance.  your card is better than mine and i dont have any problems.

---

### Post by DeusExM1 on 2009-06-07
the reason why i know its powermizer is because i was looking at my clock speeds in the nvidia panel while trying out the effects.

When the clock is set to level 0 (170mhz 100 mhz) the effects are super sluggish. If i open or close a few windows then the powermizer makes the card go into level 3 (475 Mhz and 400 Mhz) which makes the effects go fluently. 

Most of the time i run my laptop without the battery, using the AC Power, so i dont even need the powermizer. 

I just did what you said and it seems to have helped a lot, although it still does stutter from time to time. Thanks a lot for your response.

---

### Post by marcone-xiii on 2009-07-31
I'm afraid that fix is just a placebo. All it does is disable the monitoring/polling of the current powermizer setting so it does not refresh. Unfortunately powermizer still works in the background.

Once I find the real way to turn off powermizer I will post it here. I have the same card as you.

---

### Post by marcone-xiii on 2009-08-01
Ok I found how to really disable it (or rather set it to a preferred level).

The method suggested by user 'pferraro' in this thread works:
[http://ubuntuforums.org/archive/index.php/t-1128260.html](http://ubuntuforums.org/archive/index.php/t-1128260.html)

I have mine stuck on the maximum performance level using the following xorg.conf

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"            "True"
    Option        "RegistryDwords"    "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection
```Works splendidly.

You might want to play around with the values to suit your needs. I haven't for example tried PowerMizerEnable=0x0 FWIW...

---

