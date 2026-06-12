---
title: "Issue with Dell Wireless-n 1250 Half Mini Card"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by Abyss Darkstar on 2010-11-26
After installing the Broadcom STA driver from the Proprietary drivers selection I was able to connect to my wireless network, however the connection repeatedly drops. After some investigation, I found that the broadcom drivers aren't actually being loaded properly... according to lspci the kernal driver and modules that are being used by the card are wl. also the if shows up as eth1, not as a wlan0 if. I have no idea if these are the cause of the d/cs, however even if they are not, I'm sure they are incorrect.Also a lsmod | grep "wlan" search comes up with nothing... so i can guess from this that no wireless module is being loaded...

I am running Ubuntu 10.04.1 LTS, Kernel 2.6.32-26-generic i686.

Any ideas, help or whatever would be appreciated. Also, if anyone knows a way to specify which kernel driver and modules a piece of hardware uses it may well be very handy.
Will post new/additional information as descovered/requested.

Thanks in advance

---

### Post by chili555 on 2010-11-26
> I'm sure they are incorrect.Why?

I have a laptop whose interface is wlan0 and another which is eth1. I have been working with a case where the interface is ra0. I don't think the disconnects have the slightest to do with the name of the interface. Let's see what the kernel has to say about it:```
dmesg | grep -e wl -e eth
```Disconnects could also have to do with radio frequency interference, transmit power in the router or your distance from the router or maybe other reasons.> Also, if anyone knows a way to specify which kernel driver and modules a piece of hardware uses it may well be very handy.It is easy to force a device to *load* another driver, however it's very difficult and usually impossible to get the wrong driver to actually operate and connect.

---

### Post by Abyss Darkstar on 2010-11-27
I believe the card is being incorrectly detected by the kernel because iwlist scan reports eth1 as not supporting scanning, and iwconfig reports that eth1 has no wireless extensions...

dmesg | grep -e wl -e eth

```
[    0.000000]   AMD AuthenticAMD
[    0.000000]   DC000-FFFFF write-through
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000172] using mwait in idle threads.
[    0.000182] ... bit width:              48
[    0.628860] thermal LNXTHERM:01: registered as thermal_zone0
[    0.629481] thermal LNXTHERM:02: registered as thermal_zone1
[    0.679302] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.679585] device-mapper: multipath: version 1.1.0 loaded
[    0.679588] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.998887] Write protecting the kernel text: 4684k
[    0.998917] Write protecting the kernel read-only data: 1840k
[    1.054328] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.055328] eth0: RTL8168d/8111d at 0xf80dc000, f0:4d:a2:4c:df:fd, XID 081000c0 IRQ 34
[    1.393057] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.187086] EXT4-fs (sda4): mounted filesystem with ordered data mode
[   12.566428] sdhci-pci 0000:07:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[   12.571962] lib80211_crypt: registered algorithm 'NULL'
[   12.713735] [fglrx] module loaded - fglrx 8.79.4 [Oct 26 2010] with 1 minors
[   12.746100] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.746111] wl 0000:04:00.0: setting latency timer to 64
[   12.770486] lib80211_crypt: registered algorithm 'TKIP'
[   12.770617] eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.60.48.36 
[   13.140624] type=1505 audit(1290852717.977:11):  operation="profile_load" pid=904 name="/usr/bin/evince-thumbnailer"
[   14.165276] r8169: eth0: link down
[   14.165478] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.140945] eth1: no IPv6 routers present
[   29.822941] [fglrx] ATIF platform detected with notification ID: 0x81
[   30.275694] [fglrx] Firegl kernel thread PID: 1369
```Also, I am often contracted by a network security analyst to do network audits, and one of the things i am required to do during these audits is check WPA strengths by attempting to crack them with aircrack-ng. I had no issue with this on my last laptop, however airmon-ng is reporting that interface eth1 has an unknown chipset. this is another reason why i believe the card has not been recognised by the kernel properly...

As for other reasons for the DCs, I have another ubuntu install on my desktop, with an a card using ath9k drivers, and it has no issue at all with the same network... and while i'm trying to configure and set my laptop up it is sat right next to my desktop... 

Again, Thanks in advance

---

### Post by chili555 on 2010-11-27
Here is what I have learned so far. The driver *wl* is correct for your device, I believe. If you run the command:```
lspci -nn
```I believe you will find the pci.id is 14e4:4353. Checking the module aliases in *wl* shows:```
modinfo wl | grep 4353
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4353[/COLOR]sv*sd*bc*sc*i*
```The other Broadcom driver *b43* and *ssb* show no matching pci.id. While we might get b43/ssb to load, I am quite skeptical we could get it to drive.

What is more compelling is here: [http://www.backtrack-linux.org/forums/beginners-forum/1723-bt4-boot-cd-dell-1764-dell-1520-wireless-card.html](http://www.backtrack-linux.org/forums/beginners-forum/1723-bt4-boot-cd-dell-1764-dell-1520-wireless-card.html)> A reply from DELL mentions the following:

",,,,,,,the Wireless Card installed in your system is not capable of Monitor and Insert/ Injection Modes
in Networking."For your information Backtrack in an Ubuntu variant that is aimed at security auditing.

It seems that if airmon-ng is required then the Broadcom 4353 is not the card for you.

---

### Post by Abyss Darkstar on 2010-11-27
Thanks for the responses. Not what I wanted to hear, but that's not your fault. Looks like I'll have to invest in a USB wireless Dongle that is supported before my next contract.

I have used Backtrack in the past, however I prefer the "emptiness" of a fresh, proper Ubuntu install, so I can configure it how I want from the start, without having to re-configure Backtrack and risk breaking some of the installed software, most of which falls outside what I usually have to use.

---

### Post by chili555 on 2010-11-27
If you noticed in my link, Backtrack has a Wireless HCL thread; I'd think that's a good place to start.

This reminds me of one of my favorite questions on this forum which I've seen many times. It's approximately, "I read that my wireless card doesn't support injection and airmon. So what can I do to do it anyway?"

---

### Post by zdenal on 2010-12-02
I had same problems with Broadcom driver on Lucid and Maverick.

In my post

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

I summarize some facts so you can check

a) If your Broadcom card is supported by the wl.ko driver
b) Use step by step HowTo to try fix your wireless problem

Hope this helps..

---

