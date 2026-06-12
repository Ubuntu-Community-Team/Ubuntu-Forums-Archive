---
title: "No Sound"
date: 2008-07-05
forum: Multimedia Software
---

### Post by Richpickings on 2008-07-05
I hope I'm posting in the correct forum.

I'm an Ubuntu and Linux newbee but very conversant with Windows. I've Dual booted Ubuntu on my system with Vista and everything seems to be working fine apart from my sound.
 
The sound card I am using is a Creative SB X-FI.

I also don't think my scanner a Canoscan 4400F has been recognised but that is not a problem at the moment.

If anyone can steer me towards the equivalent of 'Device Manager' and assist me with information on how to find and install the correct drivers it would be much appreciated.

---

### Post by sayakb on 2008-07-05
Open a terminal (Applications->Accessories->Terminal)
Type in the following code and press Enter:
```
sudo apt-get install linux-backports-modules-hardy
```If you are **not** running Ubuntu Hardy Heron 8.04, then type:
```
sudo apt-get install linux-backports-modules
```Enter your password, let the command download and install some files.
Now reboot your computer and see if sound works.

---

### Post by sayakb on 2008-07-05
Also, did you see the sticky: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Richpickings on 2008-07-05
The Terminal thing did not work. I'll try reading the sticky.

---

### Post by Richpickings on 2008-07-05
It appears that my sound card is listed as 'Unsupported'. I suppose that means no driver. The sound card is well over a year old, I suppose I'm just unlucky.
Where do I go from here? Do I just wait until someone writes a driver?

---

### Post by Richpickings on 2008-07-06
A bit of self bumping here.... Is it the case that this sound card will not work under Linux?

---

