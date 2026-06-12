---
title: "Webcam on skype Beta works only for admin user"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by marcinpisz on 2008-03-10
I have a Llogitech Quickcam STX and it work fine with Skype Beta 2.0 when the user had admin privileges.  However as soon as a normal user with everything access except admin in Ubuntu 7.10 it does not see the webcam or the video capture card that I have installed in my computer.  It sees them both if I go to user manager and select admin.  I want to give the user access to Skype webcam but not give them access to admin where they can screw the system up. 

Any way to give access to the I'm guessing /dev/video1 with going to admin mode.  There should be a check mark in Ubuntu to give access to /dev/video1with going to admin mode in the gruops section of users and groups.

---

### Post by ssc351 on 2008-03-10
try this:

sudo gedit /etc/rc.local

then add:

chmod 777 /dev/video0 

before you see the line "exit 0"  Note you may need to change "video0" to video1 or video2

---

