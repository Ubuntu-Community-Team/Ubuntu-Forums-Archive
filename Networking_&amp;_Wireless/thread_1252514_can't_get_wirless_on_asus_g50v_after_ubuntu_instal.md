---
title: "can't get wirless on asus g50v after ubuntu install"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by mikegsg9 on 2009-08-28
I have an asus g50v and the wireless works when i use the ubuntu live cd, but after I install ubuntu I cant even view any wireless networks. The wireless tab is grayed out. I have a toggle switch for wireless on my keyboard and thought that'd be a problem. I have to press fn and the hot key for wireless and nothing happens, no display is shown, however the hotkeys for volume, and brightness and a few others work. I think this may be the problem, but i'm not sure. I'm new to linux as well so i'm not sure what other information would help so far. Any help is appreciated.

---

### Post by mikewhatever on 2009-08-31
You can try turning the wireless on with **sudo ifconfig wlan0 up**. If you get a message that wlan0 doesn't exist, try eth1 instead.

---

### Post by mikegsg9 on 2009-09-06
thanks for the response, but I tried it and nothing happened. Theres got to be a way to make it work if it works off the live cd, is there anyway that ubuntu installed drivers automatically for my card, and I could delete them and install a driver with Ndiswrapper? Ive tried using Ndiswrapper and installing the drivers from the laptops driver cd for windows, but it sais it can't find the device after the drivers are installed.

---

