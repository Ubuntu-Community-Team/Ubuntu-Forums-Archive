---
title: "fn f3 not working to turn on wireless"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by jackheart on 2010-08-04
Ubuntu 10.4 LTS as a Live CD (intend to dual boot later, testing for now.)
Laptop : Acer Aspire 5251-1513
Wireless card: Atheros AR928X PCI-Express

To turn this on in Windows, I have to do Fn F3. But it does not work in Ubuntu. Most of the other Fn keys work, sound, screen, brightness. Found some relative info, but nothing that might be certain

Now, I know there are some issues with that Artheros card, but I think i need to first get it activated. Thanks!

---

### Post by jackheart on 2010-08-05
Sorry to bump this. Seems like a simple solutions. I tried looking for a command that might enable it but they all only manipulate it. And FN f3 works fine in windows 7.

---

### Post by jackheart on 2010-08-07
Well I found it on my own. Hope this helps anybody if they have the same problem. I just had to type the fallowing in the command line:

sudo ifconfig wlan0 up

---

### Post by CStryker on 2010-08-21
Did you ever get your wireless working? I have the same model and can't seem to get it to work, despite all the searching in the world.

---

### Post by jackheart on 2010-08-22
Yeah, never did get it to work, but I have 2 workarounds:
A: right click on your network manager applet (default on the top right panel of ubuntu 10.4 LTS) and select enable wireless.
B: open terminal and type: sudo ifconfig wlan0 up
of course that command could be different depending on your situation, but that seems to be the typical command in default situations.

---

### Post by CStryker on 2010-08-22
Fair enough, I can get it to show up from ifconfig, but can you actually find any networks and connect to them? I'm having a heck of a time trying to get it to actually work.

---

### Post by jackheart on 2010-08-25
Well I actually mostly use the applet when activating and looking for networks. And yeah, they do show up. Sorry, don't know how much more I can help you without more details....and I am still a beginner with Linux.

---

