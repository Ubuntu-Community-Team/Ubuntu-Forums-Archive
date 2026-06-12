---
title: "Help with dvr-qtgui"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by wayfarer51 on 2008-03-03
Does anyone have experience with [dvr-qtgui]("http://www.pierrox.net/dvr/") ?  I'd really like to get it going.    The website and man file are less than forthcoming about ANY problems, and I can't find it on the 'Net.

I'm running Gutsy with the 2.6.20-16-server kernel on a Dell Dimension 4700.  I use tvtime, and I've confirmed that it's on video0.

Any help would be welcomed.

Neill

When I run dvr-qtgui with tvtime off, I get:

```
bb@overthruster:~$ dvr-qtgui
<init> : Avifile RELEASE-0.7.47-070916-12:47-4.1.3
<init> : Available CPU flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
<init> : 2992.72 MHz Intel(R) Pentium(R) 4 CPU 3.00GHz processor detected

```

A Device Selection screen pops up asking me to select either the video device I'm using [ (Hauppauge Win TV USB 2 (/dev/video0) ], or the path to the V4L device file.

After entering either, I then get the following and a popup saying roughly the same:

```
Can't obtain the description of the video buffer mapping : Invalid argument

```

If I try it with tvtime on, I get the following with a popup that says mostly the same:
 
```
bb@overthruster:~$ dvr-qtgui
<init> : Avifile RELEASE-0.7.47-070916-12:47-4.1.3
<init> : Available CPU flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
<init> : 2992.72 MHz Intel(R) Pentium(R) 4 CPU 3.00GHz processor detected
No device found
```

---

### Post by cblanquer on 2008-04-13
Similar problem:
> <init> : Avifile RELEASE-0.7.47-070916-12:47-4.1.3
<init> : Available CPU flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
<init> : 1732.58 MHz Intel(R) Pentium(R) M processor 1.73GHz detected
Unable to open configuration file : /home/carlos/.dvrrc. A new default file will be created
*** WARNING *** : the driver doesn't provide a correct size for memory mapping. DVR tries to correct this error, but some strange things may happend, you are warned.
Can't map memory for capture : Invalid argument

I am running Kubuntu 7.10 and the TV card is a Hauppauge HVR-1300 which works perfectly under Kaffeine (DVB-T) and can catch analog video (tvtime).

Actually my target is to enable dvr so that I can record the analog video captured from a sat box (as I do in MS windows partition).
I have not found any reference regarding this, which seems rather to be an applicaiton bug !

---

