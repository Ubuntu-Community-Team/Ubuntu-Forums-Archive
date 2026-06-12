---
title: "Updates That Never Install?"
date: 2011-04-25
forum: Mythbuntu
---

### Post by uncle hammy on 2011-04-25
For about the last 2 weeks, when I ssh into my Mythbuntu 10.04 machines (3), I see 2 "updates available" notifications (see image), which is odd on it's own.  However, the second one says 7 available, but apt-get update / upgrade never installs anything.

I have also noticed, that in this same time, I have not received any updates from x-swat ppa which I use for NVidia drivers...yet there are updated drivers available.  I also haven't received any MythTV updates from the JYA repos.  In fact the only updates I seem to be getting are alsa updates from the ubuntu-audio-dev ppa.

I am running using the 2.6.32-29 kernel because the audio-dev isn't up to date past there yet.  I manually removed the 2.6.32-30 kernel a while ago, when I realized the audio-dev limitation.

The above info is true on all 3 of my machines.

Anyone have any ideas what is going on?

TIA

---

### Post by junglist313 on 2011-04-25
Try this:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by KegHead on 2011-04-25
Hi!

Have you tried:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

### Post by uncle hammy on 2011-04-25
> **KegHead said:**
> Hi!

Have you tried:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

Before I do that, not because I think you're trying anything "funny" :).  What does -f do?  Also, will sudo apt-get install linux-image -f still leave me at the .29 kernel? And, finally, will the sudo apt-get dist-upgrade -f still keep me on the .29 kernel, and 10.04?

Thanks

---

### Post by KegHead on 2011-04-25
Hi!

-f forces the upgrade.

If you want to upgrade to the latest kernel you should use dist-upgrade. But keep in mind that you will only get the kernel delivered with the version of Ubuntu with bugfixes. For example, if you have 10.04 installed you will not get a kernel newer than 2.6.32, with 10.10 you will not get another kernel as 2.6.35, and so on.

-f is used routinely, I use it every morning as I posted.

KegHead

---

### Post by uncle hammy on 2011-04-25
I did as requested, and ended up upgrading to the 2.6.32-31 kernel from the .29 kernel.  However, still have the same problem...

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

7 packages can be updated.
1 update is a security update.


myuser@mymachine:~$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by KegHead on 2011-04-25
Hi!

Please see;

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I update my kernel daily!

KegHead

---

### Post by uncle hammy on 2011-04-25
OK, but how does that help me resolve my problem of these 7 mystery updates that don't want to install (even with the -f flag as attempted per your suggestions), and updates that I know for sure that are out there (i.e. NVidia drivers from x-swat ppa) that aren't being found?

---

### Post by KegHead on 2011-04-25
Hi!

If I read this correctly, a kernel update will resolve?

sudo apt-get install linux-image -f

Only suggestion I can make.

KegHead

---

### Post by uncle hammy on 2011-04-25
sudo apt-get install linux-image -f upgraded me to the .31 kernel from the .29 kernel fine.

However, after that, I still have these mystery 7 upgrades, which I cannot seem to install.

sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks for you help!

---

### Post by lmclaren on 2011-04-27
Are you sure you are not seeing the bug where the motd does not update?

If you do an "apt-get update" does it tell you that you have packages to update?


[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827)

---

### Post by uncle hammy on 2011-04-27
That would likely be my issue.  Thanks!  

Now, if I can just figure out why the latest Nvidia drivers from x-swat aren't being grabbed...

---

