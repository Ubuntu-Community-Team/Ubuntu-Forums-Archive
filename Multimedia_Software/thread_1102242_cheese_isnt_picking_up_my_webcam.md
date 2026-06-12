---
title: "cheese isnt picking up my webcam"
date: 2009-03-21
forum: Multimedia Software
---

### Post by louislmao on 2009-03-21
i have microsoft vx1000 webcam. i used easycam2 to install a driver and it says its installed but for some reason cheese says "no webcam found"

i dont know what to do
any help???

---

### Post by ryecomp on 2009-05-05
VX1000 works sluggish in ubuntu 8.10 version, but after upgrade to ubuntu 9.04 this cam is not recognizable and /dev/video0 is not created. So, there is no way for application to use cam. 

I tried latest gspca driver, but it didn't work. I think there is some upgrades on this cam driver, so let's wait for them.

---

### Post by ryecomp on 2009-05-07
Finally....  VX1000 works in ubuntu 9.04. 

1) Follow the procedure specified in [http://moinejf.free.fr/gspca_README.txt](http://moinejf.free.fr/gspca_README.txt)
(removal of ALL the gspca*.ko files in system, .config making, and make & make install)

2) When step 1 not working, delete gspca_sonixj.ko from system (/lib/modules/.... directories)
Plug in & off & check dmesg & test with cheese. My system starts to work when 
gspca_sonixj.ko is deleted from the system. Deletion of .ko file not related to kernel 
gspca_sonixj module working (may be cached). 

3) reinstall gspca_sonixj.ko

4) rebooting & check it is still OK!

---

