---
title: "Problems with zd1211"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by Hurrilo on 2006-06-20
Hello, I have problems with my 3com usb wireless nic.
I've set up a wireless network at home using wep with passphrase, but just trying to get the thing to work I've disabled wep. But still I can't get it to work, don't know if it's maybe because I'm on the wrong channel. When I'm trying to change channel with iwconfig I just get errors.

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.

This message comes either I try to change frequency or channel.

This is actually the first time I got the zd1211 drivers to work, I've tried for some time before in breezy but I never managed to modprobe them. So this time I uses the included drivers in dapper. People say the drivers don't work properly, is that why I can't change channel perhaps?

Sometimes I can see in the log in my access ponit that the nic has logged on, but still I can't get access to the network.

Anyone who can help me? (I'm tired so I hope my post is comprehendable)

---

### Post by guyjohnston on 2006-06-28
From my experience of trying to get that card to work, I don't think the channel can be changed if you are in managed mode, as it always tries to find the channel automatically from an access point.

---

