---
title: "Replacement for Network Manager in Kubuntu"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by devanson on 2009-07-24
Hi. All. I am a great fan of Ubuntu... My dell xps laptop comes with the inbuilt Vista.. I removed vista and installed ubuntu... And doing all my stuffs in ubuntu only.. Even my projects too..

Recently I seen Kubuntu live cd and impressed by its new KDE 4 desktop... So I transferred to it.. I did a clean install...

But the problem is I am not able to connecct to internet in Kubuntu's Network Manager..

Currently I am staying in on-campus and they have lots of security to their internet connection.. I am able to connect easily in Ubuntu.. (with the help of 802.1x security tab).. but not able to find it in Kubuntu's NW manager...

Need a good suggestion from you... Friends... Anyway I am happy with Gnome's interface also....

---

### Post by 67GTA on 2009-07-24
The Kubuntu manager won't connect to encrypted connections right now(bug). Try wicd. It's in the repos. ```
sudo apt-get wicd
``` You can get the downloaded package in /var/cache/apt/archives onced you have installed it in Ubuntu. You will need the wicd package plus

```
python-gtk python-glade2 python-cairo libglade2-0
``` to install it in Kubuntu without a connection. Just copy these to your Kubuntu install for installation.

---

### Post by 67GTA on 2009-07-24
I forgot to mention that you have to manually remove ```
networkmanager
``` before installing wicd.

---

### Post by devanson on 2009-07-26
Oh.. Thank you Friend..

---

