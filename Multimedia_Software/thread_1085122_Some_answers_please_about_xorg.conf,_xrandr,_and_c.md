---
title: "Some answers please about xorg.conf, xrandr, and compiz"
date: 2009-03-02
forum: Multimedia Software
---

### Post by Daremo_06 on 2009-03-02
I am running Intrepid with a ATI 200 Pro card (RV280).  I have dual monitors connected and they are working currently, but there are things that dont seem right.

1st off.  This is my Xorg.conf file.  From everything that I have read, this doesnt seem right.

> Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Virtual 2880 1024
EndSubSection
EndSection 

I am running Xrandr and its set to

> Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2880 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     60.0     60.0* 
   1600x1024      60.2  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
DVI-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 432mm x 324mm
   1600x1024      60.2  
   1280x1024      75.0     60.0*    60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)


I have been reading the following links..

[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)
[http://wiki.x.org/wiki/Projects/XRandR](http://wiki.x.org/wiki/Projects/XRandR)
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

And I am lost at this point.  I am so tired of reading this stuff that I am seriously considering just dumping ubuntu and going back to xp even as annoying as windows is.  I do enough learning new things at work, having to re-create the wheel at home when i get here is just too much.  (at least thats what it feels like...)  So I'm rather frustrated... I know this is a fairly common video card, because of all the issues with the flgr drivers not working ect ect, so it cant be that hard.  I thought with the newer versions of ubuntu most of this heavy lifting as far as configurations was done for you?

Issues I am having.

1.  I try to start compiz by going to Preferences/appearance/visual effects and select Extra to start compiz and I get a message saying that "desktop effects could not be enabled".  So I am not sure whats causing that, but I am thinking its because I probably dont have all of my video driver setup correctly.  

Here is what I get when I run compiz from terminal

> rob@rob2:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 


2.  My DVI screen is "jumping" slightly every few minutes.  Its barely noticable at 1st, but if your typing, its almost as if your in a car and you hit a slight bump.

3.  Whats a good tool to verify I do have my video setup correctly?  I know glxgears is not a good benchmark, so what is?  Speaking of glxgears, I get 650 fps consistantly, but from what I have read, that really doesnt mean anything.

So if I could get some assistance with assuring my vid config is correct, that would be awesome.  I can post other config files if need be as well.

Thanks,

Rob

---

### Post by Sam Lars on 2009-04-10
From your output from starting Compiz, it looks like your video card will not support a screen that size with Compiz running.

---

