---
title: "Strange bevaviours after a dist-upgrade"
date: 2010-12-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2010-12-23
I'm using Ubuntu 11.04 to test the packages and report bugs. After my sound issue was solved I have configured my system to my standard configuration, made a reboot and a checkup if all is working. Until yesterday I had no problems but today after the next apt-get dist-upgrade their are some new behaviours:

- I can't copy text between applications (if both applications are opened).

- After starting of applications like Pidgin, XChat or Skype their are no tray icons in lxpanel.

- Flash applications don't work (tested in firefox, the plugin Shockwave Flash 10.3 d162 is activated). I can hear the sound but I don't see any output.

- The dependencies of k3b are blown up so that k3b can't be installed anymore (well, I think this will be fixed automatically in a few hours).


I would post this on launchpad but the reaction of generic problems is very slow. Maybe somebody have an idea which component is doing the problems (if this is really a problem from the last dist-upgrade).

---

### Post by cariboo on 2010-12-23
When you run into problems with natty, you should check the Natty Testing and Discussion sub-forum, before creating bug reports, as someone else may have created the exact same bug already.

Oh yeah, moved. :)

---

### Post by Sworddragon on 2010-12-23
I have made a look in the Main Support Categories to see which subforum matches the best for this problem. But it's good that here is a natty subforum for such things :)

Edit: After the next apt-get update, apt-get dist-upgrade and a reboot all is working now except the flashplayer. Now the flashplayer crashes if an application starts. A new profile of firefox or an older version of the flashplayer doesn't solve the problem.

---

### Post by efflandt on 2010-12-23
PS: Nevermind, they just fixed it with some updates.

---

### Post by ronacc on 2010-12-23
@Sworddragon welcome to the dev forum and the joys of testing :p  if you are new to the forum read the stickies there is good info there .

---

### Post by Sworddragon on 2010-12-24
Flash is now working too so all is fixed now.

---

