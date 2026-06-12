---
title: "Ethernet problems (using DD WRT router)"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by hypnoticmonkey on 2013-03-26
Hi all,

I wonder if you could help. I'll give a bit of background to my situation, but networking isn't my forte so there will be tons of crucial info that i miss off, so just let me know what else might be useful.

First of all, I'm planning to get a raspberry pi in the next couple of weeks and I've been preparing for this. Because the R-Pi doesn't have wifi, I've bought a second hand D Link router (DIR 615 D4) and flashed the DD WRT firmware onto it with the intention of setting it up as a repeater. As it happens, I couldn't get the repeater feature working, but I've got it working as a client connecting to the household wifi, and the R-Pi can then connect to it through the ethernet cable as intended, so that's no problem there.

I set up all of this on my laptop, a Samsung netbook dual booting Windows 7 and Ubuntu 12.10. Because I had read somewhere on the DD WRT tutorials that some routers webGUIs work best in Internet Explorer, I booted my netbook into Windows to install DD WRT and get it set up.

Prior to doing any of this, my laptop connecting 100% problem free to both wifi and wired connections in Windows and Ubuntu.

The current state of play:


[LIST]
[*]The new router (D Link) will connect to the wifi network in the house.
[*]When booting in Windows, the laptop can connect to the router via wired ethernet connection and access the internet and other terminals on the network (i.e. the printers webGUI)
[*]When booting in Ubuntu, the computer will connect fine to the wireless network in the house (the same one that D Link is connecting to) but it cannot connect via ethernet cable to D Link. I have tried this with wifi on my laptop turned on, and turned off.
[/LIST]

The problem I get is that it just keeps saying "connecting" and then after a few minutes I get a message saying "Wired network Disconnected" and then it starts again trying to connect.

The one thing that had occured to me, and as I say networking is not my forte so I don't know if this thought is even possible, is that the router recognises the laptop as the one that was plugged in before and assigns IP address and other configurations to it, but those configurations are not compatible with my settings in Ubuntu for one reason or another. As I say, I don't know if that's possible (is a MAC address, for example, static for 1 device in all OSs, or would it change between Windows and Ubuntu?)

Any help at all that you can offer would be greatly appreciated.

---

### Post by Iowan on 2013-03-26
A few things to check (via Network Manager)...
Is the wired networking enabled? 
Is it set to "Connect Automatically"?
What (if any) wired connections are available?

---

### Post by ahallubuntu on 2013-03-26
~

---

