---
title: "Belkin 7010 (RT2500) - driver does not support WPA"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by teeds on 2006-06-08
I am trying to get my Belkin F5D7010 working with WPA.

I have verified that it works with no encryption.

I have Knetworkmanger up and working now (took a little while).  It switches between wire and wireless connections with no drama.

My wireless router is set up with WAP1-PSK / WAP2-PSK with TKIP.

When I plug in my pcmia wifi card i get the following error in my syslog
```
<information>^Iwpa_supplicant(6407): Driver does not support WPA. 
```

Does RT2500 support WPA? Has anybody had success? i.e. should I keep trying with WPA?

---

### Post by ComplexNumber on 2006-06-08
i have just successfully installed a belkin rt2500 wireless card. go into services and switch wpa_suppliment OFF. otherwise it won't work. looking in the network manager applet, it does seem to be encrypted.

---

### Post by teeds on 2006-06-09
I managed to get my Belkin 7010 (RT2500) working with wpa using the guide from this link

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500]("https://wiki.ubuntu.com/WifiDocs/RalinkRT2500")

Long and the short.  RT2500 supports wpa natively and not through wpasupplicant and knetworkmanager does not let you turn wpasupplicant on and off.  So ditch it.

I edited my /etc/network/interfaces file to looks like this
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# Ethernet Adapter
auto eth0
iface eth0 inet dhcp

#Wifi Adapter
auto ra0 
iface ra0 inet dhcp
pre-up iwconfig ra0 essid "**INSERT YOUR ESSID HERE**"
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=9
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="**INSERT  YOUR PASSWORD HERE**"
pre-up iwpriv ra0 set TxRate=54
```
Make sure you have the correct essid, channel selected, authmode and encryptype set (consult your wifi router settings).

Then restart your computer.

Shasam!

---

