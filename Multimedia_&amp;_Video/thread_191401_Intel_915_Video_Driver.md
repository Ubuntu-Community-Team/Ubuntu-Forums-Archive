---
title: "Intel 915 Video Driver"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by adityasen on 2006-06-07
Hi all..

Been using Dapper on my Laptop, and it works gr8. Except for the video that is. Vid playback is jerky, esp in full screen mode. Tried out all possible players. And even normal window movement, draggin etc isnt exactly what I would call smooth. So my guess is that I have to get the correct video drivers. I have an intel 915GM video integrated chipset. now I have absolutely no idea how to install the drivers in linux. I know the drivers are available from the intel website, and are available in a .tgz package ([http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2159&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2159&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)). 

so yeah...it would be great if someone told me how to go about installing it.

cheers..
aditya

---

### Post by brsseb on 2006-06-07
Im gonna jump on and request the same. I briefly shimmed though the release notes, but the installation is very generic and Im not sure if all the file system paths are compartible with how Ubuntus X-system is located. If anyone can shead some light on this, we would be very grateful.

I myself is having the same problem, with jerky movies and windows, and it refuses to properly work with my external monitor. Hoping that a driver change (from teh default i810 one) might do the trick.

---

### Post by adityasen on 2006-06-07
and might I add...
When I play vids, they seem to play fine in VLC / Totem. But if I switch to full screen mode, they get jerky...

---

### Post by adityasen on 2006-06-07
Ok Ok. I think I've managed to fix the video playback to a decent extent.

I edited the xorg.conf file, and replace set the video driver from "vesa" to "i810", and added a new line specifying video memory

VideoRAM 65536

That seems to have done the trick. No more jerky playbak.

But a new problem has risen.
Not all colors display properly in the videos. The color definition does not seem proper. Any fixes on that?

---

### Post by adityasen on 2006-06-07
Ok. I managed to fix it to some extent. Edited the xorg.conf file and replaced the "vesa" driver to "i810" and added a new line, 
VideoRAM 65536

That seems to have done the trick. No more jerkyness.
But the vids are now not as bright as they were. The color definition does not seem correct.

Any fixes on that?

---

### Post by brsseb on 2006-06-07
Hmm, I havent tried spesifying the video ram. I just checked the Xorg.0.log and noticed it had autodetected the 128-ish MB of ram the video card is alowed to steal from the main memory. Ill try putting 128mb in the xorg-file too, just i case. 

You say the colors aint the same..sure you are using 24-bitmode?

---

### Post by adityasen on 2006-06-07
Yeah. I'm using the 24 bit mode.

But i've been tweaking around a bit, and noticed a few things.

1. If I choose the video output as xvideo, then I get flawless full screen playback, but dull overall. 

2. If I choose the X11 output, I get back the brightness / colours, but full screen playback becomes jerky again!!!

anyone out here to help?

---

### Post by ed_agamemnon on 2006-06-07
look at the 915resoltion package...

---

### Post by adityasen on 2006-06-08
[QUOTE=ed_agamemnon]look at the 915resoltion package...[/QUOTE]

I have installed the 915 resolution package, but what am I supposed to do next? It does not change anythin. And there's no apparent way I can seem to configure anything...

---

### Post by freddo on 2006-06-09
Hey, I am using Dell laptop d620(915) with dapper and feel that the general response from gnome/other apps could be better, CPU(2Ghz CD) works quiet much when stuff moves on the screen. It feels like the graphics should res ponse faster, any hints?

---

### Post by adityasen on 2006-06-09
[QUOTE=freddo]Hey, I am using Dell laptop d620(915) with dapper and feel that the general response from gnome/other apps could be better, CPU(2Ghz CD) works quiet much when stuff moves on the screen. It feels like the graphics should res ponse faster, any hints?[/QUOTE]

try running sudo dpkg reconfigure xserver-xorg

---

### Post by adityasen on 2006-06-13
i've also noticed that if I change the resolution to 800x600 from 1024x768, then the video playback has no problems. anyone have any fixes?

---

### Post by mrvw0169 on 2006-06-14
915resolution does not apply here... it is just a video BIOS hack in the case that your resolution is not detected/supported (like my widescreen 1280x800)...

I've found xv to be the best overall and much higher quality than x11/xshm <-- software rendered it seems...

Weird, because over here everything works very smooth and I have Intel 855GM (64 MB but didn't set it in xorg.conf) and running compiz/AIGLX for 3d effects with no problem and using 16/24 bit depth... XGL is horrible though...

Maybe... this in xorg.conf will help? My driver is set to i810 and the kernel loads i915 and drm modules... so maybe you can try modprobing them if they aren't loaded?

```
Section "DRI"
        Mode    0666
EndSection
```

And I have also a stripped down and patched -ck kernel which makes everything much snappier...

---

