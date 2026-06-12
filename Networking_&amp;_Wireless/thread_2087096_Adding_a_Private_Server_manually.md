---
title: "Adding a Private Server manually?"
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by Ragi1992 on 2012-11-22
Is there a program where I can create a VPN or Private Server where I can connect my iPhone to my Lubuntu Desktop as a remote desktop?

This is the app I will be using (pictures taken with my iPhone 4)

The App
[ATTACH]227574[/ATTACH]

Configuration
[ATTACH]227575[/ATTACH]

I would love a server that has some decent security but if that is not possible I may have to go without. I'm sure somebody can help with VNC or VPN. This is pretty much what I am attempting to do:

[http://ubuntuforums.org/showthread.php?t=2086816](http://ubuntuforums.org/showthread.php?t=2086816)

And if anyone knows how to do this without having to create a server that would be even better.

Any help appreciated :)

---

### Post by Groodles on 2012-11-23
Firstly, you'll need to enable VNC services on the Lubuntu machine.  This will allow your iPhone app to connect and see/manipulate the desktop of your machine.  If you only want to do this over a WiFi LAN then that's all you need to do.

If you also want to be able to do this from anywhere in the world (ie over 3G from your iPhone) then you'll be need some way to access the machine securely to allow the VNC connection (probably a VPN because I dont think you can run a session over SSH from an iPhone).

---

