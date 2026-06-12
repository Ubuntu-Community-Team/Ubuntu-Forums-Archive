---
title: "How do I install the CPIA webcam driver?"
date: 2008-08-07
forum: Multimedia Software
---

### Post by ReallNeurotiq on 2008-08-07
I found the fabled driver that makes my oriental PACE cam work, I don't want to go buy a logitech if I don't have to, and I think buying a different cam will not aid the learning experience. I am fairly new to linux so use noob terms, in my /dev/ folder there is nothing relating to video as the instructions claim, this may be because it was intended for redhat, I'm not sure.

[http://webcam.sourceforge.net/#info]("http://webcam.sourceforge.net/#info") is the link to the driver I need. I have downloaded it, and being a tar I tried to install it as I have done with other drivers in the past, but this one is not executing, and according to the installation guide this is a copy and paste then make procedure, so I'm just confused. I'd rather see this work than cave and just buy a different one.

I'm not getting any errors other than webcam not detected

and I have tried cheese, camorama etc. the case is probably that this driver needs to be installed. 

i need halp :p.

For anyone else who has a problem these are the webcams that this driver allows support for :
# Aiptek HyperVcam Fun USB (some use the OV511!)
# Creative Video Blaster WebCam II
# Digicom Galileo USB
# Dynalink Digital Camera
# Ezonics EZCam (Not Pro or Plus)
# Intel Play QX3 Microscope
# Microtek EyeStar
# Pace Colour Video Camera
# SuperCam WonderEye
# TCE Netcam 310 USB
# Terracam USB(Not Pro) - Note: some of these use OV511 not CPiA chips
# Trust SpaceC@m Lite
# Utobia USB Camera
# ZoomCam

---

### Post by Rmantingh on 2008-09-23
Hi there,

Did you ever get this to work.
I'm interested to know how you did it.

Ruud

---

### Post by kickwin on 2010-11-16
Same issue. Dont know how to install the deb. Get this error - "Error: Dependency is not satisfiable: python-gtk-1.2"

---

### Post by no2498 on 2010-11-16
kickwin

you try the cam in cheese ?
most webcams just work now days

---

### Post by kickwin on 2010-11-16
No it doesn't work with Cheese. It is an old webcam and of the CPIA type.

---

### Post by no2498 on 2010-11-17
with the cam unplugged in a terminal type lsusb click enter
now plug it in and do it again


also in a terminal dmesg click enter

---

### Post by davebritton on 2010-12-23
lsusb doesn't see the cpia webcam
no joy yet 
has anyone gotten this to work?
it seems like the cpia drivers have been removed from the kernel

---

### Post by no2498 on 2010-12-23
with the cam plugged in open a terminal type,  lsusb click enter

you should see the # and name of the cam

put that in google  find the driver you need to use do not guess

---

### Post by no2498 on 2010-12-23
just reread it my bad

do you need to turn the cam on first
i need to turn mine on and set it to be used as a webcam
its a aiptek 3100

have you tried this yet

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

if not you need to have
gstreamer good,bad,ugly, and 10 installed

you can find them in the package manager

---

