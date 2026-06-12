---
title: "Alpha 2W disconnects"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by gabrielshier on 2011-06-22
Hello,

Working on ubuntu 10.04 on an IBM Thinkpad X61 laptop with an Alpha 2W wireless usb card on wlan0.

Once in a while the wireless network disconnects and can't connect to any network in range (open, wep, wpa, wpa2). It looks like it's trying to connect but then asks for a password (even if allready given one) and if open just not finishing connecting and trying to connect to another network. 

Happends the same with wicd.

Network card is working ok. Also with other computers. Drivers are installed correctly and power consumption management is off. 

any ideas?

---

### Post by gabrielshier on 2011-06-22
Got it:

modify /etc/network/interfaces and add:

auto wlan0
iface wlan0 inet dhcp
wireless-power off


Turn Off power managment:

1. Get this : sudo apt-get install bum
2. De-select the following services

    * powernowd
    * apmd
    * acpi-support
    * acpid

---

