---
title: "Upgrades that are on hold Natty?"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2011-03-31
Had these same holds in upgrades for quite a while: 
Should all of them still be on hold?
```
Log complete.
Aptitude 0.6.3: log report
Thu, Mar 31 2011 11:21:18 -0700

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 7 packages, and remove 0 packages.
28.5 MB of disk space will be used
===============================================================================
[HOLD, DEPENDENCIES] banshee-extension-ubuntuonemusicstore
[HOLD] banshee
[HOLD] empathy
[HOLD] empathy-common
[HOLD] gnome-user-guide
[HOLD] libgnome-media0
[HOLD] libubuntuone-1.0-1
[HOLD] nautilus-sendto-empathy
[HOLD] python-ubuntuone
[HOLD] python-webkit
[HOLD] rhythmbox
[HOLD] rhythmbox-plugin-cdrecorder
[HOLD] rhythmbox-plugins
[HOLD] shotwell
[HOLD] yelp
[UPGRADE] chromium-browser 10.0.648.204~r79063-0ubuntu1 -> 10.0.648.204~r79063-0ubuntu2
[UPGRADE] chromium-browser-inspector 10.0.648.204~r79063-0ubuntu1 -> 10.0.648.204~r79063-0ubuntu2
[UPGRADE] chromium-browser-l10n 10.0.648.204~r79063-0ubuntu1 -> 10.0.648.204~r79063-0ubuntu2
[UPGRADE] chromium-codecs-ffmpeg 10.0.648.204~r79063-0ubuntu1 -> 10.0.648.204~r79063-0ubuntu2
[UPGRADE] ia32-libs 20090808ubuntu10 -> 20090808ubuntu11
[UPGRADE] nspluginwrapper 1.2.2-0ubuntu8 -> 1.2.2-0ubuntu9
[UPGRADE] software-center 3.1.24.3 -> 3.1.24.4
```

---

### Post by kerry_s on 2011-03-31
what does it do when you use synaptic?
i don't upgrade mine when something is held, cause it means not everything is there yet. just safer that way.

---

### Post by andrek on 2011-03-31
I don't have any packages held, but yeah - it's quite normal on this kind of development stage.

---

### Post by kerry_s on 2011-03-31
i just checked mine, none held, there all updating now. using synaptic.

---

### Post by garvinrick4 on 2011-03-31
Been using aptitude safe-upgrade since get-go these 15 been hanging around not upgradable
for quite a while. Synaptic's got them on hold also I believe, guess will leave be. Using 
mirror.anl.gov in United States think I am using one up to date. If some users have no holds
something is amiss though.

---

### Post by plucky on 2011-03-31
In Synaptic select **Custom Filters** and then **Upgradable Upstream** and if they are there select upgrade and apply for each one.

This has always worked for me.

Or ```
sudo apt-get install dist-upgrade
``` seems to install the held packages.

Good Luck

---

### Post by mc4man on 2011-03-31
> **garvinrick4 said:**
> Had these same holds in upgrades for quite a while: 
Should all of them still be on hold?


[HOLD, DEPENDENCIES] banshee-extension-ubuntuonemusicstore
[HOLD] banshee
[HOLD] empathy
[HOLD] empathy-common
[HOLD] gnome-user-guide
[HOLD] libgnome-media0
[HOLD] libubuntuone-1.0-1
[HOLD] nautilus-sendto-empathy
[HOLD] python-ubuntuone
[HOLD] python-webkit
[HOLD] rhythmbox
[HOLD] rhythmbox-plugin-cdrecorder
[HOLD] rhythmbox-plugins
[HOLD] shotwell
[HOLD] yelp


Nothing you show there should be 'held'. You actually have some fairly old versions.
Use synaptic and upgrade them 
(or do a fresh beta1 +updates

---

### Post by garvinrick4 on 2011-03-31
All installed and at 0 not upgraded as of beta1
Thank you:

rick@rick-HP:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rick@rick-HP:~$

---

