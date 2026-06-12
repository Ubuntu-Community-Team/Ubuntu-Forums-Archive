---
title: "3 screens"
date: 2013-05-23
forum: Multimedia Software
---

### Post by antrock101 on 2013-05-23
Hi,

I have 2 gfx cards (geforce 260 gtx and amd 5450) they feed 3 monitors. However in ubuntu i can get this to work it only shows 2 screens. If I load the restricted drivers for either card it will display on that screen only. I also have an issue where if I use multiple screens on the top menu bar each screen has a duplicate of the indicators (system tray) how do I do this so it is on the primary screen only?

---

### Post by dino99 on 2013-05-23
such issue is often due to the hardware used, and their limitations: hdmi, dvi, cord

---

### Post by antrock101 on 2013-05-23
> **dino99 said:**
> such issue is often due to the hardware used, and their limitations: hdmi, dvi, cord

This works 100% with Windows XP,7 and 8

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Multimedia & Video**.*

Have no idea why this was in ***Absolute Beginners*** sub-forum. Please try and post in the appropriate sub-forum. Posting in the inappropriate ones won't get you help any faster, generally just the opposite. Thanks. ;)

---

### Post by antrock101 on 2013-05-23
Sorry, I'm fairly new :D and thought this would be an easy fix, the task bar thing especially

---

### Post by antrock101 on 2013-05-23
Anyone able to comment on either of these issues?

---

### Post by Bucky Ball on 2013-05-23
> **antrock101 said:**
> Anyone able to comment on either of these issues?

If they were they would. Please wait 24 hours before bumping threads. Thanks.

---

### Post by Mark Phelps on 2013-05-23
Would help if you told us which version of Ubuntu you're using.

---

### Post by antrock101 on 2013-05-23
> **Mark Phelps said:**
> Would help if you told us which version of Ubuntu you're using.

I've tried on 12.04 to 13.04 both issues

---

### Post by antrock101 on 2013-05-24
Just installed opensource drivers. Same problem

---

### Post by antrock101 on 2013-05-25
anyone?

---

### Post by Gogeden on 2013-06-06
I'm experiencing this as well. I have one monitor using VGA, another using DVI, and the largest using HDMI and I can only get two monitors to work at the same time. I'm using 13.04 and this also happens in Mint 15 with or without the proprietary drivers.

---

### Post by Gogeden on 2013-06-06
Here's my output of xrandr -q: 


```
Screen 0: minimum 8 x 8, current 2880 x 900, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 257mm
   1440x900       60.1*+   75.0  
   1400x1050      74.9     60.0  
   1280x1024      75.0  
   1280x960       60.0  
   1280x800       74.9  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        75.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-I-1 connected 1440x900+1440+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
HDMI-0 connected (normal left inverted right x axis y axis)
   1280x720       60.0 +   59.9     50.0  
   1920x1080      60.0     59.9     50.0     30.0     25.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0     25.0  
   720x480        59.9  
   640x480        75.0     72.8     59.9     59.9  

```

---

### Post by Gogeden on 2013-06-06
And here's the error message I receieve when I try to turn the third screen on in the "Display" menu (As an attachment)

---

