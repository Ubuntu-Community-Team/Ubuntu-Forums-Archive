---
title: "Youtube plays a few seconds and then quit."
date: 2008-07-27
forum: Multimedia Software
---

### Post by ostkaka on 2008-07-27
Ive have some problems with youtube. When i want to watch a video it plays about 4 seconds and then the video stops. The video continue to download but I can only watch 4 seconds each time. I use ubuntu 8.04, firefox version 3.01 and the latest flashplugin-nonfree is installed. Ive tried to reinstall firefox, java and the flashplugin but the problem remains.:confused:

---

### Post by animaniac on 2008-07-27
i have the same problem, its the flash content, and not only youtube. sometimes it works, sometimes it quits firefox randomly, thank god for the restore previous session option.

---

### Post by ostkaka on 2008-07-27
Okey, but how to solve the problem?

---

### Post by AnonCat on 2008-07-27
Are you using the latest stable version of flash or the latest beta version?  If you're using the beta version uninstall libflashsupport from synaptic or type: 

sudo apt-get remove libflashsupport  

I'd recommend installing the beta of flash 10 as it doesn't crash with the frequency that flash 9 does and doesn't require the libflashsupport library to operate smoothly.  To install the beta do this:

sudo apt-get remove flashplugin-nonfree
sudo apt-get remove libflashsupport

and then download the beta of flashplayer 10, unzip it and copy the file that ends in .so and copy it into the following locations.

/usr/lib/firefox-3.0
/usr/lib/firefox-3.0/plugins

note: you might need to delete a file called xpti.dat in the directory ~/.mozilla/firefox/(randomtext).default  You can find that directory in your home folder if you enable viewing hidden files and directories from the "View" option on the top menu.

---

### Post by AnonCat on 2008-07-27
deleted

---

### Post by ostkaka on 2008-07-27
Ive installed det newest beta av flash (beta 10) and removed the xpci.dat. But the problem remains.. Now i can only watch 2 seconds on youtube :) Any ideas?:confused:

---

### Post by jkhh07 on 2008-07-30
So far the only "workaround" i've found is at the following website. I haven't had any problems for the last 24 hours, but we'll see. If I do i'll post and edit.

_***[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)***_

---

### Post by ostkaka on 2008-07-31
I installed firefox-2.0 instead of the newest version 3.0. Youtube and other flashbased multimedia works without any problem now. Thank you for your help.

/Ostkaka

---

### Post by MillDaKill on 2008-07-31
> **ostkaka said:**
> Ive installed det newest beta av flash (beta 10) and removed the xpci.dat. But the problem remains.. Now i can only watch 2 seconds on youtube :) Any ideas?:confused:

I get this problem when my pulse audio instance dies (which it does a lot).  F you PulseAudio!

---

