---
title: "I have lost my GUI and can't get a terminal except in recovery mode"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by mrmonday on 2007-02-14
Hi everyone,

I am new to Linux and I recently installed Ubuntu 6.10. Iad quite a few problems, such as not being able to access the internet and not being able to show the correct resolution for my monitor.

I managed to get the internet working, after lots of messing around (however updates wouldn't work), so I decided I would try to get the 3D graphics working. I followed the guide [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html") and got to the point where it said to run:
```
sudo nvidia-glx-config enable
```
Which I did, this command said to restart my PC for the changes to take effect... I did so and then my PC couldn't boot into a graphical interface. It gave an error that said something like it could not start the X11 server. It did however leave me with a terminal prompt. I tried to run:
```
sudo nvidia-glx-config disable
```
which gave me no success. After asking in [this thread]("http://ubuntuforums.org/showthread.php?t=359702") I ran [envy]("http://albertomilone.com/nvidia_scripts1.html"), which couldn't connect to the internet to download the drivers. Using the ping command, I could ping any IP address, not just ones on my network. I tried again, however yet again it didn't work. Having given up I tried to install the nvidia drivers by hand... Big mistake... now I get the error, and no terminal prompt. I can still get to a prompt via recovery mode, which gives me root access. I am to afraid to go near Linux now, and would like to just have it working, so I can get on with my life, without spending all day trying to figure it out. Thank you very much for any help you can provide.

My graphics card is the XFX nVidia Geforce 7300GS with turbocache.

---

### Post by taurus on 2007-02-14
Did you make a backup copy of your /etc/X11/xorg.conf?  If not, then boot into the recovery mode and run

```
dpkg-reconfigure xserver-xorg
```

---

### Post by mrmonday on 2007-02-14
I have tried this... but I must have entered some settings wrong, I still can't get a GUI. Thanks for your help.

---

### Post by taurus on 2007-02-14
Did you use **vesa** for your driver?

---

### Post by mrmonday on 2007-02-14
No I used nv, as suggested [here]("http://ubuntuforums.org/showthread.php?t=359702&page=2").

---

### Post by taurus on 2007-02-14
Try vesa for now to see if it fixes your problem or not since nv doesn't work!

---

### Post by mrmonday on 2007-02-14
Nope. No luck.

---

