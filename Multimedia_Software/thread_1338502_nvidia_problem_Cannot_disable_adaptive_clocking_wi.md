---
title: "nvidia problem: Cannot disable adaptive clocking without setting it to &quot;high&quot;"
date: 2009-11-26
forum: Multimedia Software
---

### Post by tbraun on 2009-11-26
Hello!

I would like to permanently set the onboard nvidia card in my laptop to its lowest frequencies. I'm not a gamer and for the little bit of compiz I use the lower frequencies would still suffice and keep the laptop running cool. Adaptive clocking (frequency scaling) seems to work well ( can use nvidia-settings to see the frequencies changing), but as documented in other places, this causes my display to start flickering after a while.

Configuration: Ubuntu 9.10 on a Dell Latitude D820 with on-board nvidia card, described by lspci as: "nVidia Corporation G72M [GeForce Go 7400] (rev a1)". I run the proprietary nvidia driver, version 185. 


In several places on the web you find information that supposedly you can set the GPU frequencies to fixed, low levels by adding this line to the xorg.conf file:

```
Option "RegistryDwords" "PowerMizerEnable=0x1; PowerMizerLevel=0x3; PerfLevelSrc=0x2222; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x3"
```

This should disable frequency scaling and set the GPU permanently into the lowest power consuming mode. However, when I add this line, reboot and start nvidia-settings, I can see that my GPU is now stuck in the highest (!) CPU frequency, rather than the lowest.

I tried a number of changes to those values, but the result is always the same. Removing this line enables proper frequency scaling again.

What's wrong here? Has anyone successfully set their nvidia card to the lowest, coolest level? Is nvidia-settings reporting correctly?

BTW, I also enabled 'coolbits' and tried to manually reduce the GPU frequency with nvidia-settings. But that also has no effect at all: I set the frequencies to 100/400 and it cheerfully tells me that it now has set the frequencies to 450/700!

Any help is greatly appreciated...

---

