---
title: "Wireless connected, but not at 'N' rate (above 54Mbps)"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by Ameades on 2010-10-14
I have a Linksys WUSB600N wireless adapter for my laptop which uses the rt2800usb drivers.

My router:
Router Model: Linksys WRT150N v1.1
Firmware Version: DD-WRT v24-sp2 (07/22/09) mini - build 12548M NEWD Eko

The wireless usb adapter connects to my network, and the router is running on mixed mode, except that I cannot seem to get wireless 'n' connection speeds.  Both are capable of wireless n.  I check the connection info and it is always 54 Mbps.  I have set the router wireless on N-only and I lose my connection.

Is the standard driver for this usb adapter in Ubuntu 10.4 unable to utilize 'n' speeds?  Or am I missing something?

Please advise.  Thanks.

---

### Post by Ameades on 2010-10-14
Some info on the drivers loading.

```
andrew@andrew-laptop:~$ lsmod | grep -e ndis -e rt2
rt2800usb              31531  0 
rt2870sta             461811  1 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126496  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
led_class               2864  2 rt2x00lib,sdhci


andrew@andrew-laptop:~$ ls /etc/modprobe.d | grep -e ndis -e black
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
```

There is also [this thread]("http://ubuntuforums.org/showthread.php?t=972060") that has info on the specific usb adapter, but it is a bit out dated.

---

### Post by leejkennedy on 2011-04-18
Hi

I was having this exact issue recently and fixed it by re-setting the wireless security to use WPA2 and AES. It's strange but my windows 7 Home Premium dual boot could cope with my previous wireless settings which were WPA/WPA2-PSK with TKIP algorithm, but Ubuntu Maverick would just not work at a higher speed than 54Mbps until I reset as described. I'm now getting 150Mbps.

FYI this was with the ath9k driver, I'm not sure if this fix is specific to my network card (an Atheros AR9285 built into a Samsung laptop) and hope this helps..

Lee

---

