---
title: "Hdmi"
date: 2012-08-22
forum: Multimedia Software
---

### Post by Random20210831 on 2012-08-22
I own the SONY AV Receiver STR-DG720 with HQ sound. To connect laptop to it I use HDMI. But there was a problem. When I connect it with HDMI laptop screen on the laptop is switched to 640x480 instead of 1280x800 because cloning screens. I do not know how to handle this. In the display settings can not scroll, so I can not solve the problem.

---

### Post by cortman on 2012-08-22
Please wait 24 hours before bumping your thread.

Post the output of

```
xrandr
```

And I'll give you a quick easy fix that SHOULD work.

---

### Post by Random20210831 on 2012-08-23
How to post output? xrandr only displays information about screens.

---

### Post by cortman on 2012-08-23
> **ZDroid said:**
> How to post output? xrandr only displays information about screens.

That is the information I am asking for.
Copy/paste it into your reply.
Are you really asking for support or just playing games?

---

### Post by Random20210831 on 2012-08-23
I apologize. I did not understand you correctly.
That are the terminal log:
[FONT="Courier New"]Screen 0: minimum 320 x 200, current 640 x 480, maximum 8192 x 8192
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9* 
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 640x480+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1280x720       60.0 +
   720x576        50.0  
   720x480        59.9  
   640x480        60.0* 
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)[/FONT]. 
Note: my laptop supports HDMI transfer in Full HD, but I am using HDMI for HD audio transfer to my AV reciever.

---

### Post by cortman on 2012-08-23
> **ZDroid said:**
> I apologize. I did not understand you correctly.
That are the terminal log:
[FONT="Courier New"]Screen 0: minimum 320 x 200, current 640 x 480, maximum 8192 x 8192
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9* 
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 640x480+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1280x720       60.0 +
   720x576        50.0  
   720x480        59.9  
   640x480        60.0* 
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)[/FONT]. 
Note: my laptop supports HDMI transfer in Full HD, but I am using HDMI for HD audio transfer to my AV reciever.

OK, sounds good.
Just a tip- when you post code, put it between ```
 blocks- you can get them from the editing toolbar in the response window.

Go ahead and run

[CODE]xrandr --output LVDS1 --mode 1280x800
```

in a terminal. That should fix the resolution.

---

### Post by Random20210831 on 2012-08-23
This improved the problem of the resolution and now I can play the HQ audio. Thanks!

---

### Post by cortman on 2012-08-23
> **ZDroid said:**
> This improved the problem of the resolution and now I can play the HQ audio. Thanks!

You're welcome! :)

Please mark the thread [SOLVED] using the thread tools in the upper right.
Good luck!

---

