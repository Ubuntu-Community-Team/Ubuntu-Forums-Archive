---
title: "Which video driver to use for my media center"
date: 2010-01-22
forum: Mythbuntu
---

### Post by meazz1 on 2010-01-22
I build a media center using an Asus M3A78-EM motherboard which has on board ATI Radeon HD3200 GPU video card.
After installing Mythbuntu 9.10, I notice that it has an option under hardware, driver for propitiatory driver which is not activated.
Should I use the Ubuntu driver or the propitiatory driver?

---

### Post by myth1914 on 2010-01-22
The proprietary driver is just that.  It works well and enables the 3d rendering capabilities of the card.

While it may not be AS stable as the default ubuntu driver, it will serve you well and provide for much of the video experience the card has to offer.

(I still prefer nVidia)

---

### Post by meazz1 on 2010-01-22
> **myth1914 said:**
> The proprietary driver is just that.  It works well and enables the 3d rendering capabilities of the card.

While it may not be AS stable as the default ubuntu driver, it will serve you well and provide for much of the video experience the card has to offer.

(I still prefer nVidia)

Thanks for your input.

---

### Post by myth_cougar on 2010-01-25
I have really good results with the radeonhd driver, including audio via hdmi.  I always had problems with video tearing with the radeon and ati drivers but not with the radeonhd.

---

### Post by bbruenfl on 2010-01-25
I'm running a Jetway JMA3-79GDGEXL-LF with the 790GX/HD3300 chipset using 9.12.  9.10, from the repos, was giving me some issues with HDMI sound (no sound) and tv playback (double image).  

There is a great howto for installing 9.12 here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI ]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

One note about switching to the proprietary drivers has to do with XvMC.  ATI doesn't have any support for XvMC.  I had the default CPU+ settings in TV Playback selected.  The settings worked fine with the opensource driver but, when I switched, the call to XvMC when playing 1080p captures caused a segmentation fault in the mythfrontend.  If you get the same problem you'll have to choose a different rendering option for the settings that call XvMC in Utilities/Setup --> TV Settings --> Playback.

Like the above comment, if I had to do it over I would likely go with an Nvidia based board.  Support for Nvidia hardware seems to be a bit better.

---

### Post by bbruenfl on 2010-01-25
Trying to solve a video tearing issue with my 790gx I ran across this

[http://ubuntuforums.org/showthread.php?t=1385896](http://ubuntuforums.org/showthread.php?t=1385896)

Looks promising :D

---

