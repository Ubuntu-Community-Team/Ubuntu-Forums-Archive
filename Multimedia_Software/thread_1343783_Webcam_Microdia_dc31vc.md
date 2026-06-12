---
title: "Webcam Microdia dc31vc"
date: 2009-12-02
forum: Multimedia Software
---

### Post by Ansraliant on 2009-12-02
Hi everyone!.
I have a dual mode 8000 VGA camera (i know it's old bt i do not want to buy a new one), it works perfectly on windows, but i can't make it work in ubuntu.
I plug it in, open skype, cheese or any other program it says "camera not found".
Here's the output of lsusb

$ lsusb
Bus 005 Device 002: ID 045e:003c Microsoft Corp. SideWinder Joystick
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0c45:8000 Microdia DC31VC
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:00f9 Microsoft Corp. 
Bus 003 Device 002: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

As you can see it seems it does recognize it.
I found on google [this]("http://www.linux-projects.org/modules/news/") web site. It has drivers for microdia webcams. But i can't find my model. 

Thanks for everything.
Ansraliant

---

### Post by jamesvar_70 on 2009-12-02
hi,

Just try the following link, it worked for me partially

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs&pli=1](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs&pli=1)

good luck

james

---

### Post by Ansraliant on 2009-12-04
Thanks for the answer. I tried it and it worked, thanks.

---

