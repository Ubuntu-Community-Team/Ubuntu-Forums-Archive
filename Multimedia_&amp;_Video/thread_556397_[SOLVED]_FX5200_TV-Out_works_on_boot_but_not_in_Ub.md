---
title: "[SOLVED] FX5200 TV-Out works on boot but not in Ubuntu"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by middlewordie on 2007-09-21
I have a Nvidia Fx5200 graphics card with TV Out and a monitor and TV connected to this card. The PC has Feisty clean installed.

However, although both monitor and TV display the same things (boot screens etc) when booting, as soon as the login screen comes up on the monitor, the TV screen goes blank.

I've installed MythTV and the proprietary NVidia drivers using Envy. MythTV has been set up, but as soon as I try to watch TV (on the monitor), the window it runs in goes blank. I thought it was my ATI card previously, so bought the FX5200 which I know works with MythTV.

I've had a few attempts at configuring the Xorg.conf file, but with no success.

Why doesn't the TV carry on showing the display when Ubuntu starts?

---

### Post by MrHippocampus on 2007-09-21
If you havent already, try looking through the instructions in [this]("http://ubuntuforums.org/showthread.php?t=98456") post, if it still doesn't work post your xorg.conf along with exactly what your trying to achieve (e.g. clone monitor display to TV using s-video cable with NTSC).

---

### Post by middlewordie on 2007-09-21
I have tried this guide - several (tens of!) times on Wednesday night - and it invariably ended with me having to reboot in recovery mode and sudo dpkg-reconfigure xserver-xorg 

I'll post the Xorg.conf when I get home tonight - it's likely to be a user error but I'm not too hot on syntax checking after ten attempts!

The PC will  become a Myth TV box, but I would also like to be able to use it as my main internet PC. I would ideally like my monitor and TV to allow both concurrently, but TV is my priority as I have other PCs that can connect to the net. I'm in the UK, which I think means my TV will be PAL-I. I'm connecting using the SVIDEO output on the graphics card.

---

### Post by middlewordie on 2007-09-23
Been away for a couple of days and just booted up and lo, PC now displays via SVIDEO cable onto TV. A miracle, but I'm not sure why!

All good, except that the monitor is now not getting a signal.

Xorg conf. attached

---

### Post by middlewordie on 2007-09-23
Hooray.

Uninstalled Nvidia drivers using Envy. Re installed NVidia Drivers using Envy.

Used Applications-System Tools-Nvidia Settings to set up TwinView enabling TV-Out and Monitor on the same resolution as Clones:

Select X Server Display Configuration

Click on the Monitor outline and you can move it about. Move it to the right until TV outline is visible.

Click on TV and set:
- Configure to Twin Screen.
- Resolution to Auto.
- Position to Absolute

Click on Monitor and set 
- Configure to Twin Screen.
- Resolution to 1024x768 (or whatever suits you best)

Move Monitor back over TV until they completely overlap.

Click Save to X Configuration file and it tells you it can't - you need to be logged in as Root.

Log in as Root (I know this is not a great way to do things but works).

Used Applications-System Tools-Nvidia Settings to set up TwinView enabling TV-Out and Monitor as above. Save and it works.

Restart and you have twin view, both 1024x768, on Monitor and TV.

---

