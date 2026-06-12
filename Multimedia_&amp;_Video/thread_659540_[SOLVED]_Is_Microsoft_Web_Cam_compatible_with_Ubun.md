---
title: "[SOLVED] Is Microsoft Web Cam compatible with Ubuntu??"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by RMD94 on 2008-01-05
I have a Microsoft web cam on Ubuntu and when I am on a video conference through a source (eg. Skype) I can't turn on my web cam. The button saying " Show my web cam" in Skype is not visible.......
Is Microsoft web cam compatible with Ubuntu???

Please do help!! 

I am sorry!! if there are some mistakes, as you see I am new to Ubuntu...


Thank you

---

### Post by linuxwizard on 2008-01-05
in terminal > type lsusb > post results

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by RMD94 on 2008-01-06
dosen't work!! I went to the link above and I downloaded a Skype package for Ubuntu but it dosen't open.... looks like its a debian pacage......

any way Thanks!!! a lot

---

### Post by linuxwizard on 2008-01-06
Have you tried using Camorama or Ekiga to see if cam works in these ? Have you installed any driver for the webcam ? I asked for the results from the command that I gave to check ID# & Vendor# to use to find that cam to see if it is supported or not and which driver you may need.

---

### Post by frafu on 2008-01-09
Hello,

As the Accessibility forum is intended to discuss software related to disabilities, I am moving this thread to a more appropriate forum. 

Have a nice day. 

Francesco

---

### Post by RMD94 on 2008-01-13
after typing lsusb i got the result 

Bus 002 Device 003: ID 0bda:0103 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:00f7 Microsoft Corp. 
Bus 001 Device 002: ID 046d:c517 Logitech, Inc. 
Bus 001 Device 003: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 001 Device 001: ID 0000:000

 in ekiga the web cam works

i am using skype 1.4 itried to install skype 2.0 beta but it doesnt support 64 bit

i didnt installed any drives

---

### Post by linuxwizard on 2008-01-13
As long as the webcam is working in Ekiga your system has detected the cam you will not have to install any drivers for it. If it not working in Skype not much you can do about that.

---

