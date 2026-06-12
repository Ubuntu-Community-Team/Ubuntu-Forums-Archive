---
title: "trouble with streaming"
date: 2013-01-17
forum: Multimedia Software
---

### Post by debbs on 2013-01-17
Hello to you all!
This is my first thread and although I had Ubuntu running since 2008 I had no updates in my system since then. Two days ago I finally got the 12.04 lts version!!!! Yes quite a history and a roller coaster going from a 8.10 Intrepid Ibex and a firefox 3.0 to a 12.04 Kernel and a firefox 18.0 in 48 hours! It goes without saying that I would end up here asking you enlightened people for some help and a lot of patience. Those are my main dilemmas: 1) Before I had very little or no trouble in streaming videos from different hosts, such as: youtube, vidxden, videoweed, vidbux, muchshare, putlocker, sockshare among others. But since the update only youtube, putlocker and sockshare are working in my case. I'm surprised by the poor performance and maybe something went wrong when jumping from 8.10 to 9.10 to 10.4 to 12.04 Precise. Is there a way to check if something is wrong or missing? No error messages when trying to access those sites. 2) Even after changing the settings in 'appearance' my launcher only re-appears if I press alt+F1 any other way around it besides having it on the left side permanently? 
Thanks in advance to you all!

---

### Post by ManamiVixen on 2013-01-17
Here are some options:

Instal the Hardware Abstraction Layer for Proprietary Steams
sudo apt-get install hal

reinstall the flash plugin
sudo apt-get remove --purge flashplugin-installer && sudo apt-get install flashplugin-installer

---

