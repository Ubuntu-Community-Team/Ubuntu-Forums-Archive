---
title: "no flash plugin Firefox"
date: 2011-11-14
forum: Multimedia Software
---

### Post by mick222 on 2011-11-14
up to a couple of days ago Flash was working fine in Firefox.it stopped after some updates installed Chromium works on that but would rather use Firefox In About:\Plugins vlc plugin is selected for flv. files and I don't know where to find the flash plugin which is Installed.
 Ubuntu 11.10

---

### Post by mcgalactor on 2011-11-14
same Problem here.

---

### Post by ajgreeny on 2011-11-14
Try using the flash-aid add-on for firefox which may, as it normally does, sort out all your flash problems.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss)

---

### Post by mick222 on 2011-11-14
> **ajgreeny said:**
> Try using the flash-aid add-on for firefox which may, as it normally does, sort out all your flash problems.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss)

Hi thx installed the add-on disabled the vlc Plugin that firefox wants to use. How do i start it nothing seems to happen after restarting Firefox

---

### Post by BillyBoa on 2011-11-14
From FlashAid you have to disable HWVideo Decode in  tweaking preferences.

Then install flash again.

---

### Post by mick222 on 2011-11-14
Flash aid removed flashplugin-installer I then installed Flashplugin from Synaptic which worked. very strange i had already done the same thing and it didn't work.

---

### Post by sum1nil on 2011-11-14
I've noticed that flash installs from their homepage with apt links. Maybe you can simply reinstall/upgrade flash.

First follow the tutorial at [APTURL]("https://help.ubuntu.com/community/AptURL") to prepare Firefox for apt links.

Go to [Flash Install Page]("http://get.adobe.com/flashplayer/") and in the list pick 'APT for Ubuntu 10.04+'. When Firefox asks for an application to use, open the link with '/usr/bin/apturl', like the tutorial says. Hopefully it will reinstall the package for you and fix the errors.

---

### Post by mick222 on 2011-11-15
I think the problem was i was trying to remove the flashplugin- installer and install flash in one operation. Better to use Synaptic to remove flash then reinstall it from synaptic.

---

### Post by ajgreeny on 2011-11-15
The problem may also be that flash-aid tries to install the beta version of flash by default.  On my hardware the beta version will not work at the present time, though it always has in the past.  I have got everything working by asking flash-aid to install the flash version from the ubuntu repos.

It took me quite a while to figure out, and the problem coincided with me installing get-iplayer 2.80 from a ppa, making me think that this version of get-iplayer was causing the flash failure, which I don't think was so.

---

### Post by mister_playboy on 2011-11-16
The Flash-Aid developer's website domain lapsed a few days ago, which caused the add-on to became temporarily useless since it has to phone home for update checks.

The site appears to be back up and all should be well now, however.

---

