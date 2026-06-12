---
title: "Restarting network and wireless"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Karahana on 2010-01-28
On Xubuntu Karmic I access the net using a RaLink RT2561/RT61 802.11g PCI and a WiFi network that uses  WPA/WPA2, EAP-TTLS, PAP security. The network sometimes "hangs" and Gnome's network manager usually reconnects automatically. Every once in a while (I'm unable to recreate it) the network-manager seems to hang and a reboot is required to get it working again. 

What I need is a command to restart the network manager and all my network interfaces. If i issue /etc/init.d/network-manager restart, the service restarts but nothing changes (still unable to connect to ANY network, not just the one that's WPA/WPA2, EAP-TTLS, PAP protected).

If I issue a /etc/init.d/networking force-reload command I get this:

* Reconfiguring network interfaces...           
ifdown: couldn't read interfaces file "/etc/network/interfaces"
ifup: couldn't read interfaces file "/etc/network/interfaces"
[fail]

The same goes for ifup / ifdown commands.

This is very annoying and I hope someone helps. 

Thanks! :D

---

### Post by chewearn on 2010-01-29
I don't have a direct answer, but I shall post the script I used to toggle the wifi on my eeepc 900, including toggling the power to the hardware.  Maybe this would give you some ideas about your own set-up.

```

#!/bin/sh

wlan_control=/sys/devices/platform/eeepc/wlan
WLANSTATE=$(cat $wlan_control)

case $WLANSTATE in
    1)
        # The sequence here *is* important.
        modprobe -r -q ath_pci
        modprobe -r -q ath_rate_sample
        modprobe -r -q ath_hal
        modprobe -r -q wlan_ccmp
        modprobe -r -q wlan_tkip
        modprobe -r -q wlan_wep
        modprobe -r -q wlan_acl
        modprobe -r -q wlan_scan_sta
        modprobe -r -q wlan
        echo 0 >/sys/devices/platform/eeepc/wlan
    ;;
    0)
        # Force PCI Express Hotplug to reinit
        modprobe -r -q pciehp
        sleep 1
        # pciehp_force may be unnecessary; Xandros did it.
        modprobe pciehp pciehp_force=1
        sleep 1
        # Switch on the hardware
        echo 1 >/sys/devices/platform/eeepc/wlan
        sleep 1
        modprobe ath_pci
        sleep 1
        /etc/init.d/networking restart
    ;;
esac
```

---

### Post by Karahana on 2010-01-29
Not quite sure what to make of this but I'll try and look into it. Maybe it helps! 

Thanks! :)

---

### Post by hemlockz on 2010-03-24
This was buggin me a lot because my mobile broadband would drop my connection from time to time.  Reading this thread led me to the solution for my problem.
 
sudo service network-manager restart
 
whoohoo.

---

