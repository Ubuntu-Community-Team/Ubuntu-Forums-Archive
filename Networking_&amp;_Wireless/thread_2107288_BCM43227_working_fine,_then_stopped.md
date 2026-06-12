---
title: "BCM43227 working fine, then stopped"
date: 2013-01-21
forum: Networking &amp; Wireless
---

### Post by foldered on 2013-01-21
Hi everyone, 
I'm a newbie with linux; I got sick of windows and some problems I was constantly running into with it, so I decided to switch to Ubuntu, having used it a small amount years ago.  During the install, my wireless worked fine, but then it stopped working.  After spending several days scouring the web and trying various solutions, it worked! However, a couple days ago, it just stopped working.  I've looked through some threads and tried some of the suggestions, but they didn't work.  

Thanks to anyone that can help!

EDIT: Somehow solved the problem myself.  From another thread, I ran: 
```
sudo apt-get install linux-headers-generic  
sudo apt-get install --reinstall bcmwl-kernel-source
```
Can anyone let me know how to mark this thread as solved?

---

