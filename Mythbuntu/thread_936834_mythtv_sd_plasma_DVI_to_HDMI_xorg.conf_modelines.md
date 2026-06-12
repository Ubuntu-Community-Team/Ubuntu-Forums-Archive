---
title: "mythtv sd plasma DVI to HDMI xorg.conf modelines"
date: 2008-10-03
forum: Mythbuntu
---

### Post by oobe-feisty on 2008-10-03
Hi i have recently endevered to build a remote frontend for a sd plasma tv 

here is the specifications its a panasonic th-42pa60a

with native resolution of 852x480 at 50hz or 60hz from av inputs i think hdmi is not included as a av input ? ( is that correct)


here are some modelines in considering trying that i found around on the net

ModeLine     "852x480" 33.1 852 872 912 1068 480 483 488 516 -hsync vsync

Modeline "852x480" 33.07 852 872 912 1068 480 483 488 516 -hsync -vsync
# and last generated here [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) using the manual specs
Modeline "848x480@50" 25.47 848 880 976 1008 480 490 494 505



my questions are 


1. although im putting in as much effort to correctly configure xorg.conf as possible is it possible in anyway to damage the panasonic sd plasma if i make a mistake?

2. what happens if my card does not support 852 x 480 will it default to the next closest resolution or will i need to make a new modelins specifically for the resolution it does support?

3.  it says in the manual native resolution of 852x480 at 50hz or 60hz from av inputs i think hdmi is not included as a av input ? does this mean i can only have 50hz with hdmi


hopefully there are people out there with similar setups that can help me looking forward to hearing some reply's.

---

### Post by oobe-feisty on 2008-10-03
so no one knows anything about my questions

---

### Post by SiHa on 2008-10-03
I'll start from the bottom...

3) AV generally refers to any external video source. HDMI is included in that, so yes you should be able to get 60Hz on the HDMI.

2) The card will attempt to drive your TV at the resolution defined in the modeline and it's corresponding mode statement in xorg.conf. But it wil only do this if it has satisfied itself via EDID that the modeline is valid. You can tell it to ignore EDID though, at your own risk  - you could damage the TV if you try and drive it outside it's spec.

1) xoorg will usually do its best to stop you doing anything stupid, but you can override it - sometimes you need to. In which case yes, you can do damage.

If you're just trying out different modelines though, you shouldn't do any harm. 

I stumbled across this HOWTO earlier this week when I was having a few problems. 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

I got the answers I needed from there.

---

### Post by oobe-feisty on 2008-10-03
thanks heaps for you reply i will let you know how i go 

btw im using a nvidia fx5200 i chose it cause i wanted to try xvmc color osd but im thinking i probably would of been better off with a 6200

> **SiHa said:**
> I'll start from the bottom...

3) AV generally refers to any external video source. HDMI is included in that, so yes you should be able to get 60Hz on the HDMI.

2) The card will attempt to drive your TV at the resolution defined in the modeline and it's corresponding mode statement in xorg.conf. But it wil only do this if it has satisfied itself via EDID that the modeline is valid. You can tell it to ignore EDID though, at your own risk  - you could damage the TV if you try and drive it outside it's spec.

1) xoorg will usually do its best to stop you doing anything stupid, but you can override it - sometimes you need to. In which case yes, you can do damage.

If you're just trying out different modelines though, you shouldn't do any harm. 

I stumbled across this HOWTO earlier this week when I was having a few problems. 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

I got the answers I needed from there.

---

### Post by oobe-feisty on 2008-10-06
UPDATE: 

i went and tried it it worked perfectly first time modelines were unecessary the video fit the screen perfectly but i had to resize the menu and uncheck resize video with it from setup/utility's appearance 

then i went to the little app in setup / utilitys that you manually move the triangle on both corners this took a while as at first i didnt uncheck the thing and i couldnt get it to fit but once i was familar with the software it was easy hope this help's someone

---

