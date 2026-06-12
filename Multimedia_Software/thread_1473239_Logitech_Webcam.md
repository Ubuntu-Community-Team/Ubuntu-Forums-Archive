---
title: "Logitech Webcam"
date: 2010-05-05
forum: Multimedia Software
---

### Post by vvil2 on 2010-05-05
I just bought a Logitech Webcam c200 but it's not working with my computer. I have the latest version of Ubuntu and have the cd that came with the webcam in the computer but whenever I go to install the software an error screen pops up. Can someone help?

---

### Post by no2498 on 2010-05-05
cd's for windows do not work on ubuntu
take the cd out

plug the cam in

look at the top left of your screen window
click applications
go down the list click terminal
a small window opens

copy and past this

gstreamer-properties 
click enter

1 more window opens

click video
try v4l1 and v4l2
click the bottom test button for each 1

hope you seen yourself


a program called 
cheese webcam booth should be loaded

in applications sound & video

click cheese see if the cam works


hope this helps

---

### Post by tubunu on 2010-05-05
I have exactly the same webcam and I didn't need to install anything. It is recognized out of the box on Lucid. Just plug it in, open Skype and call a friend. That's it. If you go to Options/Video Devices in Skype, you should see a drop down menu with the name of your webcam, i.e.: 

UVC Camera (046d:0802) (/dev/video0)

---

### Post by vvil2 on 2010-05-05
Thank You so much! It works now :-)

---

### Post by wired99 on 2010-05-06
my Logitech QuickCam shows up under "lsusb" but it is not available under "/dev/video0"
How can I make the connection?

gstreamer-properties test fails on my system.

(Ubuntu 10.04, Gnome 2.30.0)

---

### Post by no2498 on 2010-05-06
look in the add remove

see if you have the good, bad, ugly  installed

---

### Post by wired99 on 2010-05-07
> **no2498 said:**
> look in the add remove

see if you have the good, bad, ugly  installed


Unfortunately I don't understand what this means

Where should I look to "add" or "remove"?
gstreamer-properties doesn't show these options and neither does Cheese.

Can you be more specific?

---

### Post by no2498 on 2010-05-07
in the add&remove program in applications
type gstreamer

see what all is installed

---

