---
title: "TripleHead2Go vs Kubuntu"
date: 2013-05-03
forum: Multimedia Software
---

### Post by fr2632 on 2013-05-03
Hey Guys,

I am not able to set a resolution of 4320x900 with my TripleHead2Go with 3x 22 inches monitors.

I contacted the Matrox support and this was the answer:

"Please take note that there is no official support for Matrox GXM products for use with Linux. If you do currently use a windows based system, you can configure the basic (standard) resolutions such as 3840 x 1024 which should be picked by the Linux based system. If you are using unique resolutions (such as the 4320 x 900 you had specified in your message), you must know how to modify and/ or edit your &#8220;Xorg.config&#8221; to include the modeline:

```
Modeline "4320x900 (3x 1440x900 60Hz)" 251.07 4320 4336 4352 4480 900 903 912 934 -HSync +VSync"
```

I follows the suggestion of this guy here : [http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/)

and created my own 10-monitor.conf file with the following entry:

```
Section "Monitor"
   Identifier "Monitor0"
   Modeline    "4320x900" 251.07 4320 4336 4352 4480 900 903 912 934 -HSync +VSync
EndSection

Section "Screen"
   Identifier "Screen0"
   Device "DVI-I-1"
   Monitor "Monitor0"
   DefaultDepth 24
SubSection "Display"
   Depth 24
   Modes "4320x900_60.00" "1440x900"
EndSubSection
EndSection
```

But when I reboot nothing has changed! The Nvidia X server settings gives me the max resolution of 3840x1024 which all is squeezed...

Tried to boot with Win7 and there is no problem, the resolution is 4320x900 with 60Hz. As video card I have an Nvidia GF116 [GeForce GTS 450] and the Linux version is:

```
3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686 i686 i686 GNU/Linux
```

From the terminal, when I type "gtf x y r" I get this which looks weird:

```
# 0x0 @ 0.00 Hz (GTF) hsync: -nan kHz; pclk: -nan MHz
Modeline "0x0_0.00"  -nan  0 -2147483648 -2147483648 -2147483648  0 1 4 1  -HSync +Vsync
```

Any help/suggestions?

Thanks!

---

