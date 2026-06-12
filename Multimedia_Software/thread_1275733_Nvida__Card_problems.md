---
title: "Nvida  Card problems"
date: 2009-09-26
forum: Multimedia Software
---

### Post by gordo52 on 2009-09-26
I have tried a few searches not really knowing what to put, so never found any help,I am on a first install of Ubuntu 9.04  I have an nvidia GForce2 400mx installed with the Ver 96 drivers installed. 

Yesterday I had a choice of resolutions to pick from, I restart today to play a little more and I have only two  640X 480 and 320 X 240.   Both of which are just about impossible to work with.

Being a complete idiot with ubuntu is there something I have overlooked ?   If any commands can you please list, so I can jot them down for my records for help

---

### Post by Merovius on 2009-09-26
[http://www.ubuntux.org/ubuntu-8-04-screen-resolution-limited-with-nvidia-geforce2-mx-400](http://www.ubuntux.org/ubuntu-8-04-screen-resolution-limited-with-nvidia-geforce2-mx-400)

This site looked like it had some good ideas. I personally would check the last one, about the monitor be identified correctly.

I looked at my setup and my monitor is identified correctly. 

I have used EnvyNG and it worked at the time. Might want to give it a try.

---

### Post by gordo52 on 2009-09-26
thanks had a read and tried using terminal > **gksu displayconfig-gtk**

 and nothing happens[B] [B]no selection window or anything appears. Why this has gone to bold I have no idea
[/B]
[/B]

---

### Post by Zimmer on 2009-09-26
Read the xorg.log and look for warnings or errors, see which config file is used, which drivers are being used and if the monitor is being detected.

---

### Post by Merovius on 2009-09-27
I did a quick search and gksu displayconfig-gtk was dropped from Jaunty. :confused:

I will do some more looking around and see what I can find.

---

### Post by Merovius on 2009-09-27
[http://ubuntuforums.org/showthread.php?t=1251477&highlight=set+correct+display+jaunty](http://ubuntuforums.org/showthread.php?t=1251477&highlight=set+correct+display+jaunty)

I would read the above thread and try to contact "inobe" directly. He seems pretty willing to help with video issues.

---

### Post by Merovius on 2009-09-27
Just curious,

When you go to Preferences, Display are you prompted to use the "vendors tool" ?

If so you should choose "yes" and when the NVIDIA X server settings manager comes up go to "X server display configuration" 

Is "Resolution" set to auto? 

Is your monitor identified correctly?

If they are (or you set them) then save them to the  X configuration file by clicking the button.

---

