---
title: "yet even another dual monitor question"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by bz3 on 2007-10-24
ok trying to get my dual monitors working in ubuntu 7.10 
on a dell optiplex 745 dual dell 1907fp lcd's
xrandr only shows 1 screen.. i have no problem getting cloned screens but trying to get an expanded desktop seems impossible.. help?? 

~$ xrandr -q
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      75.0* 
   1024x768       75.0  
   800x600        56.0  
   640x480        60.0  
   848x480        75.0  


~$ lspci |grep Graphics
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

---

### Post by buckwheat12n on 2007-10-24
Just curious on how you got the cloned screen setup going?  I can't seem to get mine working correctly.  I have a Dell Inspiron 1501 that runs at 1280x800 and a LCD that runs at 1280x1024.  The dell has has ATI Mobility X1150 onboard video card.

---

### Post by sloggerkhan on 2007-10-24
xrandr wouldn't work correctly for me, either, so I just used an manually modified version of my old xorg.conf.

---

