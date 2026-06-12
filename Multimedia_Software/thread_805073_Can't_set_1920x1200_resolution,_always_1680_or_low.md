---
title: "Can't set 1920x1200 resolution, always 1680 or lower"
date: 2008-05-23
forum: Multimedia Software
---

### Post by geoff123 on 2008-05-23
Hello, 
I just got a new Samsung SyncMaster 245BW monitor and can't use it's native resolution (1920x1200).  No matter what I do I end up with 1680x1050 or lower.  

I've tried 2 video cards the internal intel 915 and nvidia 6600GT.  I believe both are capable of these resolutions.  

I've tried several other things also like nvidia-xconfig, dpkg-reconfigure.., tried some of my own settings in the xorg.conf with no luck.  I also looked at the Windows .inf file and it clearly shows 1920x1200 also. 

Currently it defaults to:
xvidtune --show
"1680x1050"   119.00   1680 1728 1760 1840   1050 1053 1059 1080 +hsync -vsync


when I do this:
sudo xresprobe nvidia   

THE OUTPUT IS:
id: SyncMaster
res: 1680x1680 1680x1050 1280x1024 1280x960 1152x864 1024x768 832x624 800x600 720x400 640x480
freq: 30-81 56-75
disptype: 

Why can't I get the 1920x1600 resolution??

Thanks, Geoff

---

### Post by Ubuginer on 2008-05-23
> **geoff123 said:**
> Hello, 
I just got a new Samsung SyncMaster 245BW monitor and can't use it's native resolution (1920x1200).  No matter what I do I end up with 1680x1050 or lower.  

I've tried 2 video cards the internal intel 915 and nvidia 6600GT.  I believe both are capable of these resolutions.  

I've tried several other things also like nvidia-xconfig, dpkg-reconfigure.., tried some of my own settings in the xorg.conf with no luck.  I also looked at the Windows .inf file and it clearly shows 1920x1200 also. 

Currently it defaults to:
xvidtune --show
"1680x1050"   119.00   1680 1728 1760 1840   1050 1053 1059 1080 +hsync -vsync


when I do this:
sudo xresprobe nvidia   

THE OUTPUT IS:
id: SyncMaster
res: 1680x1680 1680x1050 1280x1024 1280x960 1152x864 1024x768 832x624 800x600 720x400 640x480
freq: 30-81 56-75
disptype: 

Why can't I get the 1920x1600 resolution??

Thanks, Geoff

Did you try using screen and graphics to set the resolution?

---

### Post by geoff123 on 2008-05-23
I did try using gnome's System > Preferences > Screen Resolution
When I tried it with nvidia I used nvidia-settings.
I attached a screenshot showing the config dialog; note that the highest setting available was the 1680.  Also, the monitor says 21", but it is a 24".

---

### Post by geoff123 on 2008-05-23
Okay - I'm replying to myself again, but here's some more info someone might find useful.  This is the output of xrandr and it incorrectly shows nothing about 1920x1200???

xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA connected 1680x1050+0+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+   60.0  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1

---

### Post by Ubuginer on 2008-05-23
> **geoff123 said:**
> Okay - I'm replying to myself again, but here's some more info someone might find useful.  This is the output of xrandr and it incorrectly shows nothing about 1920x1200???

xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA connected 1680x1050+0+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+   60.0  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1

The screen and graphics will allow you to select the video card and the monitor.  That's what I used to fix mine when it's stuck at 800x600.

---

### Post by geoff123 on 2008-05-25
Got it solved.  Check out here:
[http://ubuntuforums.org/showthread.php?p=5043089#post5043089](http://ubuntuforums.org/showthread.php?p=5043089#post5043089)

---

