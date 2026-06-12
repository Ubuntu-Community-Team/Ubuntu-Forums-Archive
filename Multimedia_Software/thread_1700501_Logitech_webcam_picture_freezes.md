---
title: "Logitech webcam picture freezes"
date: 2011-03-05
forum: Multimedia Software
---

### Post by furrypotato on 2011-03-05
Hi All,
           I've tried this with 2 different logitech webcams, and the same thing happens with both. 

It works fine or a minute or two, but then the picture freezes.
Using Skype, Cheese or flash based ustream.

THey are both HD Logitech webcams and give me a great image until they freeze.

---

### Post by no2498 on 2011-03-05
this comes from the cheese help FAQ'S


The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by furrypotato on 2011-03-09
Thanks for the info.

I tried it but no luck. Still freezes.

Is there any kind of log etc I can check for to see what happens ?

---

### Post by no2498 on 2011-03-09
open cheese the help files FAQ's look at 6.6 ?

cheese has a way to get a log 
but i forget how

---

### Post by furrypotato on 2011-03-11
I may have fixed it thanks to your earlier advice.

From gstreamer options, I changed Video Input from vl2 to vl  and it seems to be working ok now.

Plus I've learned a bit more. After 14 years on Windows, I've still got plenty to learn now that I've switched to Ubuntu only :)

Thanks

---

