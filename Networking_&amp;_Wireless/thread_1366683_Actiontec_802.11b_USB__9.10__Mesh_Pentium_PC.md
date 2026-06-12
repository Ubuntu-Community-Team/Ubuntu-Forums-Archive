---
title: "Actiontec 802.11b USB / 9.10 / Mesh Pentium PC/"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by JonathanWest on 2009-12-28
Tearing my hair out all day trying to get my USB wireless card working using forums and advice from everywhere!

Attached is the output from the various diagnostics commands.

I get the pop-up at the top-right but it always says wireless network is disconnected.

Can anyone suggest what is wrong? The ifconfig does not shown wlan0 at all, the iwconfig says it has no wireless extensions, there are various dmesg lines but not sure if they are fatal, lshw says the network is disabled, etc.

After a few unsuccessful attempts, including using ndiswrapper etc., I decided to start again.

I reinstalled 9.10 from scratch (using the live CD) and then installed the package linux-wlan-ng_0.2.9+dfsg-2_i386.deb (using a memory stick).

It seems I shouldn't need ndiswrapper as the card is supposed to be supported (it's a Prism 2.5 USB card).

(N.B. Linux novice!)

---

### Post by bkratz on 2009-12-28
Sorry I'm not familiar with the device but maybe something is useful here??

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=(ManufacturerModel)|(AND](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=(ManufacturerModel)|(AND))

---

### Post by JonathanWest on 2009-12-28
> **bkratz said:**
> Sorry I'm not familiar with the device but maybe something is useful here??

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=(ManufacturerModel)|(AND]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28ManufacturerModel%29%7C%28AND"))

Thanks - but tried using that paritcular page. Problem with all these guides is they never line up with what happens in reality and they all disagree with one another!

---

