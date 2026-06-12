---
title: "Weirdest **** Ever: Karmic Koala and a Crappy Wireless Card"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Feareilo on 2009-11-03
I've already solved this issue on another thread. I was a douche, sorry.

---

### Post by Feareilo on 2009-11-03
No one?

---

### Post by Menestrello on 2009-11-03
1. really dunno...let me throw some thought:

[LIST]
[*]you had 9.04 and *upgraded* it to 9.10 through Internet => the upgrade screwed your wireless setup
[*]then you installed 9.10 from the Live CD (*clean instal*l), using the Automatic Installation = it automatically took some of your hd space to install itself... and that could be the reason why you now have 2x Karmik Koala Ubuntu...
[/LIST]
But I can't explane the reason why now your *upgraded* installation has a working wireless while the *clean* one doesn't. Maybe check the version of your Network-Manager or Wicd. (for example...to make my 3g connection working on Karmik, I had to downgrade the Network-Manager to the 9.04 version...getting some bug - cannot edit the connection settings - but at least it's working)

2. maybe *gparted* can do what you wish! Download it (sudo apt-get install gparted) on the Ubuntu version you want to keep or boot the computer from the 9.10 Live CD and run it from System->Administration->gparted

Not that great input (since I'm still noob at linux) but I hope it can help you!

---

### Post by Feareilo on 2009-11-03
> **Menestrello said:**
> 1. really dunno...let me throw some thought:

[LIST]
[*]you had 9.04 and *upgraded* it to 9.10 through Internet => the upgrade screwed your wireless setup
[*]then you installed 9.10 from the Live CD (*clean instal*l), using the Automatic Installation = it automatically took some of your hd space to install itself... and that could be the reason why you now have 2x Karmik Koala Ubuntu...
[/LIST]
But I can't explane the reason why now your *upgraded* installation has a working wireless while the *clean* one doesn't. Maybe check the version of your Network-Manager or Wicd. (for example...to make my 3g connection working on Karmik, I had to downgrade the Network-Manager to the 9.04 version...getting some bug - cannot edit the connection settings - but at least it's working)

2. maybe *gparted* can do what you wish! Download it (sudo apt-get install gparted) on the Ubuntu version you want to keep or boot the computer from the 9.10 Live CD and run it from System->Administration->gparted

Not that great input (since I'm still noob at linux) but I hope it can help you!

Thanks a lot for replying, man. The more responses the better. I had thought about just deleting the partition but I don't know if that gets rid of everything I installed with the Live CD.

---

