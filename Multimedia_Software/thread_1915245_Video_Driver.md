---
title: "Video Driver"
date: 2012-01-25
forum: Multimedia Software
---

### Post by chase321 on 2012-01-25
hello, i am a new linux user, i was wondering if there was a way to install my intel graphics driver to my linux, i looked all over the intel site, all i find id info on the releases... but no install packages, please help!

my graphics card is the intell hd graphics 3000 for 2nd gen prossesors

---

### Post by wolfen69 on 2012-01-25
Video drivers for Intel aren't needed. The linux kernel comes with them. I have the same intel video, and never needed to install anything.

Btw, are you experiencing any issues we should know about?

---

### Post by MoreOrLess on 2012-01-26
Unless you're experiencing an issue, don't touch the drivers. If you are experiencing an issue and want to try updated drivers, [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by chase321 on 2012-01-26
nothing serious, just that when im playing minecraft the screen goes crazy whenever i move, so i thought it was a driver problem. and i know minecraft wasn't made for linux, but still shouldn't it play better than it does?

---

### Post by chase321 on 2012-01-26
ok so i did some looking around and the most suggested solution to my minecraft problem is to install the newest version of java, instead of the java from the software center... but when i go to download the official release from java.com it says i need to use the comand: (su) for the admin account..., i do not know the password.. help?

---

### Post by MoreOrLess on 2012-01-26
ubuntu uses sudo because it disables the root account
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by chase321 on 2012-01-26
ok, but how do i get the password? (or reset it) will this comand work?
<username> ALL=NOPASSWD: ALL

---

### Post by QIII on 2012-01-26
If you installed Ubuntu and gave yourself a username, you are already in the sudoers file.

When you do

```
sudo somecommand
```

just use your login password when prompted.  You won't see anything displayed as you type your password.  That is normal.

As for installing Java, I highly recommend this method:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by chase321 on 2012-01-26
ok ill give that a try tongith! thnx

---

### Post by chase321 on 2012-01-29
ok, so i installed java, but for some reason which I cannot figure out, i still cannot play minecraft without my screen going crazy

---

### Post by morbidchimp on 2012-01-29
> **chase321 said:**
> ok, so i installed java, but for some reason which I cannot figure out, i still cannot play minecraft without my screen going crazy

I believe your drivers are working correctly but maybe your 3d accelleration is not quite right. 

I'm not sure exactly what video card you have but the drivers as already said should be in the Ubuntu Repositories. 

If your new to linux I would recommend installing

sudo apt-get install ubuntu-restricted-extras

Also, you may need to install additional drivers to take advantage of 3d properly. Check "Hardware Drivers" for any updates and install them if there are any. 

Also, are you having the same problem with any other games? - or youtube? or is this problem only effecting Minecraft.

---

### Post by chase321 on 2012-01-30
ok, so i figured out, if i play minecraft in full screen, it work perfectly :P so problem solved thanks everyone for all your help

---

### Post by chase321 on 2012-01-30
it was only minecraft

---

### Post by chase321 on 2012-01-30
and when i check additional drivers, there are non available

---

### Post by chase321 on 2012-02-29
ok so this is solved thanks :)

---

