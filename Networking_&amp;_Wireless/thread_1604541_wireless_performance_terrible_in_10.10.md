---
title: "wireless performance terrible in 10.10"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by adenewton on 2010-10-24
The performance of my wireless card since doing a clean install of 10.10 yesterday is terrible. At first I thought it was our internet playing up again, but upon using speedtest.net on the same laptop in my windows 7 boot I got my usual speeds of around 18mb.

In 10.10 it struggles to get to 1mb. Yet upload speeds are about the same, also around a 1mb in both 10.10 and windows.

Any ideas? Before I restore my 10.04 from a clonezilla image, as I really can't cope with these speeds.

lshw lists the device as follows:


*-network
       description: Wireless interface
       physical id: 4
       bus info: usb@2:5
       logical name: wlan0
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.35-22-generic firmware=N/A ip=192.168.0.8 link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by adenewton on 2010-10-24
Sorry for the bump, no replies during UK prime time, so hoping the Americans can help me out!! :p

Additional info: 

Ok, lspci -v says:

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 0805
Flags: bus master, fast devsel, latency 0, IRQ 45
I/O ports at 4000 [size=256]
Memory at f0500000 (64-bit, non-prefetchable) [size=4K]
Memory at f0a00000 (64-bit, prefetchable) [size=64K]
[virtual] Expansion ROM at f0a20000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169

and iwconfig says:

wlan0 IEEE 802.11bg ESSID:"SKYXXXXX" 
Mode:Managed Frequency:2.437 GHz Access Point: XX:XX:XX:XX:XX:XX 
Bit Rate=18 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=70/70 Signal level=-30 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I tried:

sudo iwconfig wlan1 rate 54M auto

which just causes it to disconnect, sudo iwconfig wlan1 rate 11M auto works, but still get the same naff speeds.

although iwconfig below says 18mb it pretty much changes with every time the command is put in, 18mb was typically the highest i saw, with the lowest of 7. 

I notice lshw and lspci re giving out different driver numbers?? Don't know if that's related.

---

### Post by Akeldama on 2010-11-03
Unfortunately I've nothing much to add in the way of a solution, but I'm also in the exact same boat as you Adenewton. Dual boot into Win7 and my wireless performance is excellent. 10.10 is abysmal. 10.04 didn't have this issue with the exact same hardware I'm running with 10.10 that now has this problem.

Any suggestions or help would be greatly appreciated! I'm at a stand-still with this for now...

---

### Post by Peter09 on 2010-11-03
There has been some regressions for some wireless cards in Maverick due to a problem with the new kernel. This was resolved (for me) last night when a new Kernel and driver for my card was included in an update.
 
Not saying that this is your problem, but it may be worth checking that you have picked up the upgrade and see if it makes a difference.

---

### Post by Akeldama on 2010-11-03
Peter09, are you using proposed updates? What kernel are you on?

I'm going to now try enabling proposed updates and see what that does for me. I've found the root of the problem though. The Broadcom B43 gives far superior performance; I've been using the STA driver. Now that I finally got the B43 driver to work, I can't get it to stay activated after a reboot.

So, the STA driver works, albeit slowly. I boot with that enabled, switch to the B43 driver and see an immediate increase in wireless performance. However, after a reboot, I have to switch back to the STA then to the B43. That driver tango is killing me. On to the proposed updates...

---

### Post by Akeldama on 2010-11-03
I enabled the proposed updates, updated everything (including going from the 2.6.35-22 kernel to 2.6.35-23). The B43 driver still refuses to stay in use after reboot. "This driver is activated but not in use."

---

### Post by Akeldama on 2010-11-03
Oh, and just for the record, this is my reported wireless card:

Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

I'm also running x64. I did not have this issue at all with 10.04.

---

### Post by TBABill on 2010-11-03
All I can say is I suffered the same fate with the same card. The BCM4312 works great with the STA in Lucid but average to bad in Maverick. I reverted back to 10.04 with no intention of going back to Maverick anytime soon. Since it's the LTS and is new I'll just stand by and watch all the issues get posted. It seems that wireless is a real thorn for 10.10 right now and my other machine with a Ralink won't even connect even though it sees networks.
 
In the same boat as you I'd recommend moving back to 10.04 unless something in 10.10's new configuration or kernel is a critical need for your hardware. It seems to either work flawlessly or horribly without a lot in between. Many users report speed gains but my system bogged down in general use and online compared to 10.04.
 
Sorry I can't help resolve the issue, but a quick search of the forums will show just how many Maverick upgrades and fresh installs are not working well with some wireless cards.

---

### Post by Akeldama on 2010-11-03
TBABill, I'm slowly coming to the same conclusion. 10.04 worked so well for me that I may just backup, wipe this install and revert back to it. It's an LTS like you pointed out, so waiting for 11.04 or even longer wouldn't be a huge deal.

While we are often all tempted by the new and shiny, having the OS just work and not waste my time on what should be trivial is most important.

I may try a fresh install again of 10.10 just to be certain, since I'm going to most likely wipe this one clean, but if I get the same results, then it's back to 10.04.

I'm subscribed to this thread, so if I find any solution to this issue, I'll update.

---

### Post by Akeldama on 2010-11-11
I've come to the final conclusion that in my case this is a power management issue. I did a clean install of 10.10 and saw the very same wireless behavior (as an aside, I did many tests going back to 9.04, 9.10 and 10.04). Just by chance, I happened to be watching an active large file download crawl by at approximately 650Kb/sec, which coincidentally seemed to be the maximum transfer rate, when I noticed that my battery was getting low. I plugged my notebook in and watched as the transfer rate climbed to roughly four times its previous rate!

The B43 drivers, when I could get them to work, did not exhibit this behavior, only the STA drivers. As of now I have not been able to find a solution to this issue. I broke down and ordered an Intel mini pci-e wireless card from a seller on eBay for $4 shipped. Installed it and went on my merry way. It does not have this issue.

With a $4 solution, I just can't be bothered any longer.

---

### Post by Ack! on 2010-11-15
So, had the same problem, and if you can believe it...

sudo chmod a+rx /lib/firmware/b43

fixed for me.

---

### Post by Ack! on 2010-11-15
scratch that... it was temporary.

---

