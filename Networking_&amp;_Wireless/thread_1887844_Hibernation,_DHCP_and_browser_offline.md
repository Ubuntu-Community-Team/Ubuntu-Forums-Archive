---
title: "Hibernation, DHCP and browser offline"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by johnsd on 2011-11-28
Hi

The other day I accidentally put my machine (Ubuntu 10.04) into hibernation. It would not awaken so I had to restart. There are two issues:


[LIST=1]
[*]I now have to run dhcllient eth0 to get a auto IP number every time I start my PC. I ended up adding the instruction to the /etc/rc.local file to overcome the problem.
[*]Firefox is by default off-line even though I edit via about:config the default browser  off-line settings to false.
[/LIST]
Not a major but would like to know what has happened so it can be rectified.

Many thanks
John

---

### Post by johnsd on 2011-11-30
At the very real risk of sounding rude I wonder if Ubuntu is getting too big. The reason I say this is that I have spent most of my Linux years with Mandriva, Fedora and PCLinux where if you posted something usually within a short time some friendly person would have a helpful suggestion. 

In this forum there often is  just silence ................

---

### Post by johnsd on 2011-12-29
Found another about:config setting:

toolkit.networkmanager.disable 

Set to true.

---

