---
title: "Setting up Wireless - Ubuntu Server"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by wmgries on 2009-08-15
I recently purchased a Linksys WRT160N router to replace a failing one for my home network but I'm having some trouble getting my home server, Ubuntu 9.04, to accept the new router.  I've setup all the other computers in my house (both Windows and Mac) and they don't seem to have a problem with the new configuration, so it isn't a problem with the router.

The problem is seemingly coming from the change to WPA2 from WEP (what I used with the other router).  After realizing I couldn't use the same configuration in /etc/network/interfaces as WEP (wireless-essid and wireless-key) for WPA2, I found a HOWTO guide on these forums: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

But nothing in the guide seems to work on my server.  I've tried every setup possible (even the ones I know aren't it).  According to router setup page, I'm using WPA2 Personal with AES for encryption.

Is there anything else I ought to try?  Or should I give up and go back WEP?

---

### Post by wmgries on 2009-08-15
I think part of the problem is that no matter what I do, I can't seem to get iwlist to see my router in a scan.  I've changed every part of my router setup with no luck getting it to appear.

Under my understanding, the fact the computer can't see the network I'm trying to connect to is the problem.

---

### Post by Brandon Williams on 2009-08-15
Please post the relevant content from your /etc/network/interfaces file (SSID and WPA2 key both stubbed out for privacy). We'll be better able to give useful responses if we have all of that information. Also, post the relevant output from 'sudo iwlist scan' (again with the SSID stubbed out).

I use WPA1, not WPA2, but for me, the information in the guide looks exactly like what I use on my server.

---

### Post by wmgries on 2009-08-15
/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid *****
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk **************************************************************************

```

sudo iwlist scan:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by wmgries on 2009-08-15
Ok, I know that the problem is not the Wi-Fi card in my Server because I booted into Ubuntu 9.04 live CD and was able to connect to my to the internet with no problems.

sudo iwlist scan reveals my network as well.

This is quite perplexing to me.

---

### Post by wmgries on 2009-08-15
Ok, the card in the computer is a WMP54G.  Is it possible I need to install a newer/different driver?  Why would it have worked with our old WRT54GS but not with the new WRT160N?  Why does the WMP54G work in Ubuntu Desktop and XP (I have the same card in another computer running XP)?

---

### Post by Brandon Williams on 2009-08-15
Do you see anything in dmesg related to wlan0 or the driver?

For comparison, try running 'lshw -C network' on the server and then again when running Ubuntu Desktop. Do they both show the same information for the card? And if not, what are the differences?

---

### Post by wmgries on 2009-08-16
For Ubuntu Server

sudo lshw -C network:```

  *-network:0
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wmaster0
       version: 00
       serial: 00:21:29:6a:03:97
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 11
       serial: 00:1a:70:11:ff:a2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.108 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes
```

I am connected to the router through Ethernet temporarily, because I require some of the services on my Server.

I'll get the Desktop version up in a little bit.

---

