---
title: "X Window crashes after updates"
date: 2008-05-27
forum: Multimedia Software
---

### Post by jeffimperial on 2008-05-27
For the past weeks, I've been suffering from crashes often. I have NEVER had this problem in Gutsy, and Hardy (at least in the beginning). 

Thinking the updates *help*, I made it a point not to miss out on any of them. But now this; crashing every so often. I don't know what else to put here except that I have an nVidia Geforce 6800 card, I'm using the latest drivers from the repos.


Other details that may be of note:

[LIST=1]
[*]After installing Hardy and selecting the non-free driver, all was well. Video was good, except when I'm at the logon screen. The monitory throbs and waves and flickers like the non-free driver isn't loaded. After logging in, all is well.
[*]After some update last week, the logon screen seemed to have loaded the non-free software already.
[*]I noticed that the nVidia logo was displayed for 2 seconds before the logon screen comes up. Before the updates, the logo wasn't there.
[/LIST]

I don't know where to begin and how to solve this problem. I hope someone could help.

---

### Post by briandu on 2008-05-28
Follow guide as per

[http://ubuntuforums.org/showthread.php?p=5064980#post5064980](http://ubuntuforums.org/showthread.php?p=5064980#post5064980) #msg430 exactly. I had same problem. It is NOT the card but the install.

---

### Post by dgcaste on 2008-05-29
did you install the nvidia glx driver? give me some more info on your computer setup. what update are you talking about, through apt-get? the glx driver has (to the best of my knowledge) to be downloaded manually, and is not automatically installed into the xorg.conf.

---

