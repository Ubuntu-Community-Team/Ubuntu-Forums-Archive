---
title: "ath0 can see my router, but can't connect to it"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Big_Lebowski on 2006-06-12
Hi there

I've just installed Ubuntu, and I can't seem to connect to my wireless network. I don't have another way of connecting to the internet on the computer in question (I'm posting from a laptop, running WinXP) so I can't follow any of the solutions that involve downloading packages using Synaptic.

In the network settings manager, there is a wireless connection listed - it says 'The interface ath0 is active'. When I click properties, it identifies the wireless network correctly, but when I type in the WEP key and click okay, a window pops up saying 'Activating interface "ath0" - the progress bar swings back and forth for a while before it gives up.

I've got a feeling the solution is embarrassingly obvious, but I'm a complete noob in these matters and am rather stuck. I've got the correct key type (ASCII), i've deactivated my other two connections (ethernet and modem - both unusable at the moment), and i'm pretty sure my card works in Linux (a 3com 3CRDAG675B 11a/b/g PCI adapter), but I'm having no luck. I can't even browse to my router's IP address, let alone connect to the internet.

I typed in iwconfig, and this came up under ath0:

[FONT="Courier New"]IEEE 802.11g  ESSID:"BTVOYAGER2091-xx"
Mode:Managed  Channel:0  Access Point: Not-Associated
Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=0/3
Retry:off   RTS thr:off   Fragment thr:off [/FONT]   (sorry, can't seem to get rid of these damn smilies!) [FONT="Courier New"]
Encryption key:3839-xxxx-xxxx-xxxx-xxxx-xxxx-35   Security mode:restricted
Power Management:off
Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
Rx invalid nwid:7560  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/FONT]

and under lo, eth0, wifi0 and sit0:

[FONT="Courier New"]no wireless extensions[/FONT]

I don't know if that sheds any light on the issue or not. I'd be most obliged if someone could tell me what obvious thing I've overlooked, or otherwise how I'm to solve this problem.

Thanks in advance

---

### Post by acorn22 on 2006-06-12
Search for a how to on ndiswrapper on google for the program and in here for a great how to (several exsist). I use ndiswrapper and it works well :)

and don't wory about the :0 's becase its caused by the : and the 0 . we just ignore them here.

---

### Post by Big_Lebowski on 2006-06-12
A-ha! Wifi-radar solved my problems. Thanks for your reply though - it may sound a little tragic but I actually had fun learning about ndiswrapper, even though it turns out Ubuntu already has native drivers for my wireless card's chipset.

If anybody else is having a similar problem to me, get wifi-radar: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

It's available as a .deb package and works like a charm.

---

### Post by Big_Lebowski on 2006-06-13
Hmmm. Think I may have been celebrating prematurely. It was working last night, for a few brief, glorious moments, but this morning I'm back to square one. What am I doing wrong?

Wifi Radar reports a good signal from my router, but although it can see the network and claims to be connected to it, I can't get an IP address and when I ping the router I get 'Network is unreachable'.

One thing I find strange, which may or may not be relevant, is that when I do lshw the last line under *-network:1 is:

[FONT="Courier New"]configuration: broadcast=yes driver=new_ath_pci multicast=yes wireless=IEEE 802.11a[/FONT]

That's strange because it's an a/b/g card, and a g router, and yet Wifi Radar claims it's an 802.11b network.

Please help!

---

