---
title: "Help - Connection Dropping"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by applesRus on 2010-11-30
I am running the newest version of Ubuntu on my laptop.
The connection randomly seems to massively slow down. After a speed test is run it registers at .05 download and Ubuntu crashes before it gets to upload. I reboot from the crash and it runs fine for a while, then it suddenly does the same thing. The connection is running fine on my Windows 7 desktop, I don't know what is going on.
In transmission the upload speeds are running at ~100kbps though.
If I try downloading a mere 400kb .torrent file it stops half way through, usually at 200-300kb done, downloading at 1.2kbps the entire time.

This is getting very frustrating and I really don't want to go back to Windows. Any help?

---

### Post by Hippytaff on 2010-11-30
Hi an welcome
 
Is it a wireless or ethernet connection? if wireless, what wireless card is it and does this happen with just ubuntu or windows also?

---

### Post by applesRus on 2010-11-30
It is a wireless connection
It is only an Ubuntu problem. When I was running Windows I never had this issue.

As for what the wireless card is, I am unsure. It is integrated into the laptop.
I ran the line of code
lspci -v | less

This is exactly what terminal displayed

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: d2200000-d23fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: d2100000-d21fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
:


My laptop is a Toshiba Satellite L505D-S5983
So I Googled that and stumbled upon this.
[http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=452315](http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=452315)
My Wireless Card is
Realtek 802.11b/g wireless-LAN

Everything else about the Laptop is at that link.
Nothing has been replaced/changed.

Thanks so much for the help

---

### Post by Hippytaff on 2010-12-01
Probably a ralink driver issues though I can't see which one you need without details of the chipset
```

lspci | grep -i net
```
or you may need to blacklist conflicting drivers
[http://ubuntuforums.org/showthread.php?t=1274886&page=11](http://ubuntuforums.org/showthread.php?t=1274886&page=11) see post #107 on this page

---

