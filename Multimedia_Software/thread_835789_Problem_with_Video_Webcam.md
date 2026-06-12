---
title: "Problem with Video Webcam"
date: 2008-06-20
forum: Multimedia Software
---

### Post by Nero60 on 2008-06-20
Using latest version of Ubuntu (8.04) with latest updates.  I have an ET USB 2750 Video Camera from eMPIA Technology.  I was told that to utilize the camera with Ubuntu, I should download "Camorama Webcam Viewer" and that should activate video camera capabilities.  When I try to use "Camorama Webcam Viewer", I receive the following error message "Unable to Capture Image.  Is this a set-up problem or should I be using some other type of add-on?

---

### Post by ahbart on 2008-06-23
Instead of camorama you could try cheese too. 
Do you have more then one webcam or do you have a tv-card in your system?
Camorama is looking for a /dev/video0 device by default.
You could try the command in a terminal: 
camorama -d=/dev/video1 
If you have a second webcam or a tv-card.

---

### Post by Nero60 on 2008-06-23
I have only one video camera which is built in to my laptop.  The laptop does have a tv card.  I tried your suggestion and receive "Could not connect to video device" Please check connection.

---

### Post by ahbart on 2008-06-23
Could you print the line with the output about your camera:
lsusb

---

### Post by Nero60 on 2008-06-24
Per your request:

Bus 005 Device 002: ID eb1a:2750 eMPIA Technology, Inc. ECS Elitegroup G220 integrated webcam
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 001: ID 0000:0000  

Appreciate the help!

---

### Post by ahbart on 2008-06-24
I'm not sure what cam you have but you could try to install and use easycam:
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by Nero60 on 2008-06-25
Unable to install easycam. Any other suggestions??

---

### Post by ahbart on 2008-06-25
has you tried easycam2 also as suggested?

---

### Post by markbuntu on 2008-06-25
Try installing V4l. V4l2 did not find my Logitech Quickcam Communicate STX camera in Ekiga but V4l found it by name. Then it worked with everything.

---

