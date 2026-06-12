---
title: "Creative Webcam Vista PD1100 Not working"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by buntu_Geek on 2008-02-09
I have tried installing gspca-source ( as i m a gutsy user and have a kernel 2.11+ )

But when i try camorama i get error:
Cannot connect to video device (/dev/video0)

I thought of trying ov51x-jpeg but it doesnt support my webcam ( Creative Vista PD1100)

And there is no doubt that the webcam is recognized...
venkat@venkat-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 041e:401a Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000 

I haven't yet figured out whats the problem .. 

Please Help :(

---

### Post by linuxwizard on 2008-02-09
Try using Ekiga see if webcam is detected/works. Also you might have to change settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there

---

### Post by buntu_Geek on 2008-02-10
I tried that... but the video device is not detected....

The problem is that mount point /dev/video0 is not created when i plug in my webcam... i dunno whats the problem....

will there be any problem in configuring gspca.....

Anticipating Help.....

---

