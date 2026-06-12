---
title: "mythbuntu 9.10 desktop overscaling"
date: 2010-01-22
forum: Mythbuntu
---

### Post by mythbuntu101 on 2010-01-22
I have an hdtv (LG lh30 37inch, 1080p). I'm having difficulties controlling  desktop overscaling runing mythbuntu 9.10 w/ dvi output. my motherboard is asus m4n78 pro (integrated nvidia 8300 w/ both dvi and hdmi out) what is the way to control desktop overscaling?

---

### Post by SiHa on 2010-01-23
There is no easy way to stop overscan of the desktop, when using DVI/HDMI. You can make the Mythtv GUI only use the visible part of the screen, either using the screen display wizard of manually adjust the GUI size. Both in the frontend setup screens.

But you'll still be stuck with the desktop losing it's edges. If you want to stop this, ie remove overscan completely, the only option is to see if it can be turned off on your TV. Some sets will have an option called Just Scan, or something similar. My Panasonic just has an 'Overscan On/Off' menu option. If you can't find it, there maybe a hidden service menu, try Googling for it.

[[COLOR="Blue"]_This_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1003099&page=2) thread does claim to be able to adjust the desktop size my making a custom modeline, but it looks very fiddly.

---

### Post by itlarson on 2010-01-23
I've lived with over-scan on my panasonic plasma TV for two years with this simple hack:  
-In the mythtv's appearance setup menu, fiddle with the GUI width, height, and offset until the  edges are no longer cut off.
-in xfce's workspaces configuration applet, set the borders so that apps don't go off the edges of the screen when they are maximized.
-create launchers on the desktop for your commonly used apps.
-in the xfce panels aplet turn all panels off.
-now you can switch apps with alt-tab.  Control-alt-d will show the desktop, where you can start apps with the launchers, or with the applications menu, which you can get by right clicking on the desktop.  You will have to remember to run updates on your own without the tray applet.

This takes a little bit to adjust to, but is actually well suited to a living-room htpc setup.  The panel is too small to see clearly from across the room, and keeping apps maximized and alt-tabbing  makes the most of what is in effect a small screen because you are sitting across the room.  I also run my gui at 720p, and then have it switch into 1080p for playback.  This makes other apps more readable, since I usually don't use them while watching tv.  Watching TV, by the way, is the one thing over-scan doesn't hurt.  You never miss those edges.  I have read in other forums that tv is intended to be slightly over-scanned, and this is why over-scan can't be corrected on tv's which weren't made to be used with a computer.

---

### Post by myth_cougar on 2010-01-25
LG sets have a setting to turn off the overscan.  I don't recall where it is in the menus at the moment and I'm not near the set to check it.  But I did it with mine and see the full desktop.

Next time I'm near the tv I will find the setting, but it is there.

---

### Post by TheMiz on 2010-01-26
Which NVidia drivers are you using?
The 190.43 drivers have an overscan correction feature.  I think the drivers that come after this also have the correct overscan option in the Nvidia control panel (I believe I have 190.53 installed).

I leave mine overscanned because it prevents those flashing lines at the edges of the picture, but I will correct it if I need to be doing alot of desktop work.

---

### Post by SiHa on 2010-01-27
> **TheMiz said:**
> Which NVidia drivers are you using?
The 190.43 drivers have an overscan correction feature.  I think the drivers that come after this also have the correct overscan option in the Nvidia control panel (I believe I have 190.53 installed).

I leave mine overscanned because it prevents those flashing lines at the edges of the picture, but I will correct it if I need to be doing alot of desktop work.

For VGA (DVI/HDMI/VGA) out? 

In the past this has only been available for TV-Out (S-Vid, Composite). It would certainly be a big leap forward if this was available for all outputs. Might even be worth risking upgrading from 185...

---

### Post by TheMiz on 2010-01-27
Yeah, I am running my system on an Nvidia ION motherboard with integrated GeForce 9400 with HDMI out to a 26inch Sharp Aquos HDTV.

I believe I have 190.53 installed, but I had to do some fiddling around with installing/uninstalling the other drivers to get the overscan correction option.  It is currently present in my NVIDIA control panel.

---

### Post by SiHa on 2010-01-27
Nice... Thanks.

---

### Post by jquintana on 2010-01-27
> **TheMiz said:**
> I believe I have 190.53 installed
Sorry for the stupid question, but where do I get these drivers? I am running a different version and would like to upgrade. 

I have a 9400GT so I think I can use the same drivers you have, correct?

---

### Post by TheMiz on 2010-01-27
You can go to the Nvidia website to get the drivers.  That site lists all the supported product (of which 9400 GT is one)

Follow these directions:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by jquintana on 2010-01-27
> **TheMiz said:**
> You can go to the Nvidia website to get the drivers.  That site lists all the supported product (of which 9400 GT is one)

Follow these directions:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)Thanks. I just downloaded and installed the driver as per the thread you linked me to.

However, after I rebooted I dont see the nvidia control center like I used to. Also, if I go to the hardware drivers section, I only see 173 and 185.

How can I confirm that I am using the new driver?

---

### Post by jquintana on 2010-01-27
By the way, I installed this using putty. I am trying to install once more using sudo sh ./Nxxx.run 

If I get the same results, I will try to run from the actual computer instead of through putty.

---

### Post by TheMiz on 2010-01-27
On my system, this:

```
grep -i "x driver" /var/log/Xorg.0.log

```

I get this as an output:

> (II) NVIDIA dlloader X Driver  190.53  Wed Dec  9 15:39:50 PST 2009

You should be able to see it from the Nvidia display panel 
```
gksu nvidia-settings
```

but I can't check that because I'm at work and I don't have VNC setup yet (only putty).

---

### Post by jquintana on 2010-01-27
I found the nvidia-settings under Mythbuntu Control Center and verified the 190 driver was installed. I ran nvidia-settings from the command line and it launched correctly. It is only missing from the settings menu but I can live without it if this fixes my problem.

Thanks!

---

