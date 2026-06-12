---
title: "Setting up Wifi Scanner Epson NX430"
date: 2012-02-16
forum: Networking &amp; Wireless
---

### Post by tooch71 on 2012-02-16
I just installed an Epson NX430 All-in-one machine. The wifi printing works great, but how do I set it up to scan. Ubuntu can "see" the scanner, but the scanner cannot "see" the laptop.

Thanks!

---

### Post by tacl on 2012-07-17
Does anyone have a solution to this? I also still have this problem and have been putting it off for months since school ended. I use an sd card now, but wireless would be great!

---

### Post by Jary316 on 2012-07-20
I am looking for one as well please (scanning with cable or wirelessly, so far drivers didn't help).

I can print with cable and wirelessly so far.

---

### Post by tacl on 2012-07-28
Does anyone have a solution for this, just a bump for this thread. Maybe another thread has already fixed this?

---

### Post by joeradtke on 2012-09-23
I have the same scanner and can't make it work.  Printing is fine.  Has anybody solved this yet

---

### Post by mickey v on 2012-09-24
I have an Epson NX430 too and couldn't scan over wifi either even though printing worked fine, i ran across this thread while looking for a solution. What worked for me was downloading XSane Image Scanning Program from the software center and using that instead of the Epson iscan drivers. I have no idea if it will work for everybody but just wanted to put that out there for anyone who hasn't tried it yet.

---

### Post by tacl on 2012-09-28
mickey v, man I love you. The whole time I was trying to scan from the printer, and all I had to do was press "scan" from my computer. That was just using the simple scan, although thanks for sharing xsane, it's more of what I am used to. THANKS AGAIN.

---

### Post by mickey v on 2013-05-05
I finally got the iScan drivers to work so i thought i'd post the instructions in case someone needs them - 

Donload the drivers from epson (nx430 is the product name) - [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Make sure to install data and core package and network plug in package in that order (data, core, network)

After installation follow the instructions here - [http://download.ebz.epson.net/faq/linux/faq_ls_00007.html](http://download.ebz.epson.net/faq/linux/faq_ls_00007.html)

It's pretty simple, just open /etc/sane.d/epkowa.conf as admin/root and scroll down to instructions for network attached devices and make an entry for your device under the examples given like this - 

net your device ip addy port number (it says default is port 1865 so i just used that)

net 192.123.1.123 1865

Don't put a # before your entry

Then open /etc/sane.d/dll.conf as admin/root and put a # before epson2

That's it, it worked for me hopefully it'll work for you.

---

### Post by 2-e on 2013-05-07
> **mickey v said:**
> I finally got the iScan drivers to work so i thought i'd post the instructions in case someone needs them - 

Donload the drivers from epson (nx430 is the product name) - [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Make sure to install data and core package and network plug in package in that order (data, core, network)

After installation follow the instructions here - [http://download.ebz.epson.net/faq/linux/faq_ls_00007.html](http://download.ebz.epson.net/faq/linux/faq_ls_00007.html)

It's pretty simple, just open /etc/sane.d/epkowa.conf as admin/root and scroll down to instructions for network attached devices and make an entry for your device under the examples given like this - 

net your device ip addy port number (it says default is port 1865 so i just used that)

net 192.123.1.123 1865

Don't put a # before your entry

Then open /etc/sane.d/dll.conf as admin/root and put a # before epson2

That's it, it worked for me hopefully it'll work for you.

Could you demonstrate how to make the changes in epkowa.config?

---

### Post by mickey v on 2013-05-08
Sure, here's the relevant section of epkowa.conf - 

# Network attached devices may be made to work by first installing the
# (non-free) iscan-network-nt package and then adding configuration lines
# as per information below.
#
# For each network attached device, you must add an entry as follows:
#
#   net <IP-address|hostname> [port-number]
#
# Ask your network administrator for the device's IP address or check
# for yourself on the panel (if it has one).  The port-number is very
# optional and defaults to 1865.
# Note that network attached devices are not queried unless configured
# in this file.
#
# Examples:
#
#net 192.16.136.2 1865
#net 10.0.0.1
**#net scanner.mydomain.com**

Directly under that last line (which i bolded here)  put "net ip addy port number" (without quotes) so it looks like this - 

#net scanner.mydomain.com
  net 192.168.1.123 1865

Then save your changes and close.

---

### Post by 2-e on 2013-05-08
Thanks a lot. Works great (I actually used it on the NX420).

---

