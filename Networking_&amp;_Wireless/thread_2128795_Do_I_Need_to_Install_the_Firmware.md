---
title: "Do I Need to Install the Firmware"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by Victor99 on 2013-03-24
HI! I'm new to linux, so be gentle. I'm going to install a pci wifi card. I'm running Ubuntu 12.04. The card:
     Linksys a division of Cisco
     Wireless-N PCI Adapter with Dual-Band
     Model No.: WMP600N

The chipset is RT2860. I found a prvious post    
     Ubuntu 10.04 using the Ralink RT2860 WiFi chipset

I'm going to follow it step-by-step. I downloaded the driver, but I also saw the firmware for it on the download page, so I downloaded it also.  Should I install the firmware first, and if so how, then just follow the steps?  Do I just disregard the firmware? Also, in the tutorial, it says to be sure to extract the downloaded driver file to the Home directory so there are no problems in the following steps  Do I make another folder in the Home directory, or is it just extracted there without a folder? Any and all responses will be greatly appreciated. Thanks.

---

### Post by chili555 on 2013-03-24
Your device is probably already supported by the driver rt2800pci in Ubuntu 12.04; as well, the firmware is already in place. Let's do some diagnostics. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Victor99 on 2013-03-24
Thanks for the response. I haven't installed the card yet. I just wanted to know since In the post I referred to, it said that he had trouble booting the computer, and I wanted to avoid that. I probably won't get a chance for a couple of days. Thanks. I'll be back.

---

