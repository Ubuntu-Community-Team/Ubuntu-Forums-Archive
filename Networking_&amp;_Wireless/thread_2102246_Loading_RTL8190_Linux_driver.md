---
title: "Loading RTL8190 Linux driver"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by Marsden on 2013-01-06
There are a couple threads related to this card/driver, but none of them seem to address the situation I'm in.

I've found what is allegedly a set of Linux driver files for the RTL8190 card, and even subsequently an updated version of it at [http://www.wikidevi.com/files/Realtek/RTL8190/](http://www.wikidevi.com/files/Realtek/RTL8190/), but due I'm sure to my own ignorance I can't make use of them. (One of the aforementioned threads on this card suggested using the ndiswrapper utility and the Windows driver, but why do that if there's an honest to goodness Linux driver available?)

The Linux driver files come with a README and a Makefile file, which make it sound like the whole thing should be easy ... but they don't work for me. Separately I've found suggestions that you need to be in a very particular directory before you run 'make,' but I couldn't even find that exact directory on my computer, so I thought I'd toss out what I hope will be an easy question to the community: how do I create the drivers using the Makefile, and then how do I get them loaded and usable?

Thanks for any help provided.

My dope:

1. Desktop with ASUS P8Z77-V LX motherboard and Intel i5-3570 processor
2. Realtek Semiconductor Co., Ltd. RTL8190 802.11n
3. eth0 and lo: no wireless extensions. No wlan0 recognized.
4. Unclear what wireless module in use
5. Unclear what kernel boot messages apply to wifi card, if any
6.   *-network UNCLAIMED
       description: Network controller
       product: RTL8190 802.11n Wireless LAN
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:d000(size=256) memory:f7c00000-f7c00fff
7. No wlan0 networks
8. Ubuntu 12.10
9. 3.5.0-21-generic x86_64
10. Crashed my system; thanks for that! ;-)

---

### Post by Marsden on 2013-01-07
Update:

1) I emailed RealTek regarding getting an updated Linux 64 driver; no response yet.

2) Tried to use various Windows drivers with the ndiswrapper tool, but the ndiswrapper tool seems to have fallen apart for my version of Ubuntu: I keep getting 'module not found' errors, and while some of the checks for whether ndiswrapper has properly loaded the drivers indicate that it has, they do not work.

3) Found more than I ever cared to know about Makefiles. Apparently the file I had been trying to use was for an earlier kernel, and does not work with 3.5.

---

### Post by Marsden on 2013-01-08
All right, I threw in the towel and replaced the wireless card.

My recommendation for others: if you can't be sure the wifi card on a new computer will be Linux compliant, get your own card.

---

