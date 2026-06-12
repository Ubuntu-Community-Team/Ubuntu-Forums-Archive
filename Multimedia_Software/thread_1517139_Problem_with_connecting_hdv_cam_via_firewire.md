---
title: "Problem with connecting hdv cam via firewire"
date: 2010-06-24
forum: Multimedia Software
---

### Post by vifillr on 2010-06-24
Hi

I have a Sony HDV Handycam HDR-HC3 1080i camera using miniDV-cassettes, which I am trying to connect to my Dell laptop via firewire. 

The laptop is a dual boot with windows xp, and on windows I can connect the camera and transfer the data on the cassettes to the harddisk. However, with windows moviemaker the maximum resolution I can save to is 720 x ?? pixels. 

I believe that a higher resolution is possible (tape recorded with setting HDV) and I want to get it to work in Ubuntu! 

andy@andy-laptop:~$ lsmod |grep 1394
dv1394                 17596  0 
raw1394                25308  0 
ohci1394               29900  1 dv1394
ieee1394               86596  3 dv1394,raw1394,ohci1394

kino says: Warning: raw1394 kernel module not loaded or failure to read/write /dev/raw1394. I try to cat /dev/raw1394, there is no such file. 

dvgrab says: Error: no camera exists 

Someone has any tips to get this to work? 

/Vifillr

---

