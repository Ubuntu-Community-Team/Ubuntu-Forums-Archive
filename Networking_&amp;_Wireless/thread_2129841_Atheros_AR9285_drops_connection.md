---
title: "Atheros AR9285 drops connection"
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by djmental on 2013-03-27
Hi guys,

I've got a wifi connection that drops around every half hour. When I go to the log I see this:

ubuntu wpa_supplicant[29144]: CTRL-EVENT-DISCONNECTED bssid=00:23:69:28:21:75 reason=7

It then connects again, but after a while it drops.

My wifi card is an AR9285 Wireless Network Adapter. 

I only have this when I download or copy large files.

It is an b/g/n based card, though my router is g. Could this be the problem?

Thx in advance

---

### Post by Hadaka on 2013-03-27
Hi, let's find out..
"It is an b/g/n based card, though my router is g. Could this be the problem?"
please do..
```
lspci -nnk | grep -iA3 net
```
post the results
thanks.

---

### Post by djmental on 2013-03-28
Thx for your reply. The output is:

01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14e5]
    Kernel driver in use: atl1c
    Kernel modules: atl1c

The one above is the wifi, but I guess you already knew that.:-)

---

### Post by djmental on 2013-03-29
bump

---

### Post by Hadaka on 2013-03-29
Hi, give this a try
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
enter this line
```
 options ath9k nohwcrypt=1
```
save and close gedit.
boot and test

---

### Post by djmental on 2013-03-29
> **Hadaka said:**
> Hi, give this a try
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
enter this line
```
 options ath9k nohwcrypt=1
```
save and close gedit.
boot and test


Thx, but I've already tried that and doesn't help:(

---

### Post by Hadaka on 2013-03-29
Hi, about the only other thing i can suggest is
to look at your router settings, i you have wpa/wap2 mixed
see if you can go with just the wpa2....or...wpa.
and then there is the possibility your isp is hoseing
you for dumping big files...
good luck.

---

### Post by djmental on 2013-03-30
> **Hadaka said:**
> Hi, about the only other thing i can suggest is
to look at your router settings, i you have wpa/wap2 mixed
see if you can go with just the wpa2....or...wpa.
and then there is the possibility your isp is hoseing
you for dumping big files...
good luck.

Thx for your reply, I'll try the WPA option you suggested.

---

### Post by djmental on 2013-04-02
I put it on WPA2 only but still the same problem:-(

---

### Post by Hadaka on 2013-04-02
Hi, i dont know much about wpa_supplicant
or if this is even what the issue is. Let's see if
you have anything off the norm in your interfaces.
please do..
```
cat /etc/network/interfaces
```

you might also try the Wildman network settings that
help with disconnects. *see post #14  here
[http://ubuntuforums.org/showthread.php?t=2128565&page=2](http://ubuntuforums.org/showthread.php?t=2128565&page=2)
thanks.

---

### Post by Ashtonford on 2013-04-02
I was having the same problem and tried everything but nothing worked.  so i changed the channel on my wireless router was on 11 changed it to 1 .  Now everything is great again.  theres a free program for linux called iwscanner it lets you see what channel all the people close by people are on so you can set yours to a less used channel.

---

### Post by djmental on 2013-04-06
Hi,

This is what cat /etc/network/interfaces does:

# The primary network interface
auto wlan0
iface wlan0 inet static
address 192.168.1.151
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 212.54.40.25 212.54.35.25 
wireless-power off
wpa-ssid wtfdyw
wpa-psk 6252ba5c764932b76b784a316078a29de48107c55d95f9ae96bee19f1ea76be5
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-ap-scan 1
# The secondairy interface
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.0.0.0
network 10.0.0.0

Hope it helps.

Thx for the reply

---

### Post by djmental on 2013-04-10
Hi this is the output:

# The primary network interface
auto wlan0
iface wlan0 inet static
address 192.168.1.151
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 212.54.40.25 212.54.35.25
wireless-power off
wpa-driver wext
wpa-ssid wtfdyw
wpa-psk 6252ba5c764932b76b784a316078a29de48107c55d95f9ae96bee19f1ea76be5
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-ap-scan 1
# The secondairy interface
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.0.0.0
network 10.0.0.0

---

### Post by djmental on 2013-04-10
Oops sorry, double posting. I'll try to change the channel and see what that does.

---

### Post by Hadaka on 2013-04-10
Hi, quite the network you have there
please post..
```
cat /etc/NetworkManager/NetworkManager.conf 
```
if it says..
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
 
```
change it to ..managed=true

---

