---
title: "Reseting the modem install?"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Mortimer on 2006-06-03
After loading a live cd the dialup connection stopped working in ubuntu. I'm not sure what caused it, but it may have something to do with messing up the hosts for a dialup connection. How can I reset all this along with the modem installation? It's a US Robotics external serial modem. It was working fine before and the modem is fine and works in windows and other installations. The effects are these: I notice a delay from the time the dial tone starts to when it actually starts to dial. And btw, this delay was not there when it was working and is not there when the modem works as it's supposed to in windows and other installations. It does dial after a few seconds and it connects as usual according to the gnome-ppp tray icon, but then it just hangs, no data is sent or received, then soon the connection is lost (tray icon stops, gnome-ppp dialogue appears).

---

### Post by zxee on 2006-06-04
Hi, I have a similar problem with gnome-ppp using a multitech external modem.
Try starting gnome-ppp from the terminal and then you should get more output that hopefully someone can interpret. Also there is a modem monitor applet. You get it by right clicking the panel and selecting add to panel. Modem monitor is in the system & hardware section. That applet works for me sometimes, but sometimes it too just sits there. I think there's a bug in dial up in dapper (I did file one about a month ago but nothing was done about it)  As far as resetting you should be able to use pppconfig to delete your present ppp configuration and then recreate a new one. Hope that helps.

---

### Post by woodtw on 2006-06-04
I have a US robotics modem also.
And I can't get it to work either.
Even pon (pppconfig) will not work.
It dials, connects, then the modem squeals and the connection is dropped.
It worked fine in Breezy, Mepis, Knoppix, Fedora (core 4 and 5) Suse, everything I have tried EXCEPT Dapper.
I have searched for a bug fix and saw where this was reported as a bug, but no answer yet.
I'm going back to fedora.
At least the community there doesn't ingore issues like this.

---

