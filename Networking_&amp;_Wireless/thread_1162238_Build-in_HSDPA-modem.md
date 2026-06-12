---
title: "Build-in HSDPA-modem"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by golfarn on 2009-05-17
Hi

I'm running Ubuntu 9.04 om my new Toshiba Portege R600 laptop.
It works great!

But I can't get my build-in HSDPA 3G-modem to work.
First of all, it shows that I have 3 devices instead of 1. And when I try to connect I get a message after 5-10 seconds that says "GSM-network Disconnected"

I'm from Sweden and are using Tele2/Comviq as my operator. I've checked my connection settings and they are the same as the one supplied from Tele2/Comviq.

Have anyone any clue to how I can solve this?
Is there any error logs that I need to check and where are they located on my computer?

Regards!

---

### Post by Chiapo on 2009-05-17
I have been having a similar issue, except my built in Qualcomm 9121 3G (HSDPA/UTM/EDGE) modem is not recognized at all.
When I try tethering my Samsung i617, I get a request for password, then the PC acts like it is trying to connect, followed by the "Disconnected to GSM Network" message.
I'm using UNR Jaunty 9.04 on an Acer Aspire One.
I have no problem connecting in Windows...
I've tried appending usbserials.vendor=<hexadecimal_value_I_can't_remember> + usbserials.product=<another_hex_value_I_don't_recall> to my GRUB menu.lst file, but that returns "usbserials not found, ignoring ..." and boots normally into UNR.
Apparently this issue is rare?

---

### Post by Chiapo on 2009-12-04
A workaround might work for you is listed here: [http://ubuntuforums.org/showthread.php?t=1157846&page=6](http://ubuntuforums.org/showthread.php?t=1157846&page=6)

Cheers!

---

