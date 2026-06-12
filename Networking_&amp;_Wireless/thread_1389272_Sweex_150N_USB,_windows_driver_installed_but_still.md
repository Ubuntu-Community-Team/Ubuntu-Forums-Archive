---
title: "Sweex 150N USB, windows driver installed but still no connection"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by timmynana on 2010-01-24
I used to have a PCi wireless card but decided to upgrade to a 802.11n device. I run the  [lshw  -C network]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network") command and no output is shown for the usb dongle. I have installed ndiswrapper and it states the driver is installed, but a popup always appears stating that Ubuntu cannot recognise if the hardware is present, but once this is closed the remaining window shows the dongle is present. So Ubuntu (9.10 btw) can recognise the card is present in the windows driver window, but not in lshw -c network. Any ideas? 

There are a number of posts about older Sweex products with different chipsets, but none seem to answer my query. NB my chipset is Ralink RT3070****

---

### Post by kingmoffa on 2010-06-14
I've just got the same USB network device. 

No luck with lucid. 

Looking at /var/log/syslog - it seems that the device is detected and tries to come up.

No networks found (even though Im in range of a few). 

Any ideas?

---

