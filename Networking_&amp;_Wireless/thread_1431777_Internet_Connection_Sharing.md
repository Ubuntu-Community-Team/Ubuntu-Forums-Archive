---
title: "Internet Connection Sharing"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by RedSpade08 on 2010-03-17
I have two computers.
This one (my laptop) has Karmic.
My Desktop has Winblows XP.
The Desktop has a usb wireless network adapter (Cisco Linksys Model Number WUSB54GC) which seems to be unsupported for linux (and usually pulls less than 10 KB/s under windows)

I would like to be able to share my wireless connection from my laptop to my dektop. I currently share it with my XBOX 360 in order to connect to XBOX Live (done through the network manager in ipv4 settings) but the same does not work with another pc.

I'm looking to replace XP with gentoo but must have an internet connection. Any ideas that wouldn't require new hardware?

---

### Post by RedSpade08 on 2010-03-22
bump

---

### Post by Iowan on 2010-03-23
Does laptop have wired and wireless connection? Is laptop wired to internet and you want to share via wireless? [Here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") is a help page for going that direction.

---

### Post by RedSpade08 on 2010-03-23
thanks for the reply.

actually laptop has wireless and I'm trying to share via ethernet

---

### Post by Iowan on 2010-03-23
[This ]("https://help.ubuntu.com/community/Internet/ConnectionSharing") one may be more useful, then. You'll need to replace **eth0** with **wlan0** or whatever your interface is called.

---

### Post by danger pigeon on 2010-03-24
Does anyone know of a way to do this so the connection sharing can be up all the time with both the xbox and computer having access to the internet? For some reason when i "share" the connection to get my xbox online, it works, but then i cant use the internet on the computer.  It doesn't seem to be sharing anything, either one port gets all the internet access or the other does. I have scripts that automate this process a little but it's still annoying to have to run a script every time i turn on my xbox and then another one when i'm done playing. Any suggestions?

---

### Post by Iowan on 2010-03-24
That sounds more like "giving" than sharing ;)
If you use Karmic, have you tried the "new" [Ubuntu 9.10 Method]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%209.10%20Method")

---

### Post by danger pigeon on 2010-03-24
i haven't yet. I'm still running 9.04 and didn't really want to upgrade just yet. But i guess i'll have to give it a shot and see if it works.

---

### Post by Iowan on 2010-03-24
I'll try to review the ICS help page. I suspect there's a configuration error somewhere - I doubt it's *supposed* to work as you've described...

---

### Post by RedSpade08 on 2010-03-28
thanks...the "Ubuntu 9.10 Method" was what I used to share to the 360, but isn't working on my other pc...may just be a hardware problem on there (it's about 5 years old and i didn't exactly take very good care of it the last time I had it)

thank you for the help though

---

### Post by danger pigeon on 2010-03-29
Just to update i could never get this to work correctly. The ubuntu 9.10 method would allow the computer to stay connected to the internet while the connection was bridged, but the xbox could never connect to live. O well its not the end of the world i guess, but it would be nice if it was as simple as it is in windows to share a connection.

---

