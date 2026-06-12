---
title: "upgrading from redhat9 to ubuntu64, static name/ip prob"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by VibrantCascade on 2011-07-12
Hi there, I'm trying to replace an old computer with red hat linux 9 with a new one with the latest 64 bit Ubuntu. The problem is I'm connecting the computer to a campus network, and i'm trying to reuse the old computer network name and static ip address so I can secure shell/telnet in. However, the settings seem to be different in ubuntu than red hat. (I'm also new to linux.)

Basically when I set up a computer with red hat it asks me for a computer name during setup and I enter the name.department.institutuion.edu and then it actually prompts me for an ip address and I enter it and it works. Now with Ubuntu it prompted me for a networking name, and it told me it was already in use, (it was the name of the old computer that is no longer on the network, so I suspect it detected there's already a static entry for it in the network) but then it never asked me for the ip address. And going through the network settings for a red hat machine on the network and this new machine I can't seem to find some of the necessary settings to get ubuntu working with the manual settings for the connection. (although dhcp settings work just fine, I just can't use the static ip and name that I want)

I've tried to ifconfig the eth0 to the correct ip address, and it seems to work as the other computers will then return a connection refused instead of a computer not found message. (and the internet stops working for the ubuntu machine when I do this) However when I restart the computer the ip gets reset again and the machine connects to the internet again, but telnet no longer works to the name. And going into the ipv4 settings tab of the network connection, I can set it to manual, but I can't find all of the necessary settings to enter for manual configuration. (Or red hat names them something else or doesn't require some of the settings.) The strange thing is, when I look at the red hat boxes they're using dhcp for their network connection according to the connection settings in the gui, and they still manage to keep their static names and ip address just fine when resetting.

Any ideas? Thanks!

---

