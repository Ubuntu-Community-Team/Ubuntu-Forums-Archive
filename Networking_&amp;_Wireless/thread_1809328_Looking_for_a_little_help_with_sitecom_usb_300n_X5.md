---
title: "Looking for a little help with sitecom usb 300n X5 network adapter"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by Hetepeperfan on 2011-07-21
Hello community,

Today I bought a usb network adapter: SITECOM wireless dualband USB adapter 300n X5.
Which according the box is installed with two pushes on a button, one on the usb stick and one on the router:popcorn: (oh yeah both should be sitecom and it would be handy to use mac or windows:(...).

Well I tried to use ndiswrapper. And I got to the following point:

```

$sudo ndiswrapper -i rt2870.inf
$sudo depmod -a
$sudo sudo modprope ndiswrapper

``````
$lsusb
bla bla
bus001 Device 003: ID 0df6:0062 Sitecom Europe B.V. 
``````
$ndiswrapper -l 
WARNING: all config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release
WARNING: all config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release
rt2870 : driver installed
            device (0DF6:0062) present
``````
$tail /var/log/messages/
lot of messages..
Jul 18:00:58 my-desktop kernel: [    163.157429] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jul 21 18:00:58 my-desktop loadndisdriver: loadndisdriver: load_drive(358): couldn't load driver rt2870
Jul 21 18:00:58 my-desktop kernel: [    163.543336] usbcore: registered new interface driver ndis wrapper

```iwconfig reports that eth0 and lo don't have wireless connecitions and no other devices are mentioned.

I hope anyone can identify what is wrong and can help me a step in the right direction.
I'm on a old intel x86 computer using Ubuntu 10.04 LTS

kind regards,

Maarten

---

