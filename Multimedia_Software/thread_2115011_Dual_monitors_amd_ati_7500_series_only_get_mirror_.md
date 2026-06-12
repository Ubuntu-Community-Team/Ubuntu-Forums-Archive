---
title: "Dual monitors amd ati 7500 series only get mirror image"
date: 2013-02-11
forum: Multimedia Software
---

### Post by claven123 on 2013-02-11
Ubuntu 12.10 dual boot win 8.  AMD 7500 graphics card.


So, I have the correct cables and I now can see mirror on both monitors!

I am unable to get dual monitors to work outside of mirror.  I get the error


required virtual size does not fit available size: requested[B].....  

[/B]I have attempted to choose almost every combination allowed and  nothing works.  I have been reading and there are several solutions, but  seem quite complicated.  I was hoping something simple would work and  wondered if there were any solutions. Such as making changes to the  xorg.conf file.  I heard you can change the size resolution and this  would fix the issue, but I don't remember how to to do that.

Thanks,

D

---

### Post by Habermas on 2013-02-11
I had the same issue, I wanted my second monitor to behave as an extended desktop instead of behaving as a clone. I found a nice solution, there is an application called "arandr", I think it is in the standard repositiories so just type sudo apt-get install arandr.

---

### Post by claven123 on 2013-02-12
So, I installed and I have NO idea how to get it to do what I want.  I've searched and played with a bunch of the settings but I have no idea.

I see lots of information on the terminal interation, but I have the visual gui and I see nothing about dual monitors.  I see both monitors, but still in mirror format.  I can change resolution of them that is all.


Thanks,

D

---

### Post by Habermas on 2013-02-12
The arandr application is very simple, you just need to "drag and drop" the boxes that represent your monitors and arrange them in a way you want them to behave. 

For example I have my secondary monitor on top and my primary on bottom. So the mouse pointer jumps to my secondary monitor every time I go up on my primary monitor. To get it work neatly you have to set up similar resolutions on both your monitors. I have 1024x600 on primary and 1024x768 on my secondary. Since the width matches on both of my monitors if I arrange them vertically they work good in the extended desktop mode. 

Once you configure the layout by "drag and dropping" set the resolution under the "Outputs" tab and click the green checkbox for the changes to take effect.

I've attached a screenshot for you:
[http://s3.postimage.org/fkb70ot0j/2013_02_12_133428_1024x1456_scrot.png](http://s3.postimage.org/fkb70ot0j/2013_02_12_133428_1024x1456_scrot.png)

---

### Post by claven123 on 2013-02-12
I don't get that much room to work and or move the screen 'icons' as seen in the screen shot.

Thanks, for the help though


D

---

