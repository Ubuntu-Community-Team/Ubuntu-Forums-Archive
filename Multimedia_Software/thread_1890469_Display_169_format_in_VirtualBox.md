---
title: "Display 16:9 format in VirtualBox"
date: 2011-12-03
forum: Multimedia Software
---

### Post by BradleyAtkins on 2011-12-03
Hi

I'm running ubuntu in virtualbox on a 16:9 monitor via a hdmi port on my laptop.

The max resolution I have in my monitors section of the system settings is - 1600 x 1200 (4:3).

I don't have any 16:9 formats listed.

So I'm not getting the benefit of the full width of the monitor.

Can anyone point me in the right direction to get a 16:9 format added to the list at a good resolution?

Thanks

Brad

PS

In anticipation of being asked: -

/home/brad >sudo xrandr -q
[sudo] password for brad: 
Screen 0: minimum 64 x 64, current 1600 x 1200, maximum 32000 x 32000
VBOX0 connected 1600x1200+0+0 0mm x 0mm
   1024x768       60.0 +   60.0  
   1600x1200      60.0* 
   1440x1050      60.0  
   1280x960       60.0  
   800x600        60.0  
   640x480        60.0

PPS 

I'm running Ubuntu 11.10

---

### Post by bluexrider on 2011-12-03
seems a solution 

VirtualBox global configuration setting:     VBoxManage setextradata global GUI/MaxGuestResolution any


ref [http://humanreadable.nfshost.com/journal/2009/2009-035.htm](http://humanreadable.nfshost.com/journal/2009/2009-035.htm)

---

### Post by BradleyAtkins on 2011-12-04
Hi Bluexrider

Thanks for that.

Doesn't seem to help though, he was running windows VM's on a Linux host I think. I'm running Ubuntu 11.10 within a VM running on Win7.

I don't seem to have an xorg.conf file and don't know what has replaced it in this version of ubuntu.

Thanks anyway

---

### Post by BradleyAtkins on 2011-12-05
Okay well I have made some progress with this.

Basically running these commands on the command line sets the monitor to use almost all of the screen estate: -

```
xrandr --newmode "1920x1016_60.00"  161.75  1920 2040 2240 2560  1016 1019 1029 1054 -hsync +vsync
xrandr --addmode VBOX0 1920x1016_60.00
xrandr --output VBOX0 --mode 1920x1016_60.00

```

My problem now is how to make the changes permanent?? When I log out I need to run these commands again to set the screen to what I want.

Can anyone tell me the best file to put these in?

Do I need to identify a config file for the display or can I just put them in my profile or something?

---

### Post by BradleyAtkins on 2011-12-07
Well it looks like all I had to do was download the additional video drivers: -

```
jockey-gtk
```

I now have a 16:9 desktop that fills the monitor perfectly.

---

