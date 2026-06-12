---
title: "No channels found with conceptronic DVB-T USB device"
date: 2010-06-12
forum: Multimedia Software
---

### Post by roalt on 2010-06-12
Hi all,

I want to install a DVB-T USB TV receiver on my Ubuntu (32-bit) 10.04 so I got a Conceptronic CTVDIGRCU v3.0 (usb dvb-t device).

I thought it would work on linux, but I do not get it to work. The USB device is recognized by the kernel and the right module is loaded (af9013). Also the firmware seems to be read correctly.

But I do not get any channels when executing:

w_scan -ft -c NL

It returns (after a long list of frequency/time logging):

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

I've also tried it on the same machine with Windows and there it works.

Anybody got this device working under 10.04 ?

---

