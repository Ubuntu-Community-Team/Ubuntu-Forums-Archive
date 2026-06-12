---
title: "Cant get Intel Pro Wireless 2200bg network card to work"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by Bluehazed on 2006-07-07
I cant get my network card to work at all! it detects it and the networks, but still nothing. i would be very greatful if i could get some help.](*,)

---

### Post by parkash on 2006-07-08
What's the output of:

$iwconfig

$iwlist [your_wireless_interface] scanning

Is the network you're trying to connect to encripted?

---

### Post by sunilsattiraju on 2006-07-08
Hi ,
I have the same problem..please guide me
here is $iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"tryme"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:23BF-DEC4-A3FC-706E-C215-A86E-C3   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

and iwlist eth1 scanning 
eth1      No scan results

yes my wireless is encrypted and is WEP and i have entered the WEP key..still not working...

Any help is greatly appreciated..

---

### Post by parkash on 2006-07-08
humm...  Access Point: Invalid
That's something I've never seen before.. Perhaps you could re-check your settings?

---

### Post by sunilsattiraju on 2006-07-08
also there is no frequency listed in that.. do i have to install anything? if yes can you please post it..(I am fairly new to linux) and lshw -C gives me the following ...Plzz help

sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:77:53:ec
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=full ip=192.168.0.2 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfdfc000-dfdfdfff irq:201
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 03
       serial: 00:0b:7d:1b:8c:3f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-23-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:177

---

### Post by parkash on 2006-07-08
Don't think so... You're sure that your wireless card is on right?

$sudo ifdown eth1
$sudo iwconfig eth1 essid=[name_of_your_accesspoint]
$sudo iwconfig eth1 key=[your_key]  --Note that WPA is not supported (as far as I know)
$sudo ifup eth1

Let's see what happens with that.

---

### Post by sunilsattiraju on 2006-07-08
Thanks so much for the help..
---------------------------------------------
sudo ifdown eth1
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   Socket/fallback

--------------------------------------------------
sudo iwconfig eth1 essid =tryme
---------------------------------------------------
sudo iwconfig eth1 key =23bfdec4a3fc706ec215a86ec3
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "=23bfdec4a3fc706ec215a86ec3".
----------------------------------------------------

sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
-----------------------------------------------------------

---

### Post by Thunders on 2006-07-08
I have the same problem. Trying to make an Ad-hoc network, all configured, iwconfig lists my wireless connection with "unassociated" or "radio off" before the ESSID description, but then the iwlist scan shows "no scan results". My laptop wireless button doesnt seem to respond either (led off).

---

### Post by Bluehazed on 2006-07-08
yeah i seriosly dont get what your sayin. im kinda a noob with linux...:confused:

---

### Post by parkash on 2006-07-09
> **sunilsattiraju said:**
> Thanks so much for the help..
---------------------------------------------
sudo ifdown eth1
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   Socket/fallback



'Till there everything seems ok.

> 
--------------------------------------------------
sudo iwconfig eth1 essid =tryme
---------------------------------------------------


I guess you didn't have any trouble here

> 
sudo iwconfig eth1 key =23bfdec4a3fc706ec215a86ec3
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "=23bfdec4a3fc706ec215a86ec3".
----------------------------------------------------


Perhaps you would like to change they key to something more simple.. Just to check that line "invalid argument"...  Try something like: XXXXXXXXXX
Where X is a number from 0-F (HEX)

> 
sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   LPF/eth1/00:0b:7d:1b:8c:3f
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
-----------------------------------------------------------

This part would obviously fail... Because of the error setting the key and because, I presume, your network card is off. Do you have a button? Try getting your wireless card "ON" first.

---

### Post by parkash on 2006-07-09
> **Thunders said:**
> I have the same problem. Trying to make an Ad-hoc network, all configured, iwconfig lists my wireless connection with "unassociated" or "radio off" before the ESSID description, but then the iwlist scan shows "no scan results". My laptop wireless button doesnt seem to respond either (led off).

What wireless card are you using? 
Type $lsmod
Then look for the module corresponding to your wireless card. (ipw2200 for Intel Pro Wireless 2200 b/g, for example)

And finally try this:

```

$sudo nano -w /etc/modules

```

At the end of the file:
```

# In order to switch ON Wireless & LED
ipw2200 led=1

```
Ctrl^x and y to write the file
Reboot (and cross your fingers, that works with Gentoo pretty well, but I've using Ubuntu for not too long now and always without any problem)

It is possible that after that change your wireless will be changed to eth0 so you may want to run $iwconfig once more...

Check with iwlist to see that everything is alright.

---

