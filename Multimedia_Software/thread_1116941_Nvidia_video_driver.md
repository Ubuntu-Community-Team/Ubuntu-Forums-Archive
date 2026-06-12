---
title: "Nvidia video driver"
date: 2009-04-05
forum: Multimedia Software
---

### Post by bdmw1 on 2009-04-05
I need to write a program which will make use of the new Nvidia driver for H.264 video decoding. I want to setup a NX server where 3 developers will share it as the development machine and to execute the program on. Now, my questions are as follow:

1) Assuming that I installed the Nvidia video card on the server and three of us can time-share the video card. Would this setup work well under NX? i.e. Could the video be seen on the client machine?  

2) Assuming that I installed 3 Nvidia video card on each of the client machines, can I make use the video card on the client to do the decoding while the program is executed on the server?

I tried 1) above but I got the following error message:
Xlib: extension "NV-GLX" missing on display ":1008.0"

Any help is greatly appreciated.

---

### Post by wolfen69 on 2009-04-05
perhaps you should ask in the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") section.

---

### Post by hessczoo on 2009-04-05
Okay, well NX works by processing data on the host machine, and sending the display to the client machine.

So yes, one graphics card is needed on the host machine, and each client machine shouldn't need a video card to display. You must understand though of the lag you will be getting from this. Unless this machine is local, or you have a very good connection to the internet, it will be incredibly slow and laggy. Also, if you have 3 people logged into the machine watching decoding different videos and sharing the card, unless the card is good expect a slow down.

---

### Post by bdmw1 on 2009-04-06
Thanks for the answers.  

Knowing that all 3 developers and the host machine are all inside the same gigabit network and they will NOT execute the decoding program simultaneously, I am not particularly worry about the lag.

Having said that, I do encounter the following error message when I tried to run my executable on the NX Client:

Xlib:  extension "NV-GLX" missing on display ":1008.0".
after vdp_device_create,vdp_st=1
Segmentation fault (core dumped)

When I type "xvinfo" on the terminal, it outputs

X-Video Extension version 2.2
screen #0
 no adaptors present

Any suggestion on how I could fix this? 

Many thanks

---

