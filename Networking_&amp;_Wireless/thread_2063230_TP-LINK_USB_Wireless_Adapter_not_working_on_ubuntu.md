---
title: "TP-LINK USB Wireless Adapter not working on ubuntu 10.04"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by RichardC400 on 2012-09-26
My desktop computer has no Wireless card built in since it is a little old. I put ubuntu 10.04 onto the machine. I Recently bought a Mini Wireless N USB Adapter.. Model Number: TL-WN723N
So that I could pick up the home wireless network.
However, once I plug in the device the computer doesn't seem to detect it at all.
I installed ndisgtk, and I installed the driver but it won't pick it up.

I then did a lsusb:
```
:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04e8:6881 Samsung Electronics Co., Ltd 
Bus 001 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bc2:3300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


then iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions
```.

I then blacklisted rt2800usb
 and restarted but still nothing

I then tried this:
[http://community.linuxmint.com/hardware/view/5413](http://community.linuxmint.com/hardware/view/5413)
and it didn't work.

It picks up on my 11.04, and a Vista machine, but they both have wireless cards anyway.

Also installed WICD-GTK

---

### Post by RichardC400 on 2012-09-26
Solved it.

After a break I decided to start again and uninstalled the driver that I had. Then I went to the TP-LINK website and discovered that I downloaded the incorrect driver. The driver I installed was for version 1, and mine was version 2.2 (So I downloaded the version 2 driver)
After that it still said that no device was present.
So I went to the blacklist gedit file, and erased everything that I had blacklisted.
After that the device was found, however the green light on the usb wasn't lit up, and it wouldn't connect to any network.
I plugged it out then plugged it back in again.
After that it lit up, and after half a minute I had it connecting to my network, now it works fine.
:)
Hope this helps anyone who is having similar problems as I did.

---

### Post by TriciaS on 2013-06-02
:)

---

