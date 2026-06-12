---
title: "No sound"
date: 2008-08-24
forum: Multimedia Software
---

### Post by SlyReaper on 2008-08-24
It seems ubuntu is unable to detect my sound card (an Asus Xonar DX).  I've plugged my headphones into my computers integrated audio which works, but is a bit ****.  Is there any way I can force ubuntu to use my dedicated sound card?

---

### Post by Yellow Pasque on 2008-08-24
I believe you can use asoundconf to select the default device, but a better idea would be to install ALSA >= 1.0.17, which supports the Xonar (Hardy and Intrepid still have 1.0.16). I've modified the script I wrote for you to use the virtuoso model and attached it. Let me know how it works.

Make sure you go to System -> Administration -> Software Sources and have the first 4 repositories enabled (also make sure the CD is disabled unless you have a slow internet and would prefer to use the older versions of the packages on the CD). When you close that dialog, Ubuntu will ask you to update your software sources. Make sure you don't have Update Manager or Synaptic Package Manager open and click yes/ok to update the package list.

Now save the attached script to your desktop, and:
```
cd ~/Desktop
sudo chmod 777 alsa-1.0.18rc.sh
sudo sh ./alsa-1.0.18rc.sh
```
Reboot for the changes to take effect.

---

