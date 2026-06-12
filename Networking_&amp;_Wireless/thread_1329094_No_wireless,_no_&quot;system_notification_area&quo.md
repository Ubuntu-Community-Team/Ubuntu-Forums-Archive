---
title: "No wireless, no &quot;system notification area&quot;?"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by ambrosechapel on 2009-11-17
I don't have a wireless connection on my EeePC. (I'm on 9.10 using Wubi) 

Wireless has worked before, the connection is stored and set to auto-connect. When I boot to windows it works. 

I don't really know what to do -- the Help tells me to click on the network icon in the "System Notification Area", so … what is that? Is it in the top menu bar? Help gives no clue. 

What do I do next? How do I troubleshoot this on Ubuntu?

---

### Post by ambrosechapel on 2009-11-17
Maybe it would help if I could launch the Network Manager manually somehow, as it's not appearing as an icon onscreen?

---

### Post by ambrosechapel on 2009-11-17
OK I've made some progress.

My problem is essentially this:

* when I log in, NetworkManager is running, but nm-applet isn't
* I'm not connected to the wireless networkh
* when I launch nm-applet from the command line, it automatically connects and everything's fine

---

### Post by debsankha on 2009-11-17
> **ambrosechapel said:**
> OK I've made some progress.

My problem is essentially this:

* when I log in, NetworkManager is running, but nm-applet isn't
* I'm not connected to the wireless networkh
* when I launch nm-applet from the command line, it automatically connects and everything's fine

Probably  you should add Notification area to your gnome panel. It should work fine. If it doesn't , add the command 'nm-applet' to the list of startup applications.

---

### Post by ambrosechapel on 2009-11-17
Thanks. I've added mm-applet to the startup applications list and it didn't work. And when I was looking at the list, I saw things like the Bluetooth applet which also used to appear in that area too and have stopped appearing. I might start experimenting with that startup list -- something in it is obviously causing the process to choke. 

Can I put the command somewhere else though, like .profile, and have it run when I log in?

The really annoying thing is, shouldn't NetworkManager be connecting in the background, as it's running? The documentation makes it seem like NM is the real deal and nm-applet is just a handy little widget, but in my case, NM isn't doing anything until nm-applet is launched.

---

### Post by sportsock on 2009-11-22
I have the same problem and can add the following to it.

From the start of upgrading to 9.10 and for some days wireless and notification area worked well, i.e. notification area visible and wireless starting. Suddenly (I believe) the behaviour described have started. I have made several "clean installations" of Ubuntu 9.10 64-bit. On first login everything works fine, on second and further login I have the problem. I have tried different things on the first installation (e.g. nothing, upgrading software, installing drivers and applications) but always the same thing.

Important info: On all reinstallations I keep /home, which is on a separate partition.

Problem in detail: no wireless connection and notification area is just "three vertical dots"

I have a HP dv9000 laptop with Nvidia graphics card

Could anyone hint on possible configuration files on /home that might be modified causing this behaviour?

---

### Post by sportsock on 2009-11-23
Additional information to my last comment:
I made a clean installation of Ubuntu where I placed /home on the same partion as / , i.e. not reusing my old /home. In this case everyting works well. So there must be something in the old /home cusing this. It is a matter of digging through all files and check. Any hints on where to look would be appreciated.

---

