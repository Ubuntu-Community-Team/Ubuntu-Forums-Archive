---
title: "Help installing video card"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by charles.g.moore on 2006-08-10
I just bought a new Nvidia G-force6200 because I couldnt get my ATI Radeon9800 working.

My question is: Do I just unplug the box, switch out cards and restart my Kubuntu 6.06?  

The guy at the store said I might want to disable the ATI drivers first but I don't know how you could disable them while running X

I'm obviously not too saavy with the Linux but I have been using it for the past two weeks and love it...

Any help would really help this noob out...

---

### Post by tseliot on 2006-08-10
**How did you install the ATI driver?**
Please answer this question before trying the method below.


1) Swap the cards and connect the monitor to the Nvidia card

2) Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

3) Type:
```
reboot
```

4) The xserver shouldn't crash and you should be able to install the Nvidia driver:
follow Method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

