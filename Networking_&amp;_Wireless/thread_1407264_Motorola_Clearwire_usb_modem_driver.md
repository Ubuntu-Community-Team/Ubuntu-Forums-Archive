---
title: "Motorola Clearwire usb modem driver???"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by fortyseven05 on 2010-02-15
Ive been searching all over the internet and i cant find a driver or way to use my clearwire usb modem with kubuntu. ive found where several people have asked about it, but no one seems to have an answer for this. clear is the only access i have to the internet right now and will be for quite a while, and its a real pita to have to reboot to windows to do anything. if any one knows how i can use this modem with kubuntu or if someone has heard of a place to dl a linux driver for it, i would really realy appreciate the info. suggestions, guesses, whatever, im open to all of it...!!

---

### Post by GeorgeVita on 2010-02-15
Hi **fortyseven05**, I cannot help you directly but I feel some more technical is useful for all readers of your thread:

- Specific type of modem (look at the sticker), post a link of tha sales brosure.

- boot without modem, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- from terminal: **lsusb**
- kernel version (from terminal): **uname -a**
- attach modem, power it ON
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**

NOTE: do NOT post output of the 'sudo dmesg -c' as this is huge and without data for your modem!

Notice any changes comparing 'lsusb' outputs. The 'new line' must be the modem (example below shown my modem):
> Bus 001 Device 004: ID **19d2:2000** ONDA Communication S.p.A. The vendorID : productID numbers are your 'search string' to find help. For above output you must search for **'19d2:2000'** and their HEX definitions '**0x19d2 0x2000'**

Second 'dmesg' will show all system activity, possible drivers used and any communication port created. If you see something like **ttyUSB0** you can 'list it' using: **ls /dev/ttyU***

In general, most new communication ports created can be listed with:
```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
```

>>> An update using other internet connection (wifi or ethernet) is preferable as a bug exist on initial kernel (ubuntu 9.10 LiveCD).

Regards,
George

---

