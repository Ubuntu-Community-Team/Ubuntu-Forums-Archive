---
title: "No Skype Video with Quickcam E2500"
date: 2012-06-29
forum: Multimedia Software
---

### Post by kjaspan on 2012-06-29
I have just installed Ubuntu 12.04 Precise on my new HP p1247 Pavilion x64 AMD computer. Previously I had Skype running, with some tweaks, on 11.10 on my old Dell E310 32 bit Intel Pentium PC.

My video works with Cheese but not with Skype 2.2.0.35 Beta for Linux/Ubuntu. I have tried many of the Forum threads, including those suggesting using LD_PRELOAD=LD_PRELOAD='/usr/lib32/libv4l/v4l1compat.so skype' after installing libv4l-0. I have a Logitech Quickcam E2500 series webcam.

Has anybody had the same problem or is there a solution somewhere?

Thanks in advance.

---

### Post by kjaspan on 2012-07-02
The instructions for Skype 4.0 under the heading "Install method for Skype 4.0 on Ubuntu 12.04 64-bit:" in this URL worked for me. 

[http://askubuntu.com/questions/139279/skype-on-ubuntu-12-04-x64-anyone-has-it-installed](http://askubuntu.com/questions/139279/skype-on-ubuntu-12-04-x64-anyone-has-it-installed)

Problem solved.

---

### Post by kjaspan on 2012-07-09
Alas, the problem was not solved. I did get video but it was frozen. As I said, Cheese worked but not Skype.

---

### Post by pihbar on 2012-08-07
Here's a fun (and mysterious) fact: I have the same problem, but the cam unfreezes when I put my hand over it and reduce the amount of light it takes in. That is, When I reduce the brightness of the room (make it dark by, say, closing the blinds and turning off almost all the lights), the camera unfreezes.

I have been using screen sharing and full-screening cheese as a workaround! :)

---

### Post by pihbar on 2012-08-07
Here's a fun (and mysterious) fact: I have the same problem, but the cam unfreezes when I put my hand over it and reduce the amount of light it takes in. That is, When I reduce the brightness of the room (make it dark by, say, closing the blinds and turning off almost all the lights), the camera unfreezes.

I have been using screen sharing and full-screening cheese as a workaround! :)

---

