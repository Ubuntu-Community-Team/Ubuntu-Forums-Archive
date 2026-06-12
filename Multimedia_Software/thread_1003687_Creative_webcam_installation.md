---
title: "Creative webcam installation"
date: 2008-12-06
forum: Multimedia Software
---

### Post by jlopez67 on 2008-12-06
Hello - I'm new to ubuntu. I found another thread discussing my issue but it appears to be archived:
[http://ubuntuforums.org/showthread.php?t=543204](http://ubuntuforums.org/showthread.php?t=543204)

I have the Creative Live! Cam Optia and Ubuntu 

Below is the output of my lsusb command:

Bus 002 Device 003: ID 041e:4057 Creative Technology, Ltd 
Bus 002 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09


Per the archived thread, I ran the following command:

sudo apt-get install camorama

It appears to have run successfully?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  camorama
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 208kB of archives.
After this operation, 1524kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe camorama 0.19-2 [208kB]
Fetched 208kB in 2s (92.7kB/s)   
Selecting previously deselected package camorama.
(Reading database ... 113888 files and directories currently installed.)
Unpacking camorama (from .../camorama_0.19-2_i386.deb) ...
Setting up camorama (0.19-2) ...


I am using Skype and when I select Options -> Video Devices -> Test 
I am still unable to see video and the Camera is not on.

Any other ideas?

Thank you in advance :)

---

### Post by wolfen69 on 2008-12-06
there is a chance that it is not compatible with linux. you may have to buy a new one. see [this site]("https://help.ubuntu.com/community/Webcam") for info on getting it to work. [here]("http://mxhaard.free.fr/spca5xx.html") is a list of compatible webcams.

---

### Post by jlopez67 on 2008-12-06
THank you.

The site shows my camera is supported. When I followed the instructions on the other link for the 32 bit install, things appeared to be successful, but still not recognizing the camera.

---

