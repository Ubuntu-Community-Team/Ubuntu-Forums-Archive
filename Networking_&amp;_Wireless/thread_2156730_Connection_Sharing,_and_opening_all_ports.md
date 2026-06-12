---
title: "Connection Sharing, and opening all ports"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by Captain Smiley Pants on 2013-06-22
Hello,

Right now I had a set up from my computer to my PS3 allowing the PS3 to connect to the Internet. Basically, the PS3 is in a bad range with my wifi and short of running a long cable through my house, I have a crossover cable long enough to go from my laptop to the PS3 and laptop it's connected to has a much better signal to my wireless hot spot. To get a better idea:

Modem with wireless router ----- Laptop wifi/ethernet card going to ---- PS3

Everything seems to be fine so far. I have assigned a static IP through the PS3, as Ubuntu automatically makes a shared connection to host 10.42.0.1. The PS3's IP is 10.42.0.2

To elaborate on how I'm doing this just so you have an idea, I went to my network icon on the top right, selected **Edit Connections...**, and on the **Wired** tab deleted any other connections and make a new one called *Shared Connection*, when clicked I go to the **IPv4 Settings** and select *Shared to other computers*.

So far everything seems alright. When I run a network test, I get NAT Type 2 (which from other forums posts, seems ideal). When I play Battlefield 3, I can still voice chat and join servers with everyone just fine.

There is one game, though, giving me trouble. Call of Duty Black Ops 2 ... It's not exactly my favorite game but I have some friends I still hop online with. The NAT type in the game tells me that I am in "Moderate". Ideally I need to be in "Open".

Now, something I'm wondering - is there any way to just have all ports open from the connection sharing (where I can put my laptop in a DMZ) or is there anything I can do in Linux to allow port opening? The PS3 is the only other device going through my laptop so I won't need to worry about messing up anyone else's network settings.

I am running Ubuntu 12.04 on a Dell Inspiron 15.

Thanks!

---

### Post by Kujua on 2013-06-24
Do you know what ports the game uses? Then you can add port forwarding rules for those.

---

