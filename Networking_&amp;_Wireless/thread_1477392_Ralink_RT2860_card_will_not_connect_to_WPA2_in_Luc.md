---
title: "Ralink RT2860 card will not connect to WPA2 in Lucid"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by powerofpi on 2010-05-08
Hi guys,

After installing Lucid, I noticed that my Ralink RT2860 card would not connect to my home network using WPA2 despite the network being visible and of good strength. So I followed the guide at [http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703) in order to install the newest Ralink drivers. 

After installation, same issue. That is, the card will connect to my a/b/g/n network if I leave it unprotected, but it will not connect to the same network if switch it to WPA2. After being given the passphrase, the wireless icon on the indicator applet shows that it is trying to connect, but after awhile it fails. Does anyone know why the built-in driver and also the official Ralink driver are no good for WPA2 in Ubuntu 10.4 for my RT2860 card? Thanks in advance.

---

### Post by mysiak on 2010-05-08
Hi there I am havving the same issue as you described and cannot find any solution yet, but what happened to me, I actually got connected after install of ubuntu 10.04 and the first reboot but never after that

---

### Post by chili555 on 2010-05-08
From both of you, may I see, from a terminal:```
dmesg | grep -i rt2
```Thanks.

---

### Post by powerofpi on 2010-05-08
> **chili555 said:**
> From both of you, may I see, from a terminal:```
dmesg | grep -i rt2
```Thanks.

root@deering-desktop:/mnt# dmesg | grep -i rt2
[   16.664346] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.740685] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.752007] rt2860 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20

---

### Post by powerofpi on 2010-05-08
> **mysiak said:**
> I actually got connected after install of ubuntu 10.04 and the first reboot but never after that

Yes, I also was able to briefly connect to my network with WPA2 once, but then the connection was dropped and I also have not been able to connect since.

---

### Post by powerofpi on 2010-05-09
So... I was able to successfully connect to my WPA2 network after changing the cipher type at my router from "TKIP and AES" to just "AES". It may work with just "TKIP" as well, but I suspect that the driver does not play nicely with multiple rounds of ciphers. In any case, my original goal was to connect to my network with WPA2, which I now have, so marking as solved.

---

### Post by userFrodo on 2010-05-19
> **mysiak said:**
> Hi there I am havving the same issue as you described and cannot find any solution yet, but what happened to me, I actually got connected after install of ubuntu 10.04 and the first reboot but never after that

Exactly same problem here. I got connected for a short while, but never after that. Here is some log txt

$cd /var/log
$cat daemon.log

May 19 10:06:59 AcerAX3300-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 19 10:06:59 AcerAX3300-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 19 10:07:04 AcerAX3300-Ubuntu wpa_supplicant[971]: Trying to associate with 00:24:fe:00:71:20 (SSID='Frodo' freq=2452 MHz)
May 19 10:07:04 AcerAX3300-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 19 10:07:04 AcerAX3300-Ubuntu wpa_supplicant[971]: Association request to the driver failed
May 19 10:07:09 AcerAX3300-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
May 19 10:07:09 AcerAX3300-Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
May 19 10:07:09 AcerAX3300-Ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (Frodo)
May 19 10:07:09 AcerAX3300-Ubuntu NetworkManager: <info>  Marking connection 'Auto Frodo' invalid.
May 19 10:07:09 AcerAX3300-Ubuntu NetworkManager: <info>  Activation (wlan0) failed.
May 19 10:07:09 AcerAX3300-Ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
May 19 10:07:09 AcerAX3300-Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

$cat messages
May 19 10:02:45 AcerAX3300-Ubuntu kernel: [   10.932733] type=1505 audit(1274256164.893:2):  operation="profile_load" pid=731 name="/sbin/dhclient3"
May 19 10:02:45 AcerAX3300-Ubuntu kernel: [   10.932929] type=1505 audit(1274256164.893:3):  operation="profile_load" pid=731 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 19 10:02:45 AcerAX3300-Ubuntu kernel: [   10.933040] type=1505 audit(1274256164.893:4):  operation="profile_load" pid=731 name="/usr/lib/connman/scripts/dhclient-script"
May 19 10:02:45 AcerAX3300-Ubuntu kernel: [   11.353823] eth0: no link during initialization.

$lspci
04:00.0 Network controller: RaLink RT2860
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403

$ dmesg | grep -i rt2
[   10.608368] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   10.655058] rt2860 0000:04:00.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[   10.655221] rt2860 0000:04:00.0: setting latency timer to 64
[   11.728367] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat

---

### Post by userFrodo on 2010-05-19
> **powerofpi said:**
> So... I was able to successfully connect to my WPA2 network after changing the cipher type at my router from "TKIP and AES" to just "AES". It may work with just "TKIP" as well, but I suspect that the driver does not play nicely with multiple rounds of ciphers. In any case, my original goal was to connect to my network with WPA2, which I now have, so marking as solved.

Changed settings on router from:
WPA + WPA2

to:
WPA2 (CCMP)

Wireless networking is operative now

---

### Post by peterroots on 2010-07-15
Same problem here too. My router was set to wpa-psk/wpa2-psk with tkip/aes.
following the suggestion by powerofpi I changed the encryption to tkip only (as opposed to aes only) to see if that worked - it did.
It survived a disconnect and reconnect and a reboot so this seems to have cracked it for me.

---

### Post by stuberman on 2010-07-22
Had same experience here. I could get Lucid to connect intermittently.
 
Here is a [thread]("http://ubuntuforums.org/showthread.php?t=1476007") with details to update 10.04 with latest 2.4.0.0 RaLink driver.
 
I can connect now with WPA and WPA2 enabled on access points. (TKIP + AES)

---

### Post by nocco on 2011-07-30
Great!!! Thanks a lot all of you... I had the same problem and I've solved changing in my router options "TKIP o AES" with "AES" :D:D:D:D:D

---

