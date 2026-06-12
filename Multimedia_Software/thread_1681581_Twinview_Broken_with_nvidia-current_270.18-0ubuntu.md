---
title: "Twinview Broken with nvidia-current 270.18-0ubuntu1~lucid~xup1"
date: 2011-02-04
forum: Multimedia Software
---

### Post by derrek on 2011-02-04
After running system update my dual monitor (twinview) setup stopped working.

About my system:
10.04 LTS 64 bit
Nvidia GeForce GT 220

I believe this change ruined it: nvidia-current(260.19.29-0ubuntu1~xup-lucid4, 270.18-0ubuntu1~lucid~xup1)

I've tried reworking NVIDEA X Server Settings with no success.  I've tried some manual manipulation of xorg.conf with no success.

I can't seem to figure out how to downgrade back to nvidia-current(260.19.29-0ubuntu1~xup-lucid4). 

Any help would be appreciated!

---

### Post by derrek on 2011-02-04
I was able to 'downgrade' back to older nvidea drivers by using this guys repository: [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html) 

That allows me to use both monitors in twin view.  

The 270.18 driver is buggy for my setup...

If anyone is to investigate I downgraded to 260.19.36 and that got my dual monitor twin view setup working again.

---

