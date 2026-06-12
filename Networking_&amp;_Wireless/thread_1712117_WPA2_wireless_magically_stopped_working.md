---
title: "WPA2 wireless magically stopped working"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by Mila on 2011-03-22
And yes, I do mean magically.

Yesterday I upgrade from Ubuntu 10.04 to 10.10. Everything went perfectly, no hiccups or glitches. I did a clean install of 10.10, updated, and then added the following applications/packages: Chromium, Thunderbird, Pidgin, Kate, vim, ruby1.8, rubygems1.8, ri, ruby1.9.1, ri1.9.1, and update-alternatives. (Plus some gems.)

My wireless worked fine. It is a WPA2 Personal encrypted network, not hidden, with a 24-character password. I spent some time browsing the internet when suddenly, *boom* my wireless disconnects. No matter how many times I reselect the network from the list of available wireless networks, it just does it's little whirly "trying to connect" bit and then goes back to Could Not Connect. I also tried adding a new connection to the network manager but had no luck there either (same results).

The router sits next to my laptop. The Windows laptop next to my Ubuntu laptop never flinched. The only way I can now connect to the internet on this computer is by plugging in directly, which is not a solution.

I am running an Acer Aspire 3810TZ. I ran lspci -v | less and my wireless card is:
```
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Lite-On Communications Inc Device 6632
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d3500000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Count=1 Masked-
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

It's not on the list of supported wireless cards, but you know, it worked ... well, until it stopped working. ;) Please help. Or tell me what information you might need to help me. Because this plugging in business is no fun *at all*. 

(also: while launchpad has [a half dozen bugs](https://bugs.launchpad.net/ubuntu/+source/linux?field.searchtext=ar928x&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=) related to this network card, they're not quite what my problem is.)

---

### Post by Mila on 2011-03-25
*bump*

Still a problem. A point to note is that I can log into my school's unsecured network, as well as the free wi-fi at my local supermarket and Starbucks. It seems to just be the WPA2 networks that I can't access.

---

