---
title: "Tearing-effects with 177.80 in intrepid amd64 when playing video"
date: 2008-11-24
forum: Multimedia Software
---

### Post by h3nk3 on 2008-11-24
Hello everyone!!!!

I&#7743; so frustrated. I have a 9600gt card from nvidia. I&#7743; running on ubuntu intrepid ibex 8.10 amd64. I have the driver 177.80 installed. I have also compiz effects on (doesn't matter though) and synk to v-blank activated in ccsm.
The nvidia-settings are default hardware settings. I have two monitors and use twinmode + clone in the resolution 1360x768.

Now to the problem!!! Everytime I play video ( I have tried every known player there is for linux) my picture shows tearing effects. I have also change between xvideo,x11,gl,gl2 video-output.
If i go to nvidia-setttings and change synk to x-server to the other screen it works on my lcd
LG LC55. But after reboot it&#347; the same again and i have to switch in the nvidia-settings to the other monitor, save and quit and then back to my lcd again (X-server Xvideo settings and then synk to vblank) to work properly.

I have a picture to easily show my problem.


[http://img179.imageshack.us/my.php?image=screenshot1zj0.png]("http://img179.imageshack.us/my.php?image=screenshot1zj0.png")





Any ideas PLEASE!!!!!!!!!!!

Frustrated nvidia-user from sweden

---

### Post by h3nk3 on 2012-07-20
MARK AS SOLVED!!!!!!

I am now in Ubuntu 12.04 and still using two monitors connected to my htpc. Since i discover that my screens don't use the EXACTLY same hz i add this in /etc/environment file:
__GL_SYNC_DISPLAY_DEVICE="DFP-2"

Where "DFP-2" is _MY_ tv that had tearing problems before

CHEEEEEERS !!!!!!!!!!

---

