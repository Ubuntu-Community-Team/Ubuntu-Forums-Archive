---
title: "Looking for a 802.11n card"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by jknotzke on 2009-05-16
Hi,

   I've been searching and reading on this topic for a week and it looks to me that Ubuntu does not support any 802.11n USB or PCMCIA/Cardbus cards at 'n' speeds.

   Is this right ?

   I'm looking to get either a PCMCIA/Cardbus or a USB card that will give me 802.11n speeds on my 9.04 Ubuntu box.

   If anyone has a setup working, let me know.

   Thanks

   J

---

### Post by dBLiSS on 2009-08-28
Have you found a solution?? I am in the same boat.

---

### Post by hwttdz on 2009-09-13
Me too.

---

### Post by falconindy on 2009-09-13
Check out [http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k). I believe the ath5k and madwifi drivers also support an array of 802.11n devices.

I know that's not a direct answer, but it's a place to start. There **are** people running draft-n cards on Ubuntu.

---

### Post by hwttdz on 2009-09-13
A link from there sends you to a list of supported devices, which is one device long (but it's better than zero).

[http://linuxwireless.org/en/users/Drivers/ath9k/devices](http://linuxwireless.org/en/users/Drivers/ath9k/devices)

Apparently the D-Link DWA-645. Though it seems to be discontinued, and additionally for laptops only.  It looks like n devices and support are still maturing.

---

### Post by falconindy on 2009-09-13
draft-n is still in draft. Support for said draft has been shaky since its first appearance over 2 years ago. Hopefully the current plan of releasing the official 802.11n specification by October goes through and we'll start to see some real support for it.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-13
Ralink.My laptop has one. I don't have an N network avaliable, but it probably works
My module is " rt2500sta"

---

### Post by Everybody Loves Hypnotoad on 2010-02-22
You might not get any better transmission rates using an n card in ubuntu compared to built in g stuff like intel 3945 or some cheap generic USB g 54Mbps sticks. So save your money.

---

