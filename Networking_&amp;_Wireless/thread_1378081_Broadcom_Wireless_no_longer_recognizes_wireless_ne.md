---
title: "Broadcom Wireless no longer recognizes wireless networks"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by cyqotiq on 2010-01-11
I've seen many threads that are similar to my problem, but none of them seem to have this exact issue.

I've been running Karmic since it was officially released on my Dell Studio 17 (specs are in my signature) with a Broadcom wireless half mini wireless card.  When I installed Karmic, it gave me the option to install proprietary drivers for my video card as well as 2 Broadcom drivers, STA and one of the BC43 drivers.  I installed all of these, and the only problems I had were with the audio.  I spent a few days troubleshooting the audio and finally got PulseAudio set up for my card.

Almost 3 months later, I was making use of my wireless network at home, as I had done plenty of times over the previous 3 months, when I closed the lid (thus putting the computer into sleep mode) and took it to the hospital to stay over night with my fiancée after her surgery.  When I got to the hospital, I couldn't get their network to show up.  Network Manager didn't even recognize the network.  We had also brought my fiancée's laptop (same machine with a slightly less powerful CPU and only 4 GB of RAM).  She is running Windows 7, which detected the hospital's network with no problems.

After trying to ad-hoc the hospital network with no success, I finally just gave up and played Sudoku and toyed with some graphics stuff in GIMP until we came home.  Upon returning home, however, I was shocked that my card didn't even detect our home network.

I have been unsuccessful for the past 3 days in getting Network Manager to identify our wireless network.  The wired network connects without issue and I am able to make use of a USB Belkin adapter, which identifies all 7 of the various wireless networks in my neighborhood, including our home network.

While I would be able to simply carry my Belkin adapter with me in order to make use of wireless networks, I would really like to solve this problem with my Broadcom adapter.  I've gone through the Ubuntu Wireless Network Troubleshooting guide, but I still can't get it to work.

Output of lshw -C network:
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth2
       version: 01
       serial: 0c:ee:e6:9d:14:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f2200000-f2203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:20:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:da:37:74
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:32 ioport:4000(size=256) memory:f2004000-f2004fff(prefetchable) memory:f2000000-f2003fff(prefetchable) memory:f2020000-f203ffff(prefetchable)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan4
       serial: 00:11:50:a4:8d:1e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.5 multicast=yes wireless=IEEE 802.11bg
```

Output of 'lsmod | grep wl'
```
wl                   1277380  0 
lib80211                7812  2 lib80211_crypt_tkip,wl
```

Network Manager still recognizes my Broadcom card, but my card just doesn't recognize any networks.  I tried adding my home network as a hidden network, but it just continuously prompts me for the network key.  I enter the right key and it does the spinny "I'm searching" thing on the notify icon before prompting me again for the key.

So why would my card just suddenly stop recognizing networks, and how might I go about fixing this issue?

TIA for any help.

---

### Post by cyqotiq on 2010-01-11
With all of the wireless problems floating around - a very common problem with Broadcom, it seems - is there no one who has the slightest idea of where I might even start to look for an answer?

I would hate to have to reinstall the entire OS and hope the audio and network both work with little to no trouble.

---

### Post by changingstate on 2010-01-11
Have you seen this? : [http://ubuntuforums.org/showthread.php?t=1308989&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=1308989&highlight=BCM4312)

Hardly ideal, but if you're in a hurry..

This looks like it will assist too.. : [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by cyqotiq on 2010-01-11
First, thank you for a positive response.  I hadn't seen that post before, but I'm not sure how applicable it would be to my situation.  It's worth a shot, though.  I'll have to grab a Live USB image to test, as I installed from the Karmic AMD64 DVD and can't seem to locate the bcmwl-kernel-source package anywhere on the disc.

Meanwhile, if anyone else has any information, I would **LOVE** to hear it.

---

### Post by cyqotiq on 2010-01-11
As a bit of background info on what I've tried, I've uninstalled (e.g. "deactivated") both the BC43 fwCutter (or something to that effect) and the STA drivers for the Broadcom chipsets.  About half the time, the fwcutter driver doesn't even show up in the list, but the STA driver is always there.  No matter how many times I deactivate / reactivate these drivers, I can't get anything to change.

My system recognizes my card and shows that the driver (which is 'wl0' instead of 'bc43') is present and loaded.  The card itself is reported to be deactivated and no networks are showing up as available in Network Manager.

---

### Post by PRC09 on 2010-01-12
Just a wild guess but during your travels did you manage to physically turn off the wireless some how.A switch or key combination maybe.I did suffer this embarasment myself once and thats the first thing I check now, especially when it was working before the travel and not after...

---

### Post by efflandt on 2010-01-12
It could be easy to accidentally deactivate wireless on a new Dell.  I know that for a 1545 I recently set up, the function of the Fn key is reversed from most computers.  You have to press the Fn key for normal function keys (like Fn+F2) and NOT press Fn for special functions of the function keys (like turning wireless off or on).  So if you accidentally press a function key without also pressing Fn, it might do something different than you normally expect.

---

### Post by cyqotiq on 2010-01-12
I tried using the Fn + F2 (Wireless toggle) just to make sure I hadn't done this, because I do recall trying to dim the brightness of the screen that first night at the hospital.  Unfortunately, pressing the key combo simply disconnected the Belkin USB adapter.  Pressing again reconnected the Belkin adapter, but the on-board Broadcom adapter still claims to be disconnected.

I did notice, however, that while the wireless was disabled (via the first Fn+F2 key combo) the Belkin adapter and the Broadcom adapter were both listed as Disconnected and the similar appearances made me curious.  My system lists the driver for my Broadcom (which is 'wl0' instead of 'b43') as being available and loaded.  Somewhere during all of my console troubleshooting, I saw a place where it listed my actual adapter as being disabled.  I'll go looking for that again to see if I can make sense of that.  Meanwhile, I did notice that lsmod lists 'wl' as being used by 0 devices.  Does this mean anything to anyone?

---

### Post by cyqotiq on 2010-01-12
> **efflandt said:**
> It could be easy to accidentally deactivate wireless on a new Dell.  I know that for a 1545 I recently set up, the function of the Fn key is reversed from most computers.  You have to press the Fn key for normal function keys (like Fn+F2) and NOT press Fn for special functions of the function keys (like turning wireless off or on).  So if you accidentally press a function key without also pressing Fn, it might do something different than you normally expect.

I found this out very quickly, actually.  One of my first tasks when I received the machine was to go into the BIOS and disable this so that my Fn key acted the way it *should* act (IMHO).

---

