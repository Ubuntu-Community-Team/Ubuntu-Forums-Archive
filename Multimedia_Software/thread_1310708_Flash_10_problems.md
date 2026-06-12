---
title: "Flash 10 problems"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Alain21 on 2009-11-02
I try to different solution in order to get flash 10 working after I upgrade to Ubuntu 9.10 .... 

1) Using Firefox 3.5, and flash 10 ... I get things working, but playing some games get choppy and slow causing several screen refresh problem. This was not the case under my old ubuntu 9.04 with firefox 3.0

2) I also tried Opera 10, and speed-wise its flawless, but there is another problem. Everytime I click anything in flash (button, text, etc) It seem to do something wrong with focus, or I don't know. I cannot click anything else afterward. I have to click outside of the flash box (empty spot on the web page) and then I can click something in-game

Is there a way to fix those ? Or is there a way to still use firefox 3.0 ? or using both version keeping my 3.0 for flash gaming ?

---

### Post by qhor on 2009-11-02
> **Alain21 said:**
> Is there a way to fix those ?

Are you using 64-bit Ubuntu?

If so, I had what seems to be the same problem today. After searching the forums, I found that this is apparently a bug with the wrapper (nspluginwrapper) used to make 32-bit Flash work on 64-bit Ubuntu.

A good solution until the bug is fixed is to install 64-bit Flash. (Supposedly, this is in "alpha" status, but users are reporting it seems as stable as the regular Flash plugin.)

Add this PPA: [https://launchpad.net/~dinxter/+archive/test](https://launchpad.net/~dinxter/+archive/test)

Then do:
  sudo apt-get update
  sudo apt-get install flashplugin64-installer

You do not need to reboot. Just restart Firefox, and all should be well.

(Other relevant threads if you want to read further: [http://ubuntuforums.org/showthread.php?t=1232816&page=4](http://ubuntuforums.org/showthread.php?t=1232816&page=4), [http://ubuntuforums.org/showthread.php?t=772490&page=80](http://ubuntuforums.org/showthread.php?t=772490&page=80), [http://ubuntuforums.org/showthread.php?t=1241313&page=5](http://ubuntuforums.org/showthread.php?t=1241313&page=5))

---

### Post by Alain21 on 2009-11-02
> **qhor said:**
> Are you using 64-bit Ubuntu?


Hmmm no i'm not using 64bit ubunntu ... just regular 32bit one. 

I've notice that for some reason, while in Opera 10, it's only some games that actually seem to cause the "button" problem. Armor games' Frontier; Sonny 1; sonny 2 for example. while most others games seem fine. 

Might be a programming issue with one technique of doing button behavior, while some other techniques are fine.

---

### Post by wojox on 2009-11-02
Look here: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567") and scroll down to Flash Optimization. Sounds like a conflict.

---

### Post by Alain21 on 2009-11-03
> **wojox said:**
> Look here: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567") and scroll down to Flash Optimization. Sounds like a conflict.

Wow that's really useful ... thanks! ... i'm gonna try some of those tweaks

---

