---
title: "MythTV help? first/fresh install"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by toecutter on 2007-07-19
Have just finished assembly on a quiet media PC and have installed Ubuntu server using these instructions: 

My first hiccup was installing software, apparently the CD burn was bad so it didn't want to install OpenOffice, so I skipped the software install step because I won't be needing any of that anyway. I only mention this just in case this has implications with my actual problem :)

I installed SSH okay, but when I attempted to do the command ```
sudo nano /etc/apt/sources.list
``` I got "sudo: nano: command not found" which I thought was really weird.

I tried a "man" command, but got the same "command not found" message.

I followed the instructions here [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) to "Enabling Repositories with a (non-interactive) Script" and that worked fine. When I did "apt-get update" and "apt-get upgrade" I got the message "0 upgraded, etc., etc." so I assumed all was well at this point, even if I can't manual change my sources.list. 

However, when I tried these commands:
```
$ sudo apt-get install xmltv
$ sudo apt-get install mythtv-backend-master
```

I got the message "E: Couldn't find package" for both.

Any suggestions? I hope I provided all the info necessary, I know it's a lot :)

---

### Post by tgm4883 on 2007-07-19
> **toecutter said:**
> Have just finished assembly on a quiet media PC and have installed Ubuntu server using these instructions: 

My first hiccup was installing software, apparently the CD burn was bad so it didn't want to install OpenOffice, so I skipped the software install step because I won't be needing any of that anyway. I only mention this just in case this has implications with my actual problem :)

I installed SSH okay, but when I attempted to do the command ```
sudo nano /etc/apt/sources.list
``` I got "sudo: nano: command not found" which I thought was really weird.

I tried a "man" command, but got the same "command not found" message.

I followed the instructions here [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) to "Enabling Repositories with a (non-interactive) Script" and that worked fine. When I did "apt-get update" and "apt-get upgrade" I got the message "0 upgraded, etc., etc." so I assumed all was well at this point, even if I can't manual change my sources.list. 

However, when I tried these commands:
```
$ sudo apt-get install xmltv
$ sudo apt-get install mythtv-backend-master
```

I got the message "E: Couldn't find package" for both.

Any suggestions? I hope I provided all the info necessary, I know it's a lot :)

If I were you, i would check the md5sum of the cd image, then reburn and verify the cd.  Then reinstall.  You have nothing to lose doing that.

---

### Post by toecutter on 2007-07-20
> **tgm4883 said:**
> If I were you, i would check the md5sum of the cd image, then reburn and verify the cd.  Then reinstall.  You have nothing to lose doing that.

Very true - will have to do that I suppose! Better safe than sorry, don't want to do things halfway at this point :)

---

### Post by Scorpuk on 2007-07-20
A great guide for mythtv and ubuntu can be found here:

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by Motoxrdude on 2007-07-20
do
```
sudo apt-get update
sudo apt-get install nano
```
Then try again.

---

### Post by tgm4883 on 2007-07-20
> **Scorpuk said:**
> A great guide for mythtv and ubuntu can be found here:

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

IMO, a better guide is here

---

### Post by toecutter on 2007-07-22
hmm...ok...

How about this one: I installed from a fresh CD (checked MD5 sum after downloading, burned at 8x and verified CD before installing). Installed over the existing data on the partitions and software install went without a hitch. But now when I turn on the MythTV box, the monitor gets no signal and just shuts off (goes into power save mode). Any clues? GRUB loader comes up fine and then the screen goes blank. 

I'm following this guide, FWIW: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

except this time I can't even get to login!

---

