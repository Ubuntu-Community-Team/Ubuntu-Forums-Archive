---
title: "wlan connected but can't go to internet"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by dex3000 on 2010-09-02
I can connect my wlan card to router (gateway) ,but I can't go to internet, pinging my router (and everything else) also falied. Same problem was with knoppix but with help of others i solved it modifing etc/reslove.conf  IP address to my gateway (nameserver). At ubuntu resolve.conf seems ok, as there is already IP address of my gateway?

---

### Post by MaindotC on 2010-09-02
Please try following the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know at what point you are having difficulty or not receiving the desired output from the commands listed.

---

### Post by dex3000 on 2010-09-02
all seems ok with hardware, as commands display mac from router (ap), i disabled ipv6, but i don't have /etc/modprobe.d/aliases file
 
btw. i don't use dhcp on router.

---

### Post by MaindotC on 2010-09-02
show me:

lshw -C network
iwconfig

---

### Post by dex3000 on 2010-09-03
this is when connected
 
lshw -C network 
 
>  
*-network 
description: Wireless interface
product: RT2500 802.11g Cardbus/mini-PCI
vendor: RaLink
physical id: b
bus info: pci@0000:02:0b.0
logical name: wlan0
version: 01
serial: 00:10:a7:2c:48:c9
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2500pci ip=192.168.1.2 latency=32 multicast=yes wireless=IEEE 802.11bg
resources: irq:9 memory:de000000-de001fff

 
lwconfig
 
>  
lo no wireless extensions.
 
wlan0 IEEE 802.11bg ESSID:"lateralus" 
Mode:Managed Frequency:2.412 GHz Access Point: 00:13:49:EC:0B:68 
Bit Rate=48 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
Link Quality=44/70 Signal level=-66 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


---

### Post by MaindotC on 2010-09-03
> **dex3000 said:**
> this is when connected
 
lshw -C network 
 
```

*-network
description: Wireless interface
product: RT2500 802.11g Cardbus/mini-PCI
vendor: RaLink
physical id: b
bus info: pci@0000:02:0b.0
logical name: wlan0
version: 01
serial: 00:10:a7:2c:48:c9
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [SIZE="4"]driver=rt2500pci[/SIZE] ip=192.168.1.2 latency=32 multicast=yes wireless=IEEE 802.11bg
resources: irq:9 memory:de000000-de001fff
```


Ok so you appear to have the correct driver installed and you assigned yourself an ip address.

>  
lwconfig
```

lo no wireless extensions.

wlan0 IEEE 802.11bg ESSID:"lateralus"
[SIZE="4"]Mode:Managed[/SIZE] Frequency:2.412 GHz Access Point: 00:13:49:EC:0B:68
Bit Rate=48 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn
Link Quality=44/70 Signal level=-66 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

I wanted to make sure your wireless card was not in Ad-Hoc mode and it is in Managed.  Now you said you can't ping your gateway but you also mentioned it to be a nameserver.  Can you ping anything by ip address?

Also, I found [this thread and post #2](http://ubuntuforums.org/showthread.php?t=369100) that has a wealth of information specifically related to your network card.  Can you see if any of that helps you?

---

### Post by dex3000 on 2010-09-04
it seems the only problem was in wlan configuration is using WEP 128 bit passphrase, changing that to WEP 40/128 bit key solved the problem. It's strange couse in both cases i was connected
(this is for Ralink 2500)

---

