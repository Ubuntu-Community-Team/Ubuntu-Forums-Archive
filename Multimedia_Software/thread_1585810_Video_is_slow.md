---
title: "Video is slow"
date: 2010-10-01
forum: Multimedia Software
---

### Post by manfredrasta on 2010-10-01
Hi everyone,

I have insatalled Lubuntu 10.04 on my old laptop Toshiba Satellite Pro 4600 (Pentium III).

I have installed the package of the flashplayer plugin so I can watch the video online.

The problem is that they go very slow. I didn't install any driver and:
```
marino@marino-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
```

Can anybody help me? How do I now wich driver should I install? And how do I do it? I am really noob

Thanks

---

### Post by manfredrasta on 2010-10-06
Also my desktop is slow... I think its a problem of driver. How do I check this?

Anybody?

I paste you my xorg.conf (I created it because I couldnt set my resolution up to 1024x768 ):

```
Section "Device"
Identifier "Trident Microsystems CyberBlade XP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier	"Default Screen"
Monitor	 "Generic Monitor"
Device	 "Trident Microsystems CyberBlade XP"
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 32
Modes "1024x768"
EndSubSection
EndSection
```

---

### Post by manfredrasta on 2010-10-15
I think it's because of the minimun RAM in my laptop

---

