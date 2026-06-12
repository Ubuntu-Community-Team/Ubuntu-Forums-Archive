---
title: "Wireless connection problems on Dell Insprion 6400"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by jvb012983 on 2009-05-16
Hi,

I'm pretty new to Ubuntu so please forgive me if I have a lot of followup questions based on any responses to this thread.

Anyway, I can't get my wireless to connect to my router consistently.  The router is setup using WPA2 Personal and AES.  Using the same password on Vista, I can connect without any issues. The SSID is displays when I show the available wireless networks, but everytime I choose it and enter in the password, the blue swhirl just keeps going and then I just get a can't connect to network error.

The weird thing is, if I'm connected wired, then I try to connect to that wireless connection, SOMETIMES, it connects.

I'm totally stumped so any suggestions would be greatly appreciated.

Thanks!

---

### Post by jvb012983 on 2009-05-17
Any ideas? :(

---

### Post by New_aka_fido on 2009-05-23
> **jvb012983 said:**
> Any ideas? :(

Nope, sorry. Have same problem actually.

Tried to play with drivers - b43 and ndiswrapper, but it didn't help.

I red a lil' bit on the net and they say to give a try another connection manager - maybe knetworkmanager from the previous version of distro or wicd, but it seems nobody has a clue where the problem lays exactly. Some blames plasma widget, or whole kde4 while anothers focuses their anger on wifi drivers or even kernel. The roblem is ... widely spread - so to speak.

Will check the above later on and report back.

---

### Post by raymondh on 2009-05-23
> **jvb012983 said:**
> Any ideas? :(

Just an idea to try ....

Using Jaunty, a forum member found success when he installed jaunty backport drivers as he was getting on-off-on-off wifi (dropping).

```
sudo aptitude install linux-backports-modules-jaunty-generic
```

Again, just an idea to try ....

Good luck,

---

### Post by groovomata on 2009-05-23
Hi, I've got an Inspiron 6400 and am having wireless connection issues as well. I currently downgraded to 8.10 from Jaunty to see if that would have and am trying to do some troubleshooting. I'll report back here what I find out. 
All the best,
Erik.

---

### Post by New_aka_fido on 2009-05-23
Ok, I'm back and well... all that reading was worth it, cause I'm writing from jaunty right now. A small workaround does the trick for now.
I'm using b43 Broadcom driver for my dell 1390 mini-wlan wireless. Additionally, I have installed a package from previous distro version (google for: "knetworkmanager_0.7svn864988-0ubuntu8_all.deb download", then install it). Once installed, after you launch it - an icon in the system tray pops up. Press right mouse button on it and choose New connection -> wlan0. A list of available networks in your area will appear. Just select your network and that's it. 

Note: It was done on an unsecured network as this is the only one I've got.

---

### Post by groovomata on 2009-06-01
I am currently typing this note using a wireless connection. After I was unable to get wireless to work with ubuntu 9.04, I got paranoid that my wireless adapter was no longer working and decided to see if it would work if I install Windows Vista on my computer. Lo and behold, it did not, but while digging around in vista, one dialogue box informed me that my card was not enabled, and indeed the little wireless light was not lit in vista. Once I enabled it, wireless worked fine in vista. So then I wiped out vista and re-installed Jaunty and voila! My wireless worked. I very much prefer ubuntu over Windows, but I do wish in all of the different outputs of various commands that I pored over, one of them had simply said that my wireless card was not enabled, afterall, the little wireless light was on the whole time in ubuntu. How was I to know?
Anyways, I'm happy to report that my wireless now works fine!

---

