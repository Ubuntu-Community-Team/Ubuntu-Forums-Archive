---
title: "Problems with webcam and gspca in Jaunty"
date: 2009-04-27
forum: Multimedia Software
---

### Post by eternauta on 2009-04-27
Hello, I have just registered.

I have a problem, which is really making me feel very disappoionted towards ubuntu. I am not new to the distro or linux for that case. I have used ubuntu previous versions, now I have just installed Jaunty because I decided to give it a try.

For the time being things seem to work fine, except for one thing... my webcam doesn't work. In the previous versions in downloaded the sources from: [http://mxhaard.free.fr/](http://mxhaard.free.fr/) and everything worked excellent (except on Intrepid, that was the reason why I changed back then). So I decided to try Jaunty, assuming that was solved.

Reading some posts it seems the driver is already supported in the kernel. Fine then I wouldn't have to compile it. So I do a type "lsmod | grep gspca" but nothing is there.

So I tried to compiled those drivers. First problem... they wouldn't :(. I found a patch which was a workaround, so they compiled and were properly replaced by the gspca_build script. I reloaded the modules, didn't work. I tried to see if it worked with "camorama -d /dev/video1". The result was a black and white image, like a picture (no motion at all) divided in three columns like if it captured in a glimpse where the camera was pointing at, but I was a very bad quality image.

Reading a bit more I bumped into this [http://ubuntuforums.org/showthread.php?t=939329](http://ubuntuforums.org/showthread.php?t=939329) which suggested downloading the "libv4l" package and then preloading it "export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so". Of course, didn't work.

Other people suggested installing a previous kernel version, among other things. Of course I won't do that. Before I would download another distro. Though I wouldn't like to do that, it is not like I have plenty of time to install things everyday from zero and the means to download a new distro when I want.

One of the best things (in my opinion) ubuntu has is its community. But it is really depressing to face these problems, or different problems in other distros for the hardware you have, for the software you love and for the slave you dont wanna be. So I hope someone could give me a hand... sorry for distort the thread, thing which I obviously did.

PS1: Maybe this can help you:

```
$ lsusb
Bus 001 Device 002: ID 0ac8:0328 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
# lsmod | grep gspca
gspca                 684880  0 
gspca_vc032x           25856  0 
gspca_main             29952  1 gspca_vc032x
videodev               41600  3 gspca,gspca_main,bttv
```PS2: Yeah I have a tv-card, though never was a problem.

---

### Post by kkady32 on 2009-04-27
hi,this is mine:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and 

> 
gspca_zc3xx         59392  0 
gspca_main          34560  1 gspca_zc3xx
compat_ioctl32      18304  2 cx8800,gspca_main
videodev            45184  5 tuner,cx8800,cx88xx,gspca_main,compat_ioctl32
this was native ,i not must install gspca driver

---

### Post by eternauta on 2009-04-27
Thanks for your reply kkady32. So I shouldn't have installed anything... but anyway the webcam wasn't working as ubuntu came out from the box.

So that means I should reinstall ubuntu so everything goes back to the original installation or what else can I do?

Thanks for your help.

---

### Post by kkady32 on 2009-04-27
test with livecd,normal must work,i have tested my tvtuner and FM radio with gnomeradio and this work in livecd
i have tested my webcam with more programs,work with amsn and skype and not work with camstream and camorama

---

### Post by eternauta on 2009-04-28
I tried with a live cd and things worked. So I reinstalled ubuntu and tried with other programs. After a few adjustments things worked. It seems camorama is kind of buggy.

Though before reinstalling I also tried with skype but nothing there. After I resintalled webcam works in skype and aMSN.

Thank you for your gelp kkady32.

---

### Post by nevdelap on 2009-04-28
So is there a solution? I don't count reinstalling ubuntu as a solution. Hoping......

---

### Post by nevdelap on 2009-04-28
Hi eternauta. Is the output of your lsmod and lsusb looking exactly the same?

---

### Post by eternauta on 2009-05-06
Hello nevdelap,

Of course reinstalling is not a solution. I just did it because I had recompiled the gspca module along with some patches I found. Also, I had been pleying around with a few config files, so the quicker for me was that outcome (to reinstall).

After I reinstalled, I tried with amsn and the webcam worked fine, and with skype I had to choose between my tv tunner card or webcam (so I chose webcam, restarted and worked fine). I would suggest you not to try it on camorama. Even Cheese worked, all happened "out of the box".

About my lsusb and lsmod (regarding the gscpa module, because it has many things):

```
:~$ lsusb
Bus 001 Device 002: ID 0ac8:0328 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
:~$ lsmod | grep gspca
gspca                 684880  0 
gspca_vc032x           25856  0 
gspca_main             29952  1 gspca_vc032x
videodev               41600  3 gspca,bttv,gspca_main
```

I hope you find it useful, otherwise I 'll try to help you.

---

