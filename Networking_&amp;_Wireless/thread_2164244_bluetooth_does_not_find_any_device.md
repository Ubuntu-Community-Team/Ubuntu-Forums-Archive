---
title: "bluetooth does not find any device"
date: 2013-07-30
forum: Networking &amp; Wireless
---

### Post by frohfroh on 2013-07-30
Hi,
when  trying to pair my notebook to my phone, my notebook keeps searching and never find the phone. The phone is in discoverable mode, and the pairing works just fine when using this very same notebook with another os. The phone is unable also to find the notebook.
Some information that might be helpfull:

hcitool dev
Devices:
    hci0    94:39:E5:95:BF:D4

rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

Does anyone have an idea?

P.S.: not sure whether bluetooth goes under <<wireless ans networking>> , apologies if it does not

---

### Post by pauljwells-m on 2013-08-02
I have the same issue. It's a known bug to do with firmware :-( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400) Your best bet is to use a usb plugin dongle then it works no problem

---

