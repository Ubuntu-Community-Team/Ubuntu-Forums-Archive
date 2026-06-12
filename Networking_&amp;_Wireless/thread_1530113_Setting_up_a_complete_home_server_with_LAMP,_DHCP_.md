---
title: "Setting up a complete home server with LAMP, DHCP and DNS."
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by ManiDhillon on 2010-07-13
Okay! Friends I will explain everything as good as I can and I hope I'll be able to get some solutions soon.

I have this setup:

1. A Laptop-1 with Ubuntu 10.04 x86-64 with LAMP, DHCP(dhcp3) and DNS(bind9) server installed with wireless connectivity.
2. A Laptop-2 with Windows XP/Xubuntu 10.04 x86 having wireless connectivity option.
3. A Desktop with Xubuntu 10.04 x86 having an ethernet and also a wireless card.
4. A Nokia mobile having wireless connectivity.
5. Though I also have a Modem/Router with wired and wireless connectivity, but I don't want to use that in this setup.

What I did:

1. I have created a new wireless ad-hoc network in Laptop-1 on "wlan0".
2. This network is automatically assigned ip 10.42.43.1.
3. I can connect my Phone, Laptop-2 and Desktop to this new network and they are automatically assigned the next available ips.
4. When in any of the connected devices' browser I enter the ip 10.42.43.1, I can see my Apache homepage.

What I want:

1. Correctly setting the DHCP server to assign the range 10.0.0.5 - 10.0.0.20 and to assign the ip 10.0.0.2 to my server Laptop-1.
2. To correctly setup DNS server so that the connected devices can use a human readable address(example.org) to open my homepage.

I will be satisfied if you can provide detailed instruction or brief good pointing.

P.S: I've already googled it and have tried the ubuntugeek and howtoforge tutorials but they didn't help.

Edit: I can set this up with my Router as connection gateway for all connecting devices but I don't want to use that. Instead I want to use my wi-fi card for that purpose.

---

