---
title: "ATI laptop with cloned external monitor of different resolution"
date: 2009-02-27
forum: Multimedia Software
---

### Post by surfdoc on 2009-02-27
I've become an xorg.conf victim. I've been trying to fix this for the last 12 hours!

I have a laptop (ASUS F5) with a ATI Technologies Inc Mobility Radeon HD 3400 Series. It has a DVI output on the back. I'm running kubuntu intrepid.

The laptop display is 1280x800 and I have plugged in an external TFT that can do 1280x1024.

I would like to have the "normal" external behaviour where the external monitor clones the laptop display. 

The default behaviour is for the external monitor to clone the laptop, but it shows the screen stretched from 1280x800 to 1280x1024.

This is to be expected, however I would like to be able to switch to the external display only (preferably using Fn+F8) at 1280x1024.

It looked like xrandr would provide the solution, but after hours of trying, i can't get xrandr -q to show my external monitor. I read that fglrx doesn't work with xrandr?

I have managed to get xinerama to work dual head with both monitors using their max resolutions. In xorg.conf, using the "Relative" screen option in ServerLayout, I am able to overlap the two displays so that they show the same view (although the lower section is croped of on the laptop as you would expect). The problem with all of this is that when I unplug the external monitor and restart, xorg won't start at all. I've seen solutions using two ServerLayout section and switching between them using startx, but I can't see how to automate this depending on whether the external monitor is pluged in.

Does anyone have any ideas that might help me?

Cheers

---

### Post by surfdoc on 2009-02-27
Ahhhh - It came to me 60 secs after posting

By setting a virtual screen resolution of 1280x1024 I get the external monitor at max resolution (the laptop shows a cropped section of the virtual desktop). However, although xrandr still doesn't show the second monitor, it now shows options for both 1280x1024 and 1280x800. I can easily switch between them using xrandr -s.

The only problem is that I only get the 1280x1024 option if I set the virtual screen to that size, but I would prefer to default to 1280x800. Maybe I can run xrandr somewhere in /etc/init.d/kdm? I can write a script to switch using Fn+F8 easy enough.

---

### Post by surfdoc on 2009-02-27
And now, I think I have it!

I started with a clean xorg.conf, then ran

sudo aticonfig --desktop-setup=clone

then

sudo aticonfig --mode2=1280x1024

This gave me the external monitor at max res and the laptop screen cropping the desktop down. 

The best bit is

sudo aticonfig --query-monitor

showed

lvds tmds1

I could then enable any combination of the two monitors using 

sudo aticonfig --enable-monitor=

However, after running this last command, the resolution stayed down at 1280x800 regardless, but I could still change it with xrandr -s. 

So... I should be able to write a script that uses the two commands to switch between the various options

phew

---

