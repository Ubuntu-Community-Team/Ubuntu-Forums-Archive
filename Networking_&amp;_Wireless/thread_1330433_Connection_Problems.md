---
title: "Connection Problems"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Bugs318 on 2009-11-18
To begin with, it seems like whether or not I have torrent traffic, I have some bug otherwise akin to [this]("https://bugs.launchpad.net/ubuntu/+bug/374650").  Essentially, my wireless connection periodically disconnects, but will not reconnect.  It tries - asking me again for my WEP passphrase - but just sits there eternally unless I reboot, following which it connects no problem... until the next disconnect.

Thus, when internet searches proved fruitless in resolving it, I kept reading that Wicd would let me restart the connection without the need to reboot.  So I installed Wicd.

Now, Wicd won't connect to my network at all, such that I cannot even reinstall network-manager to remove Wicd.

Can anyone help?  My WEP passphrase is in properly.  Wicd validates authentication (very slowly) (or at least it seems to), but then fails to obtain an IP address.

If there is a way to reconnect gnome network manager and uninstall Wicd without access to the internet, that would suffice.  Otherwise, how can I first get Wicd working before removing it?  (And what is the best way to do that?)

Thanks so much in advance!

---

### Post by Bugs318 on 2009-11-18
Here is a log of one example connection attempt (from /var/log/wicd/wicd.log)

2009/11/18 12:46:12 :: Connecting to wireless network James
2009/11/18 12:46:12 :: Putting interface down
2009/11/18 12:46:12 :: Releasing DHCP leases...
2009/11/18 12:46:12 :: Setting false IP...
2009/11/18 12:46:12 :: Stopping wpa_supplicant
2009/11/18 12:46:12 :: Flushing the routing table...
2009/11/18 12:46:12 :: Putting interface up...
2009/11/18 12:46:12 :: Attempting to authenticate...
2009/11/18 12:46:12 :: Running DHCP
2009/11/18 12:46:12 :: Internet Systems Consortium DHCP Client V3.1.2
2009/11/18 12:46:12 :: Copyright 2004-2008 Internet Systems Consortium.
2009/11/18 12:46:12 :: All rights reserved.
2009/11/18 12:46:12 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2009/11/18 12:46:12 :: 
2009/11/18 12:46:13 :: Listening on LPF/ra0/00:25:9c:07:97:a1
2009/11/18 12:46:13 :: Sending on   LPF/ra0/00:25:9c:07:97:a1
2009/11/18 12:46:13 :: Sending on   Socket/fallback
2009/11/18 12:46:16 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
2009/11/18 12:46:22 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
2009/11/18 12:46:36 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
2009/11/18 12:46:55 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
2009/11/18 12:47:08 :: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
2009/11/18 12:47:17 :: No DHCPOFFERS received.
2009/11/18 12:47:17 :: No working leases in persistent database - sleeping.
2009/11/18 12:47:17 ::  * Reloading /etc/samba/smb.conf smbd only
2009/11/18 12:47:17 ::    ...done.
2009/11/18 12:47:26 :: DHCP connection failed
2009/11/18 12:47:26 :: exiting connection thread
2009/11/18 12:47:26 :: Sending connection attempt result dhcp_failed

---

### Post by Bugs318 on 2009-11-18
Okay, upon advice found elsewhere, I downloaded the required network-manager-gnome and network-manager packages in .deb form, brought them to the Wicd-disabled computer via usb-key and upon their install they removed Wicd.

Thus, my problem is half solved.

If anyone finds fixes (which I have now spent three days seeking wildly) for the problem of periodic wireless network disconnects which require a reboot for reconnection (apparently prevalent in Karmic Koala) please post here and let me know as this is particularly annoying.

Note, as aforementioned, that unlike the typical bug which occurs when torrent downloads are ongoing, mine drops the connection faster when downloading torrents, but also when not doing so if left alone for a while.

---

### Post by swatsbiz on 2009-11-18
bump

---

### Post by Bugs318 on 2009-11-19
Can anyone even hint at specific logs or outputs to post that may provide info to someone down the road who could offer some input?

---

### Post by Bugs318 on 2010-05-20
An eventual update has fixed this disconnect bug!

---

