---
title: "xrandr: difficulty setting up multiple desktops"
date: 2008-12-22
forum: Multimedia Software
---

### Post by chardish on 2008-12-22
Hi,

I'm having difficulty setting up multiple desktops on two monitors under Hardy. Currently, both monitors are on and active but displaying the same thing. After a lot of googling, trying to edit my xorg.conf, etc., I came to the conclusion that the way I should do multiple desktops with my particular video card (Radeon RV100 QY [7000/VE]) is via xrandr.

I know that to enable multiple desktops you need to add a "Virtual" line to the Screen's Display subsection. I did this, and there's no change in my results.

```

me@mymachine:~$ xrandr --output DVI-1 --right-of DVI-0
xrandr: screen cannot be larger than 1280x1024 (desired size 2560x1024)
```

I've restarted X with this xorg.conf; it loads fine. But it seems to be ignoring the "Virtual" line I added in. Line 566 of the Xorg.0.log file is a dead giveaway that something's not right:

```

# (II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
# (II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf

```

Anyone know what's going on?

Here's my xorg.conf: [http://pastebin.com/f4e7909f6](http://pastebin.com/f4e7909f6)
Here's my Xorg.0.log: [http://pastebin.com/f12323b6f](http://pastebin.com/f12323b6f)

Cheers,
chardish

EDIT: Here's the output of my xrandr -q:
```

evanj@cherokee:/var/log$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1024
DVI-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   59.9  
   1280x1024@60   60.0  
   1280x960@60    60.0  
   1024x768@60    60.0  
   1024x768       60.0  
   800x600@60     60.3  
   800x600        60.3  
   800x600@56     56.2  
   640x480@60     60.0  
   640x480        60.0  
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```

---

### Post by prshah on 2008-12-22
> **chardish said:**
> 
I've restarted X with this xorg.conf; it loads fine. But it seems to be ignoring the "Virtual" line I added in. 

Can we have a look at your xorg.conf? Probably the line's not in the right place.

---

### Post by chardish on 2008-12-22
> **prshah said:**
> Can we have a look at your xorg.conf? Probably the line's not in the right place.

Sure, it's linked here: [http://pastebin.com/f4e7909f6](http://pastebin.com/f4e7909f6)

---

### Post by chardish on 2008-12-22
Inexplicably, it started working now, after rebooting the machine. I don't know why it wouldn't work when I restarted X (ctrl+alt+bksp), but it worked after rebooting.

---

