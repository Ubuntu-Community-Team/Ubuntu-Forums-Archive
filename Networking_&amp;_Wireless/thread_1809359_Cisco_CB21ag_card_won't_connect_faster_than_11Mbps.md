---
title: "Cisco CB21ag card won't connect faster than 11Mbps"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by tadpowle on 2011-07-21
Somebody help out a complete noob. I'm setting up my first Linux laptop with Ubuntu 11.04 and my CB21ag wireless card works, but won't achieve speeds over 11Mbps (maybe not "doing 802.11g rates for some reason?) 

I guess this  cardbus card is manufactured by Atheros for Cisco so I maybe that's why I'm seeing two wireless connections - the one with the "airo" driver gives me 11mbps, the other with the ATH driver would only get me 1mbps so I deleted that.

The card seems to disconnect/reconnect  periodically too - messages pop up frmo the wireless icon ...

lsmod says "airo" and "ath5k" are loaded 

So to get 54Mbps (802.11g speed) I'm wondering if theres maybe a different driver module for the CB21ag card or some configuration I need to tweak. 

Any ideas? 

More info - security is static WEP, lshw -C network returns some "wierdness" about network 0 ???

-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:d0:59:c8:7d:94
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo ip=192.168.1.5 latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:d0200000-d0203fff memory:d0400000-d07fffff memory:d0800000-d09fffff
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:50:b3:cb
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:d0204000-d0204fff ioport:8400(size=64)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:40:96:a2:39:c8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:d8000000-d800ffff

---

### Post by chili555 on 2011-07-22
Tad, Tad, Tad...where do I start. It seems that you have two separate wireless cards. Both are miraculously connected and each has its own IP address. In a forum where people can't get connected for love or money, you are connected *twice!*> *-network:0 DISABLED
description: Wireless interface
product: Cisco Aironet Wireless 802.11b
vendor: AIRONET Wireless Communications
physical id: 2
bus info: pci@0000:02:02.0
logical name: [COLOR="Red"]eth1[/COLOR]
version: 00
serial: 00:d0:59:c8:7d:94
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical wireless logical
configuration: broadcast=yes driver=airo [COLOR="Red"]ip=192.168.1.5[/COLOR] > *-network
description: Wireless interface
product: Atheros AR5001X+ Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:07:00.0
logical name: [COLOR="Red"]wlan0[/COLOR]
version: 01
serial: 00:40:96:a2:39:c8
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A [COLOR="Red"]ip=192.168.1.3[/COLOR]Is your Cisco Aironet a PCMCIA card that sticks out of the side of the laptop? Can you simply remove it? Aren't you still connected? Now that your computer isn't confused, is it fast?

---

### Post by tadpowle on 2011-07-23
Yup,I was confused, I thought the one NIC was being seen twice. But there are two WNICS, and one is hanging out the side. 

When I remove the one hanging out, I still have one connection left - the internal WNIC which is the Aironet 802.11b card at 11Mbps. 

So I shut that guy down with: sudo ifconfig eth1 down and the connection goes away.

and then insert my Cisco CB21ag card and it connects, but only at 1Mbps. Bummer, but we're getting there!

Any idea how to get 54Mbps out of that card? manipulate drivers maybe?

---

### Post by chili555 on 2011-07-23
Why don't we start by blacklisting the driver for the internal card and see if that helps. Please open a terminal and do:```
sudo su
echo "blacklist airo" >> /etc/modprobe.d/blacklist.conf
ifconfig eth1 down
rmmod -f airo
exit
```Now how does the external (Atheros) work? Please post:```
iwconfig wlan0
```Thanks.

---

### Post by tadpowle on 2011-07-23
Didi that and noticed the connection speed was 45Mbps for a short time after I inserted the CB21ag, but it settled out to 1Mbps. Remoived and reinserted and bitrate bounces around but settles down to 1Mbps.

Looks to me like I have a signal strength issue too....

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=17/70  Signal level=-93 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0

reinserted again and checked at  5 sec int 

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          
tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=21/70  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=21/70  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=24 Mb/s   Tx-Power=23 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=19/70  Signal level=-91 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:32   Missed beacon:0

Moved to 8 feet from the AP, reinserted and got ...

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0

tommy@tommy-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0

Maybe the card is bad (it's been hanging around here for a while)? (-64dbm I think is not good at 8 feet....)

I'll have to try it in another machine, maybe my windows work laptop. Any other ideas?

---

### Post by chili555 on 2011-07-23
It's probably not the card. Google ath9k slow and you will see lots of complaints. Please try this and let us have your report. If that doesn't do it, we can dig deeper.

[http://forums.debian.net/viewtopic.php?f=7&t=62979](http://forums.debian.net/viewtopic.php?f=7&t=62979)

---

### Post by tadpowle on 2011-07-27
Sorry for the delay. (work gets in the way now and then.)

I couldn't test the card in another machine (work laptop has no PCMCIA slots)

added file /etc/modprobe.d/ath5.conf containing "options ath5k nohwcrypt=1" then..

rmmod ath5k (lost the connection)
modprobe ath5k (connection came back)

but no better. (bit rate bounced around then settled down at 1Mbps

root@tommy-laptop:/etc/modprobe.d# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"WZCP8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:E2:64:EE   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:0FB3-DF16-0C
          Power Management:off
          Link Quality=20/70  Signal level=-90 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

What other info can I send? (I just ran the system test with Network selected..)

---

### Post by chili555 on 2011-07-27
You could try to force it to 54M:```
sudo iwconfig wlan0 rate 54M
```Or try:```
sudo iwconfig wlan0 rate auto
```However, I'm not sure it will stick because of:> wlan0 IEEE 802.11abg ESSID:"WZCP8"
Mode:Managed Frequency:2.462 GHz Access Point: 00:18:01:E2:64:EE
Bit Rate=1 Mb/s Tx-Power=27 dBm
Retry long limit:7 RTS thrff Fragment thrff
Encryption key:0FB3-DF16-0C
Power Managementff
[COLOR="Red"]Link Quality=20/70[/COLOR] Signal level=-90 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:3 Missed beacon:0
I don't know if that's a valid reading or if the card is not capable with it's current driver, of discerning the power level accurately.

You might build compat-wireless: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

I don't have an ath5k device, so I can't say if it's better or worse. I am confident it's newer. If you'd like to try it, post back and we'll get started.

---

