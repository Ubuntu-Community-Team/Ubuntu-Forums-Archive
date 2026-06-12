---
title: "Flash/Javascript Videos Not Working"
date: 2011-11-17
forum: Multimedia Software
---

### Post by mashmusic11235 on 2011-11-17
Youtube is working, but no videos from other sites are (Google videos, Photobucket videos, etc - these videos are *not* working). The video object comes up (that is, the box where the video should be), but nothing happens inside of it. I've tried clearing my history, rebooting, etc, and nothing seems to work. I've checked my Flash and Javascript, and they're both installed and up-to-date. These videos have been working fine up until now.

---

### Post by ajgreeny on 2011-11-17
How did you install the flash plugin?

---

### Post by mashmusic11235 on 2011-11-17
It was a while ago, but I'm pretty sure I installed it from Firefox>Tools-Add-Ons, because I couldn't figure out how to run it from the .tar.gz that comes from Adobe. 

I'm not sure why it matters, though, because it was working up until now.

---

### Post by wolfen69 on 2011-11-17
Try reinstalling it with the [Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") plugin for firefox. It works for a lot of people.

---

### Post by mashmusic11235 on 2011-11-17
I installed the Flash Aid plugin, but I'm not sure exactly what I should DO with it/how to make it work/what it does.

---

### Post by Stochastic on 2011-11-17
You'll see a red circle icon to the right of your firefox address bar - that's the add-on's menu.

I found that using it to install the current (oneric) release was unsuccessful because of this error at the end of the script ```
Package flashplugin-nonfree is a virtual package provided by:
  adobe-flashplugin 11.1.102.55-0oneiric1
  flashplugin-downloader 11.1.102.55ubuntu0.11.10.1
You should explicitly select one to install.

E: Package 'flashplugin-nonfree' has no installation candidate

```
**However,** I then tried with the beta release of flash and it worked great!

Thanks wolfen69, great tip.


***** Edit/Update *****
I found the beta version of flash to be VERY crashy  :(
So after running through the Flash Aid's script for installing the regular flash I then opened a terminal and typed ```
sudo apt-get install adobe-flashplugin
``` then restarted firefox.  I now have an up-to-date flash working great.

p.s. this is a great site to let you know what version of flash is currently running on your browser: [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

---

### Post by mashmusic11235 on 2011-11-17
Thank you so much! I did everything you said, and it works perfectly! Youtube videos even work better than before!

THANKS EVERYONE!

---

