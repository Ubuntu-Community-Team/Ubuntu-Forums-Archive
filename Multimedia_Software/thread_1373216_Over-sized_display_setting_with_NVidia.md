---
title: "Over-sized display setting with NVidia"
date: 2010-01-05
forum: Multimedia Software
---

### Post by gnitram on 2010-01-05
Good evening all,

I am new to Ubuntu (Karmic with GNOME) and have come unstuck, efforts to find solutions on the forums etc have not yet helped me.

I have a Samsung LED UEB7020, with an Asrock ION 330 BD player feeding to a Onkyo TXSR607, AV rec.  The other day I downloaded NVidia v180.25, which was very useful, because it immediately solved an earlier teething problem of no sound. However immediately upon re-booting and ever since, the screen size is too big for the TV, meaning that I can not see the top, bottom, side and left of the display by about 2 inches either way. I have checked the NVidia resolution settings and they are correct for the TV, ie 1920 by 1080.

Any pointers or help would be much appreciated.

My etc/X11/ xorg.conf file reads as follows:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


John

---

### Post by gordintoronto on 2010-01-05
I would expect there to be an HDMI cable from your computer to your TV.  Is that what you have?

If the size is off, change the TV's settings.

---

### Post by RedRat on 2010-01-05
Might want to look into the horizontal and vertical refresh rates in your nvidia settings. Sounds like it might be using 50Hz in place of 60Hz.

---

### Post by gnitram on 2010-01-05
You are quite correct Redrat,  my NVidia setting is using 50Hz instead of the 60 HZ, which the Samsung TV is. 

The error message appears "failed to parse to existing X config file", when I change the setting to 60 Hz, and also I note that by applying the changed NVidia settings to 60 Hz, it still did not alter the over-sized display.

I am hesitant to at this stage alter the TV settings, given that it was all working perfectly as far as image goes, until the NVidia drivers were activated.

Thank you very much for all of your suggestions, it is much appreciated.

---

### Post by gnitram on 2010-01-05
Gordintoronto,

I have a HDMI cable going from my ASrock ion330 to the av receiver and the AVR feeds out via HDMI to the TV set. I was trying to avoid altering the TV settings at this stage, because it was all going fine image-wise until the Nvidia was installed. 

 I am trying for a fix via the drivers if possible. Note anyway, that the TV display is still reading as 1920 by 1080, when I switch the source to Asrock Ion.

---

### Post by gnitram on 2010-01-05
I note that the display monitor in NVidia  config is listed as the AV receiver (as this is what the applic detected when I enabled it), would it fix the problems if I find a way to alter this to Samsung TV model no#, e.g should I uninstall Nvidia, then re-install whilst the TV is connected directly to the ASrock ion?

---

### Post by RedRat on 2010-01-05
If you have Nvidia-settings installed you can select your monitor or AV device. Try that first. You seem to be using the most up to date Nvidia drivers, I think you mention the 185.x driver set, so the monitor/TV set ought to be in there.

If you do not have nvidia-settings use synaptic or apt-get. When you run the program you must run it using "sudo" otherwise the changes won't stick.

---

### Post by gnitram on 2010-01-05
OK so I will leave it as it is with the AV receiver model no. marked as the monitor (I couldn find a way to change this to Samsung TV). 

I do have v185 for NVidia and I therefore already have NVidia settings, correct?

---

### Post by RedRat on 2010-01-05
> **gnitram said:**
> OK so I will leave it as it is with the AV receiver model no. marked as the monitor (I couldn find a way to change this to Samsung TV). 

I do have v185 for NVidia and I therefore already have NVidia settings, correct?
You may well have to install nvidia-settings. I run 8.04 Hardy so I had to install this program from synaptic. I am running an older driver for my system, so I can't say if it comes with that driver for sure. 

There is a gui for nividia settings, you run the code in the terminal:
gksudo nvidia-settings

You must run it using either sudo or gksudo because it writes to the xorg.conf file. Now what I am saying here is based on my use of 8.04 and it may well be slightly different for 9.10.

---

### Post by gspat on 2010-01-05
I had this problem... your tv is simply "Overscanning"...

Check through your menus for some sort of "adjust picture size" setting.

---

### Post by gnitram on 2010-01-06
THanks everybody, problem is solved, it was over-scanning on he TV and I just adjusted the TV to screen-fit.

---

### Post by gordintoronto on 2010-01-06
Now you could mark the thread as "solved".

---

