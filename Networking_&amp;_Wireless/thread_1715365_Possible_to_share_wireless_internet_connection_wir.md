---
title: "Possible to share wireless internet connection wirelessly?"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by Nurga on 2011-03-26
I'm running Ubuntu 10.10 on my laptop, our building has a setup where you pay $X/mo for internet access that's MAC filtered.  I recently got a second machine and discovered that we're not allowed to connect more than one machine up without paying for a second MAC address to be added.  Naturally, I asked them to switch my address out for the newer machine but they refused to do so.  It's running Windows 7 with some Dell re-branded Broadcom card that I can't seem to spoof a MAC address on.

So, what I'm trying to do is figure out a way to share my wireless internet connection from my Ubuntu laptop with my Win7 laptop.  Is this possible without purchasing a second wireless card?

---

### Post by Kbloch on 2011-08-01
I'm sort of new to Ubuntu/Linux but I do know a bit about networking. It is not possible to share your wireless connection wirelessly using just one wireless adapter. I can't even get my laptop to do it with two wireless adapters.

I know it's been a couple of months, but here's a few options for ya:
**Option #1**
Using an ethernet cable to share the connection (my choice). A normal ethernet cable (AKA, a **Straight-Through** or **Patch Cable**) should work fine, as newer laptops have ethernet cards that automatically switch between cross-over and straight-through connections. If you have one lying around the office, try using that before buying a cross-over cable. **Cross-Over** cables are kinda rare and harder to come by, but if you have one lying around, try it out first. I use a straight through to share to my Xbox 360, and it works just fine. Once you've procured your ethernet cable, follow the steps [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") to setup your ICS (Internet Connection Sharing) on your Ubuntu machine. In reference to the guide -you'll only be making changes to your ethernet port (wired LAN). So make sure you can browse the internet over your wireless LAN **before** starting the procedure in the guide.

**Option #2**
There are some MAC Spoofing programs available for Windows out there. Here's one that I found a while back on [www.pendrivelinux.com](www.pendrivelinux.com)
[http://www.pendriveapps.com/mac-makeup-change-mac-address/](http://www.pendriveapps.com/mac-makeup-change-mac-address/)
[COLOR="DarkRed"]Don't click the links near the top of the page to download the program, look for the link near the end/bottom of the description titled[/COLOR] "[COLOR="Blue"]HERE[/COLOR]"

**Option #3**
Swapping your network cards between the machines (I'm assuming both PCs are laptops). Of course this presents new problems like: installing the right drivers for each laptop, making sure the cards will fit in either machine, having the skillset to perform this level of hardware work and, most importantly, not voiding your warranty(ies).

Good luck in whichever option you choose and I hope this helps! :popcorn:

Any Mods or more knowledgeable people feel free to correct me, my feelings won't be hurt.

---

