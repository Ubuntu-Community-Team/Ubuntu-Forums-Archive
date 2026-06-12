---
title: "NVidia 630 GT (and 9500 GT) not displaying 2560x1080"
date: 2014-01-07
forum: Multimedia Software
---

### Post by richardmarzan on 2014-01-07
I recently got an nvidia 630GT. It has 1 mini-hdmi, 2 DVI-I outputs. The card specification is able to output 2560x1600 max. I only need 2560x1080@60. However, HDMI only gets me 1920x1080 and Dual DVI-D connections (both ports) give me 2560x1080 but the text and mouse on screen are horribly pixelated. xrandr does nothing when adding a creating and adding a new mode with and without blanking using CVT and GTF. I created my own monitor section at /usr/share/X11/Xorg.conf.d/10-monitors with appropriate modelines and nothing. 

I read in a post that nvidia has locked the pixel clock in drivers above 301.x making it difficult to run custom modelines. 

I tried the machine in windows and the DVI-port still outputs that ugly pixelated image...however, when I switch to HDMI it is crisp and clear at 2560x1080 which doesn't matter because it's windows. If I can get it to run in Ubuntu at the same rate with the same cable everything would be ok.

I tried using a custom EDID in xorg.conf and I get nothing...What happens then is that Ubuntu outputs 2560x1080@60 with the same pixelated image that I get when connected throught DVI.

If anyone needs more information or for me to try anything else I am willing to do so. 

PS. The previous card gave me the same issue a 9500 GT but it then worked flawlessly with VGA, However, I want to put my new card to use and would rather not use VGA but prefer a digital connection like HDMI or DVI.

---

### Post by richardmarzan on 2014-01-08
[Solved]! Kinda...I just tried the new DVI cable from Cable Matters that I got from amazon with  noise chokes on both ends and this thing is no longer is pixelated @  2560x1080. It is working beautifully. However, Nvidia should bring their  linux drivers up to parity with windows drivers. There is no reason why  this card should not be able to output 2560x1080@60 over HDMI on linux  when it does so just fine under Windows 7. One more mess-up like this  and I will default to ATI or Intel graphics in the future. As for now,  I'm content with the DVI cable giving me a crisp clear image as it should.

---

