---
title: "Cannot seem to get pulseaudio to unmute in pulseaudio volume cotrol"
date: 2009-11-20
forum: Multimedia Software
---

### Post by garvinrick4 on 2009-11-20
New Laptop fresh install of 9.10 and cannot seem to get the pulseaudio volume control to unmute. Any help would be appreciated driving me nuts.

HP G71-340US  6600 dual processor  intel chipset  sound card Intel 82801I (ich9 fAMILY)

---

### Post by garvinrick4 on 2009-11-21
Turns out there were a lot of people in Karmic with the sound issues
I just loaded a new laptop so it was my first sound issue. You cannot mute or unmute in pulse audio volume control if it is on mute
It just means you have got a problem. A software problem it seems most all the time. Had to include backports in repositories. Then there were a ton of fixes out there for sound issues. A couple of them mentioned the mute in the pulseaudio. Any way the only fix was
keep trying different ones that would not damage. Hopefully. Would
try a edit, save the old one and put it back the way it was when edit did not work. Finally one worked, just about jumped out of my chair the audio was full blast and when I logged off and back on it
shocked me. Sure feels good when they go right. 12 hrs. of frustration. Found best ones Googling. Lot of others fixed peoples machines so there is no common ground to work with. Drivers,cards and kernel that says it all. Good luck and have a nice day.

---

### Post by gordong11 on 2009-11-21
Possiblt goto software center and download pulseaudio server and manager? see if that will control your mute better.

---

### Post by garvinrick4 on 2009-11-30
Here is where it worked for me on every clean install.
Every time it worked.



[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

