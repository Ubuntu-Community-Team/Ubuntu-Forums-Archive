---
title: "Can't Play YouTube Videos in Ubuntu 9.10"
date: 2010-06-12
forum: Multimedia Software
---

### Post by lisar915 on 2010-06-12
Hi everyone,

I just upgraded to Ubuntu 9.10.  Now I can't play YouTube videos using both Firefox and the Epiphany browsers.  I get an error message saying "you need to upgrade your Adobe flash player to watch this video. However, when I try to install it, I get a message saying I already have the current Adobe flash player installed.  

Any suggestions or ideas?  

Thanks.
Lisa

---

### Post by lovinglinux on 2010-06-12
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by lisar915 on 2010-06-12
Hi, 

Thanks for getting back to me. 

I ended up doing the following:

First, I uninstalled flashplayer from the synaptic package manager.  Then, I went to the Adobe site to download the .deb file.  When I tried installing the .deb file, I got an error message saying I already have a newer version of flashplayer installed.  

So then, I used the terminal to install the non-free flashplayer plugin, which finally worked.

---

