---
title: "ndiswrapper, kernel update, WG511V2 made in China"
date: 2006-03-29
forum: Networking &amp; Wireless
---

### Post by vinfred on 2006-03-29
Hi,
I'm not in front of my machine, and I'll try to remember as much details as possible. But I'm a newbie to linux ...

Hardware: Sony Vaio GR214MP with 512Mb memory, Netgear WG511V2 made in China
Software: Ubuntu Breezy 5.10

After many reading on forums and wiki, I finally got the WG511V2 card to work with ndiswrapper using the 2080W driver (if I remember correctly the name of that driver) and WEP

A few days ago, I got a notice that a new kernel was available for installation. I accepted the change, then no more wifi :mad: 

ndiswrapper could not even detect the card, although lspci did see it. I tried to install the W2K driver from the Netgear CD on ndiswrapper. the card is detected (hardware present).I don't remember exactly, but I think that as soon as I made modprobe ndiswrapper, I got a complete freeze of the PC.

Since then, as soon as I insert the card, I get the freeze.

I suspected a mismatch between ndiswrapper version and the kernel version. I got the sources for the kernel using synaptic, and the sources for ndiswrapper from sourceforge (as a .tgz filr) in order to rebuild ndiswrapper (maybe I should have got the sources with synaptic).

I got messages with missing files. I saw somewhere that I should start and compile the kernel before being able to rebuild ndiswrapper.

I'm stuck here! ](*,) 

Could someone provide me with a pointer to a complete procedure to rebuild ndiswrapper (including kernel compilation if needed) and a cleaning procedure (to clean faulty previous build attempts)

Just another question: as ndiswrapper seems to be kernel specific, why a new version of ndiswrapper is not distributed along with a new kernel version ?

Thanks in advance
vinfred

---

