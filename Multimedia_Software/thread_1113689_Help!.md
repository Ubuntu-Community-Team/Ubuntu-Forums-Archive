---
title: "Help!"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Simple dude on 2009-04-01
I've tried googling this, with no avail in help.


Note, I'm a complete linux newbie, as I've been a recent convert, and if I can't fix these problems, I might have to switch back to *dreads it* windows

I installed the most recent nvidia 64 drivers, NVIDIA-Linux-x86_64-180.29-pkg2.run, successfully

my current hardware setup is 

asus m3n78vm motherboard
phenom II x3  720 processor
corsair twinx ddr800, motherboard automatically reads it at ddr933
Generic case and 420w supply

Currently running ubuntu 8.04 64 bit, because 8.10 won't recognize my hard drives

I'm trying to get my onboard geforce 8200 to function. The computer will run in low graphics mode, but no matter what I've tried, I can't seem to get the box to recognize my onboard 8200, and always tells me it can only run in low graphics mode. I'm thinking about getting a videocard to fix it, but I'm waiting for tax refund money before I can even think about it.

The videocard I'm eyeballing is a msi geforce 260 216stream, clocked at 655

What I found is interesting, is envyng recognized it, when I used that, before I did my current driver install.

 Any ideas how I can get my 8200 to work so I can delay buying a videocard as long as possible?

Also, I installed flash 64bit, and it still won't work. I'm hoping fixing one problem will fix the other

Any help is highly appreciated

---

### Post by wolfen69 on 2009-04-01
you should have just installed the nvidia drivers from system>administration>hardware drivers. installing the latest drivers from nvidia probably won't give you any boost on an older card.

for flash, remove what you have, and go [here]("http://get.adobe.com/flashplayer/") and download the tar.gz flash file. right click it and select extract here. you will see a file inside the folder called **libflashplayer.so**

do
```
gksudo nautilus
```
navigate to the **libflashplayer.so** file and right click and copy it. then navigate to /usr/lib/mozilla/plugins and paste it there. restart firefox if open.

---

### Post by Simple dude on 2009-04-01
I'm not worried about a speed boost. I tried the driver installation method you suggested first, and it still won't recognize my integrated graphics. This is beyond frustrating to me. I have very little hardware accelleration, so even HL2 looks horribly ugly.

I'm not worried about speed, I just want it to work, and display things correctly.

Websites aren't even showing up right.

---

### Post by Simple dude on 2009-04-02
This is damn well frustrating. 

I'm using 8.04 64x because 8.10 won't recognize my sata controller.

It won't run in anything but low graphics mode, since it won't recognize my onboard. I got flash to work, using nsplugwrapper. I'm lost...

---

