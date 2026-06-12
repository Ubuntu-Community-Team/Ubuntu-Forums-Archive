---
title: "Kernel &amp; Xorg video drivers"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by nickmcg on 2006-10-04
Can anyone enlighten me as to the link between the linux kernel graphics support and the Xorg video driver?

The reason that I ask is that I have a VIA CV860A machine with on-board VT 8601A graphics controller (this is reported as a Trident Cyberblade).

I've rebuilt the kernel with the appropriate cyberblade driver, but there seems to be no equivalent in Xorg - whatever driver I use in the kernel, Xorg uses Trident.

Thanks

Nick

---

### Post by nickmcg on 2006-10-11
In the absence of any reponses (did I post this in the wrong section?), I thought I'd post the link I've found:

If I load the cyblafb kernel driver, I can then use the fbdev xorg driver (althought this has its problems on my system - refresh rate is set to 56 Hz rather than 60 or 70)

...it's not much, but its a start ....

Nick

---

### Post by tseliot on 2006-10-11
Try setting the driver to "vesa" in your /etc/X11/xorg.conf

If you have problems with its refresh rate and resolution read this guide:
url]http://doc.gwos.org/index.php/ChangeResolution[/url]

OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by Radiera on 2006-10-11
Well, I'm on vesa drivers too because the nv caused random freezes of X (mouse cursor still moving, though). With vesa I have no crashes, but I'm stuck on 60 Hz. I would like to try installing nvidia drivers, but none of methods I've tried work. I'm starting to miss Windows...

---

### Post by tseliot on 2006-10-11
> **Radiera said:**
> Well, I'm on vesa drivers too because the nv caused random freezes of X (mouse cursor still moving, though). With vesa I have no crashes, but I'm stuck on 60 Hz. I would like to try installing nvidia drivers, but none of methods I've tried work. I'm starting to miss Windows...

Try this guide (even if your card is not PCI):
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by Radiera on 2006-10-11
Thnks, for your answer bui it did no good.

I have a 6600 GT gpu, mobo Asus A7V600-x.

At some point, in xorg.0.log i see these lines:

(WW) VESA(0): Bad V_BIOS checksum # i guess it's from the vesa driver

(II) NVIDIA(0): Detected PCI Express Link width: 16X
Ok, this one is weird! I have an AGP card (maybe it's because 6600 is PCI-E native?)

Thanks for your attention.

---

### Post by Radiera on 2006-10-11
I also have a bunch of warnings like this one:
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000508, 0)

Sorry, I couldn't edit my post.

---

### Post by mojoman on 2006-10-12
> **nickmcg said:**
> In the absence of any reponses (did I post this in the wrong section?), I thought I'd post the link I've found:

If I load the cyblafb kernel driver, I can then use the fbdev xorg driver (althought this has its problems on my system - refresh rate is set to 56 Hz rather than 60 or 70)

...it's not much, but its a start ....

Nick

Just a short note. In another thread a xorg.conf has been posted that is supposed to work with the trident card. I myself have recently installed Debian on my laptop so I haven't given it a go myself but do try it out and please keep me posted. :D 

[http://www.ubuntuforums.org/showthread.php?t=211937](http://www.ubuntuforums.org/showthread.php?t=211937) 

All the best
/Mojoman

---

### Post by nickmcg on 2006-10-15
The video output is ok with vesa or trident drivers.

I tried using a "modeline" setting in xorg.conf, but that made no difference to the fbdev driver - is this a limitation of fbdev - 56 Hz refresh rate only?

This is all becuase I'm trying to improve video acceleration

Nick

---

### Post by nickmcg on 2006-10-15
> **mojoman said:**
> Just a short note. In another thread a xorg.conf has been posted that is supposed to work with the trident card. I myself have recently installed Debian on my laptop so I haven't given it a go myself but do try it out and please keep me posted. :D 

[http://www.ubuntuforums.org/showthread.php?t=211937](http://www.ubuntuforums.org/showthread.php?t=211937) 

All the best
/Mojoman

Have you got any 3Dd acceleration on your laptop?

Nick

---

### Post by mojoman on 2006-10-15
> **nickmcg said:**
> Have you got any 3Dd acceleration on your laptop?

Nick

Nope, none at all. When I tried to run any program that required 3D it came to a screaching halt. Right now I'm trying to run Debian on it instead to see how the card works on that OS but now I'm having problem with my wireless instead so I haven't even started looking at the trident yet. :-k 

/mojoman

---

### Post by nickmcg on 2006-10-16
> **mojoman said:**
> Nope, none at all. When I tried to run any program that required 3D it came to a screaching halt. Right now I'm trying to run Debian on it instead to see how the card works on that OS but now I'm having problem with my wireless instead so I haven't even started looking at the trident yet. :-k 

/mojoman

Good luck with the wireless. Let me know if you get any joy with the 3D.
It looks to me as though the 3D aceleration dropped out of the Mesa package when it went from monolithic to modular. I looked at Zenwalker - v fast, but no 3D.

Cheers

Nick

---

