---
title: "Wicd Hangs on Wireless &quot;Obtaining IP Address&quot;"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by Literati on 2009-06-21
Hi there fresh install of Ubuntu 9.04 here. From the moment I installed to now, here's what I've done...

1. Remove network-manager and gnome-network-manager
2. Install wicd
3. Follow this guide to get my Broadcom 4318 running ([link]("http://ubuntuforums.org/showthread.php?t=766560")) (And it is running)
4. Try to connect wireless via wicd.

Then upon doing that, it gets stuck at Obtaining IP Address. When I'm hooked up via Ethernet, it connects fine with Wicd (In the wired connection of course) and it can get it's IP Address.

What gives?

---

### Post by cariboo on 2009-06-21
This might be a dumb question, but do you have wireless to get an ip address via dhcp?

---

### Post by Literati on 2009-06-21
Hehe. Yes, I do. We have a linksys 300N something or other router. And before this laptop had Ubuntu, it was hooked up wirelessly with Windows. (Also, we have another windows box in the house that is done wirelessly, and is still working now) :)

---

### Post by Literati on 2009-06-21
Anyone? I feel like I'm on the BRINK of getting internet to work :P

---

### Post by Literati on 2009-06-22
*pokes thread*

---

### Post by Literati on 2009-06-22
Okay so I've figure out that it's just WEP and WPA that it doesn't like. If I remove all security from my access point it connects A-OK. But as soon as I put WEP or WPA on, it hangs at "Obtaining IP Address" :( 

Why?

EDIT: Nevermind. If I use a WEP Hex Key instead of a passphrase it seems to work. Odd, but at least it's up and I have some sort of security :)

---

