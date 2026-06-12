---
title: "[SOLVED] Adobe Flash Player 9 problem"
date: 2008-06-05
forum: Multimedia Software
---

### Post by acron1 on 2008-06-05
Strange problem when I try to view any of the videos on [www.cnet.com](www.cnet.com) the flash player opens a gray box without a picture while you can hear the sound. Now if I navigate away from the page and then hit the back button the flash player plays normally. Firefox 3.0 is the browser and the system is up to date with all the updates. Although this is not a big deal it's annoying non the less.

PS I have removed and reinstalled flash with out success.

Any pointers are greatly appreciated.

---

### Post by FuturePilot on 2008-06-05
Check to make sure you don't have mozilla-plugin-gnash or swfdec-mozilla installed. They can sometimes cause problems like this if you have them installed alongside Adobe's Flash.

---

### Post by acron1 on 2008-06-05
None of the plug-ins you mentioned seem to be installed but here is a screenshot of what is installed:
[IMG]http://i27.tinypic.com/2qdtx91.png[/IMG]

---

### Post by Sef on 2008-06-05
I have a similar problem with Epiphany except nothing happens.  If I click 'From CNET TV' in the upper right corner, a new window opens and it plays.

---

### Post by acron1 on 2008-06-05
> **Sef said:**
> I have a similar problem with Epiphany except nothing happens.  If I click 'From CNET TV' in the upper right corner, a new window opens and it plays.
Thanks for taking the time to respond but I don't see the "from CNRT TV"
in the upper right corner(?).:confused:

---

### Post by acron1 on 2008-06-06
This solved the problem:
sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree

Thanks to reassuringlyoffensive's sticky.:)

---

