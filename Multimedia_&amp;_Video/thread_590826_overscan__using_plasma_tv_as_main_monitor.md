---
title: "overscan : using plasma tv as main monitor"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by hobophobe on 2007-10-25
hello

I am trying to use a dell gx620 with a ATI radeon X600 256 as a media center for my living room running a fresh copy of Ubuntu.

It is connected to a panasonic plasma and so far it is really the makings of a damn sweet set up.  

My problem now is that "overscan" seems to be on so all the Ubuntu menus are just off the screen.

I am new to Ubuntu.  Is there somewhere this can be set?  Has anyone had this issue come up?  Would the ATI driver instead of the default driver perhaps fix this?

thanks

---

### Post by yopnono on 2007-10-25
Resolution of screen and computer?
What is the native resolution of the plasma 800x600?

---

### Post by hobophobe on 2007-10-26
hi, thanks for responding.

The screen is a Panasonic TH-50PX75U.   Ideally I would run the computer at 1366 x768 with the ability to turn overscan off.

thanks

---

### Post by yopnono on 2007-10-26
ok the plasma support up to 1366x768, however it does not mean that the PC VGA in support it on the screen.
Are you connection using PC VGA connection or HDMI.

Also what is the reso on the computer?
Run this in the terminal  " xrandr "

---

### Post by hobophobe on 2007-10-27
On first install the computer only had 1024x768.  I have since installed the ATI driver which now allows me to do 640x480, 800x600, and 1024x768 and also turned off overscan so I can now see my menus.


xrandr says:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0*
   800x600        60.0     56.0     47.0
   640x480        60.0
   720x480        60.0
   640x400        60.0
   512x384        60.0
   400x300        60.0
   320x240        60.0
   320x200        60.0


When in XP the card can go up to 1600x1200 when using DVI.

When I first installed Ubuntu, I had that machine connected to a crappy old monitor that could only go up to 1024x768.  Is there any chance that I need to define what type of monitor/tv this?

thanks

---

### Post by yopnono on 2007-10-27
And what does the plasma use for resolution?Have you checked that. Still are you connection using the PC input or HDMI input

---

### Post by hobophobe on 2007-10-27
The plasma tv's specs are as follows:

50 screen; Progressive Scan
1366x768 (720p) native resolution
16 - 9 Widescreen aspect ratio
Pixel Pitch (H x V) - 0.81 x 0.81 mm
Contrast Ratio - Up to 10,000 - 1


The Radeon x600 is going out DVI.

thanks

---

### Post by nixxofugi on 2008-02-08
has this been resolved??? i need the same help :confused:

---

### Post by jyoti_ranjan_pani on 2008-02-08
Same here...i am also facing the same problem.

Changing the display modes didn't help.  :(

---

