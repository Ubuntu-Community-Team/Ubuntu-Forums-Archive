---
title: "What's different in Linux Mint that makes ath_pci work better?"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2009-04-15
My Atheros card (AR5212/AR5213, 168c:0013) works near perfectly in Linux Mint, but it has big issues in Debian Lenny and Ubuntu Intrepid.
In all three distros, ath_pci driver is used (well, in Debian, I had to compile the madwifi driver and blacklist ath5k) and yet it only works well in LM.
In Debian and Ubuntu, the issues are:

[LIST=1]
[*]Wireless connection disconnects a lot
[*]Wireless card gets hot
[*]Even when connected, the download speed is extremely slow most of the time
[*]Once in a while, I get fast download speed for a couple of seconds and it stops
[/LIST]

The download speed is from my eyeballing (ie actual file transfer speed) and speedtest.net.

So my question is what tweak is done in Linux Mint that makes ath_pci driver work so well that is not done in Debian and Ubuntu?

---

### Post by ddrichardson on 2009-04-16
Are they running the same kernels? I have that chipset on an Arch machine that doesn't work before 2.6.26 and had a problem with 2.6.27 and the acer_wmi module.

---

