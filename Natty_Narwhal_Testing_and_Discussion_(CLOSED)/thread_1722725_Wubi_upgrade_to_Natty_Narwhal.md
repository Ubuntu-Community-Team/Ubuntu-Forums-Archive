---
title: "Wubi upgrade to Natty Narwhal"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by doctor82 on 2011-04-06
I'm using wubi on my windows 7 pc to load ubuntu version 10.10. Is it okay if I use the command "update-manager -d" to upgrade to Natty Narwhal.
 
I have read [http://ubuntu-with-wubi.blogspot.com/2011/03/wubi-finally-working-in-natty-narwhal.html](http://ubuntu-with-wubi.blogspot.com/2011/03/wubi-finally-working-in-natty-narwhal.html) 

I wonder if I will eventually have to install latest version of wubi andin the process reinstall ubuntu to use Natty Narwhal. It will be a pain to lose my home folder and to build it from scratch.

---

### Post by Rubi1200 on 2011-04-06
As far as I know, upgrades to Natty are okay.

As usual, make sure you have backups before starting.

Last I read, a fresh install is still problematic.

You can do a quick and dirty backup by saving the root.disk to an external medium such as a USB stick.

---

### Post by Mark Phelps on 2011-04-06
While it MIGHT work, it's more likely to cause problems, due to the following:
1) Natty just entered Beta.  From what I've seen before, Wubi-related stuff seems to be among the last things they get working in new versions.  So, while it might work at this stage, it's more likely it won't.
2) Previous releases have mentioned in the Release Notes that Wubi upgrades not only do NOT work, they "break" the existing installation.  Haven't read the Release Notes for Natty, so that may not apply here.
3) There is no way to easily roll-back to your current version if the Wubi upgrade "breaks" it.  You're stuck with a broken version and only a complete reinstall from scratch will fix that.

---

### Post by Frogs Hair on 2011-04-06
I just read that there is currently a problem and Natty and Wubi , but I'm not sure if it was installing Wubi from the beta disc or upgrading.
 
Wubi upgrades are possible , but with a beta release I would be more than a bit gun shy. It's your day , spend it how you wish.

---

### Post by uRock on 2011-04-06
Moved to NNT&D

---

### Post by garvinrick4 on 2011-04-06
If you do give it a go I believe you might need these links!
Live Cd and how to fix a Wubi install by rubi1200 he does specialize
in WUBI installs.
[Index of /]("http://cdimage.ubuntu.com/") 
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
[Ubuntu 11.04 Beta | Ubuntu]("http://www.ubuntu.com/testing/natty/beta") 
[[wubi] Wubi megathread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by bcbc on 2011-04-06
> **doctor82 said:**
> I'm using wubi on my windows 7 pc to load ubuntu version 10.10. Is it okay if I use the command "update-manager -d" to upgrade to Natty Narwhal.
 
I have read [http://ubuntu-with-wubi.blogspot.com/2011/03/wubi-finally-working-in-natty-narwhal.html](http://ubuntu-with-wubi.blogspot.com/2011/03/wubi-finally-working-in-natty-narwhal.html) 

I wonder if I will eventually have to install latest version of wubi andin the process reinstall ubuntu to use Natty Narwhal. It will be a pain to lose my home folder and to build it from scratch.
Avoid beta testing if you can't afford to lose the data. The Wubi fresh install is 'finally working' but it doesn't mean that you won't encounter issues. The upgrade was being worked on up until yesterday and it's apparently solved for installs on the same partition as windows, but whether that fix has made it into the repositories or the daily-live CD isn't clear (to me anyway).

So... testing is good. But make sure you have adequate backups.

---

### Post by doctor82 on 2011-04-07
Thanks for your inputs.:D I guess it'd be better to wait until it appears in my regular updates. I'll leave beta testing for those who can fix it when it breaks.

Edit: I downloaded the latest wubi from [http://people.canonical.com/~evand/wubi/natty/](http://people.canonical.com/~evand/wubi/natty/) and installed Natty. My Natty Kubuntu works great. ( Compiz and emerald stopped working.. but then it needs to be discussed in another forum )

---

