---
title: "Videos won't play with Firefox 3.6.3"
date: 2010-04-30
forum: Multimedia Software
---

### Post by PDA1 on 2010-04-30
I just upgraded to Ubuntu 10.0.4 (or whatever numbers they are) and now no videos play on Youtube....or any videos using Firefox 3.6.3.  The error message I get on Youtube is;

						You need to upgrade your Adobe Flash Player to watch this video. 

Yeah, so I've downloaded the wretched Adobe Flash Player several times but still no videos play.  However, the problem might be that I'm not putting the Flash Player in the correct folder (like I should really know where to put it!).  

Any idea how to solve this problem?

---

### Post by lovinglinux on 2010-04-30
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by garvinrick4 on 2010-04-30
sudo apt-get remove flashplugin-installer

sudo apt-get clean

sudo apt-get install flashplugin-installer

---

### Post by PDA1 on 2010-05-01
> **garvinrick4 said:**
> sudo apt-get remove flashplugin-installer

sudo apt-get clean

sudo apt-get install flashplugin-installer


Your method worked!  

That was so simple!  Now all videos play.

Thanks a lot!

---

### Post by garvinrick4 on 2010-05-01
> **PDA1 said:**
> Your method worked!  

That was so simple!  Now all videos play.

Thanks a lot! You are Welcome, have a nice day.

---

### Post by vincencollins on 2010-05-02
I was having a problem of the sound in flash not working.  This did the trick.  Thanks!

Update - Flash kept reverting back to 9 which was causing the sound issues.  I fixed the reverting issue by finding the other versions of libflashplayer.so that was confusing firefox as outlined in the following thread - [http://ubuntuforums.org/showthread.php?t=1193479](http://ubuntuforums.org/showthread.php?t=1193479)

> You must have libflashplayer.so somewhere that Firefox looks for it. Typical locations are places like:

~/.mozilla/plugins
/usr/lib/mozilla/plugins
/usr/lib/adobe-flashplugin/libflashplayer.so

---

### Post by alcyst on 2010-05-12
garvinrick4 method didn't work, got an unmet dependencies msg

---

### Post by atr_hugo on 2010-05-12
> **garvinrick4 said:**
> sudo apt-get remove flashplugin-installer

sudo apt-get clean

sudo apt-get install flashplugin-installer

After much confusion, semi-stressed gulps of coffee, and two clean reloads of Lucid Lynx this (and only this) solved my flash/sound issues in Firefox. Thanks!!!!

---

