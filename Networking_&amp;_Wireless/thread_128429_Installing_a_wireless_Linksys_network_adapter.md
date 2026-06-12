---
title: "Installing a wireless Linksys network adapter"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by Y-town on 2006-02-11
I can't figure out how to get my internet working with my **Linksys wireless-B usb network adapter, model WUSB11**. I connect one end of the usb cable to my computer and one to the network adapter but i still have problems with connecting to the internet. 

Any ideas on how to install the wireless network adapter?

---

### Post by UbuntuLinuxUser on 2006-02-11
I have almost the same problem....only I have a laptop pci port linksys wireless G card.

---

### Post by arckeda on 2006-02-11
I had same exact adapter and i will help you! 
go to root terminal and type 

iwconfig wlan0 ap any

iwconfig wlan0 essid any

then try going to admin and networking then set up wlan0 ad DHCP and leave web key and stuff blank, you may have to do this before doing teh steps i just mentioned in root terminal

---

### Post by az on 2006-02-11
It must be the prism2_usb chipset.  There are more than one  version of that card.  It is supposed to work fine if you install the linux-wlan-ng package (on the cd)

Try that.  It works for some people, but not me.  Here are the details of what I do to get it to work, as well as the bug report for you to add to, if you can.


[http://ubuntuforums.org/showpost.php?p=465719&postcount=7](http://ubuntuforums.org/showpost.php?p=465719&postcount=7)

---

### Post by UbuntuLinuxUser on 2006-02-12
[QUOTE=arckeda]I had same exact adapter and i will help you! 
go to root terminal and type 

iwconfig wlan0 ap any

iwconfig wlan0 essid any

then try going to admin and networking then set up wlan0 ad DHCP and leave web key and stuff blank, you may have to do this before doing teh steps i just mentioned in root terminal[/QUOTE]

who are you talking to? author of this thread?

---

