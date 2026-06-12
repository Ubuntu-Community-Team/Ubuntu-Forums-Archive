---
title: "wifi not loading automatically"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by KeBaBubba on 2010-01-11
Hi. I am a complete newbie to Ubuntu. Just installed it today and everything I have done so far has been found and worked out using forums such as this.

So far I have installed ndiswrapper, the latest version, and got my wifi card working. In fact I am online now writing this!

Problem is when I shutdown and reboot. My wireless connection won't automatically run. It won't even show in the top left that I have a wifi connection. There is no "enable wireless" tickbox. 

I have to type in the terminal:

sudo depmod - a
sudo modprobe ndiswrapper

then my WEP key 

...then it works. 

BTW I have no idea what those commands do I just found them on a forum.

I can't seriously have to do this everything I boot up?!! Can this be automated or is there a better fix?

Cheers
KeBaBubba

---

### Post by Crafty Kisses on 2010-01-11
> I have no idea what those commands do I just found them on a forum.

So when you run "modprobe ndiswrapper" that is loading the ndiswrapper module, now to my knowledge there should be a file called "**/etc/modules**" then you need to open /etc/modules by running:
```
nano /etc/modules
```
Once you're in that text file, you need to add the following line:
```
ndiswrapper
```
Then reboot and see if your wireless works.

---

### Post by KeBaBubba on 2010-01-11
ok sorted thanks! 

Any way of stopping the need to type in the network password each time too?

KeBaBubba

---

### Post by KeBaBubba on 2010-01-11
All sorted - just found the post below

[http://ubuntuforums.org/showthread.php?t=1378648](http://ubuntuforums.org/showthread.php?t=1378648)

:)

---

