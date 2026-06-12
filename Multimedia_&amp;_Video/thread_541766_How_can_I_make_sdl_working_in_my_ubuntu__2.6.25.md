---
title: "How can I make sdl working in my ubuntu ? 2.6.25 ?"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by renjith on 2007-09-03
Hi, 
I have  a video capture card to test videoIN. 
The driver is installed and the test app reqiored sdl.
I hae installed sdl  and the requied other libs as well.
But i am getting an  Error like , 
 
              unable to initialize SDL: No available video device

when I run my test app.

kindly gimme a suggestion.... 
I was going thru the forum comments as well. and as per the suggestions, 
I tried with  
          xhost +local:root 
and 
         export DISPLAY=:0.0 in a new terminal.

I am using my video card as follows,
  
But the result is same. :(Section "Device"
        Identifier      "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Now, after commenting the "DRI " lines in the /etc/x11/xorg.conf, I can play video with 
mplayer but , still the test app using sdl is giving the same errror.. pls advice..

Thanks 
Ren








How can I make sdl working in my ubuntu ? 2.6.25 ?

---

