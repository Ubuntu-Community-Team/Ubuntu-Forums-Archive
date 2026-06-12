---
title: "Gyachi webcam"
date: 2009-05-14
forum: Multimedia Software
---

### Post by lalkumar on 2009-05-14
WHEN I CONNECT MY WEBCAM USING GYACHI THE ERROR MESSAGE IS"ioctl VIDIOCSPICT Canot edit camera properties"".I AM NEW TO UBUNTU.PLS HELP

---

### Post by loell on 2009-05-14
pls give the version of the program you're using, and the Ubuntu version where you installed it.

and also the camera by posting the commandoutput of **lsusb**

---

### Post by lalkumar on 2009-05-14
I AM USING  UBUNTU 8.04 LTS AND GYACHI IMPROVED 1.1.48
I AM USING MOBILE PHONE AS WEB CAM WHICH I WAS USING IN WINDOWSS XP 
(MTK6227 CHIP SET )

lsusb  gives the following output

desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0e8d:0004  
Bus 001 Device 001: ID 0000:0000

---

### Post by loell on 2009-05-14
ah.. there's the problem, in windows xp i think you need a driver to use that mobile phone camera as a webcam (this is the case of s60)

there's no avaialable driver for that in linux.

---

### Post by lalkumar on 2009-05-15
Yes, I have installed a driver for my phone for windws xp.Can i download a linux driver.If so from which site.Can i uss any inbuilt driver in ubuntu.or other application.
when i gave the cammand luvcview a new window is opend and image from my camera can be seen in it..Also give the following message

desktop:~$ luvcview
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 


How to solve this problem.pls help

---

### Post by loell on 2009-05-15
like I said there is no driver like this on linux, you really have to buy a real webcam.

---

### Post by lalkumar on 2009-05-15
Thank you very much for your help to identify the problem

---

