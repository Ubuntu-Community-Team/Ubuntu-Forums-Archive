---
title: "Help: Ubuntu and EPIA VIA mpeg"
date: 2005-11-14
forum: Multimedia &amp; Video
---

### Post by msmaulini on 2005-11-14
I trying to build a silent Linux box to play DVD's to a TV. I
bought a EPIA ME6000 (C3 Chip 586-MMX, CL266 with MPEG
and TV-Out (VT1622).
I've been installing Linux and reading forums and
documentation in the last 4 weeks and I'm becoming
crazy...
I have tried, Fedore Core 3 (slow), Gentoo (lost),
Debian Sarge(ok) and finally Ubuntu 5.1 (ok).
Please, be so kind to provide me some references:
1) The current Via driver is up to date? Which features do it include?
2) Is it possible to get MPEG optimization with the standard driver or Do I need another one? I have read a thread announcing a how-to but I did not find it.
3) Do I need DRI support for the MPEG ? Is everthing included in the same driver or they can be installed separetely?
Probably I could deal with the kernel optimization, however, do not hesitate to give me any suggestion.
Thanks in advance,
Regards
---
MSM

---

### Post by msmaulini on 2005-11-17
If anybody is interested, news on this subject:

I got ubuntu running with the included via driver and I can play DVD's with Xine after installing libdvdcss and some codecs. Info from the unofficial Ubuntu.

However, Xine reports frame lost and requests for optimization. I have compiled the Kernel for a VIA C3 cpu with mrl video memory optimization and maybe there is a slight improvement but xine insists on more optimization.

Expected result, this EPIA board is silent (fanless) and low power but the cpu horse power is also low. I need mpeg decompression if a want to play DVDs on it.
I'm reading more documentation about activating this feature. Keep informing.

---

### Post by poptones on 2005-11-17
Good deal. I've been considering one of the 10000 systems because I want to play with the encryption technology. Hope you're able to get good mpeg/avi playback.

---

### Post by luis31415 on 2006-03-28
Hello,

I also have a VIA ME6000, but when I try to install Ubuntu 5.10, after some startup text the screen displays just garbage.

Did you have any similar setup problem? I am using a 17" Acer monitor that has always worked fine at many different resolutions.

...Is there a way to, say, passing a parameter on startup, change the video mode of the setup tool?

Thanks,

   Luis.

---

### Post by msmaulini on 2006-04-05
:-| 

No I hadn't that problem. I'm using a 15" acer monitor and it works fine.
Performing a standard install, Ubuntu works as a typical desktop machine, openoffice, browsing the net, mail, etc. Much better than FC3 and Suse 9.2

Bad news is that I was not able to set the mpeg chip, I desperate and took a rest for some time... 4 months in fact.
The nice black box is there, waiting to start from the scratch one of those days.
---
MSM

---

### Post by TuxCrafter on 2006-07-15
Hello,

I have a ME6000 bios v1.16 i am pretty good with computers and also with linux. (no supper expert) ;) 

I am trying to get Ubuntu Dapper 6.06 LTS fully working with the same speed as in WindowsXP. I totaly tunned the box with XP and it was fast especialy boot time (2 times faster then a slow P4)

But I don't like the way Microsoft works with this world so I wanted to make my epia aslo go to linux. 8) 


The ME6000 alsmost workt out of the box NOT.

It is running far far to slow.

I cant get hdparm to use UDMA5 with my hdd and chipset (this is a know bug but is not resolved in ubuntu)

please try and post results
```

sudo hdparm -i /dev/hda
sudo hdparm -d1 -X69 /dev/hda

```
I aslo have a 10% higher cpu load with mpg decoding on linux vs windows.

Also i cant get my cpu muliplier to 5.5 instead of 4.5 this is a isue with the longhaul module.

I was trying to recompile the kernel but i am still trying

Also the USB speed of my epia is lower than with my athlon nforce2

Epia:
Timing cached reads:   264 MB in  2.02 seconds = 130.43 MB/sec
Timing buffered disk reads:   62 MB in  3.04 seconds =  20.39 MB/sec

Athlon:
Timing cached reads:   1764 MB in  2.00 seconds = 881.94 MB/sec
Timing buffered disk reads:   66 MB in  3.02 seconds =  21.82 MB/sec

By my dolby sound i got almost everyting working but my center and LFE are switched wrong. 

I am know going to try EpiOS special Linux distro for epia's to see if they got it working:-D

---

