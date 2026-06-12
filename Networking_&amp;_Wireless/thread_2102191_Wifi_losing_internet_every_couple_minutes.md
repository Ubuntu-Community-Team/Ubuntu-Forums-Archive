---
title: "Wifi losing internet every couple minutes"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by flangust on 2013-01-06
I know some other people have run into this problem as well but so far I haven't found a solution.  Every couple minutes, or link clicks, webpages just sit and spin and spin and spin.  I have to reconnect to my wifi, to get it working again.  It's starting to get old.
   I'm running a Samsung Chromebook (the original one, can't remember the name just now), which has an Atheros AR9300 card, on Ubuntu 12.04.  My router is set to WPA-Personal.  But, I believe I also tried WPA2.
   I've tried doing the modprobe with nohwcrypt=1, but that doesn't seem to help.  I've tried setting my router to different channels.  I've also tried pinging my router, and google.com, when I can't get to a page, and that seems to work fine.
   If anyone has any suggestions, it'd be greatly appreciated.

Thanks

---

### Post by flangust on 2013-01-07
Well, it appears I was being a dum dum.  Setting the router to WPA2 only seems to have fixed the issue... For now.

---

### Post by doxramos on 2013-01-08
Another thing to try is 
```
sudo apt-get update
```
and then afterwards 
```
sudo apt-get upgrade
``` if running 12.04 or 12.10.

---

### Post by flangust on 2013-01-09
I had actually run a couple updates since the problem started.  Since I'm dual booting a Chromebook, if the wireless issued pissed me off enough, I'd just reboot into Chrome and surf from there.  But since I started coding more it was becoming a real hassle.
Thank you for the suggestion, though.

---

