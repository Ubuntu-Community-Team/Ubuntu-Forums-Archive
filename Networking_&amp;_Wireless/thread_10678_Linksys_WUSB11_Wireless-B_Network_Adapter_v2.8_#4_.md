---
title: "Linksys WUSB11 Wireless-B Network Adapter v2.8 #4 not working"
date: 2005-01-10
forum: Networking &amp; Wireless
---

### Post by minghai on 2005-01-10
Hi all, 

    I'm using a Linksys WUSB11 Wireless-B Network Adapter v2.8 #4 in WinXP with 64bit WEP and I'm looking to switch everything over to Linux but I've had no luck getting this USB adapter to work.  I've tried it under Mepis, Knoppix, Fedora Core 3 and Kanotix and nothing works.  I'm quite the Linux newbie.  Ubuntu is my last resort since I read on Ars about the wonderful user community.  Anyone have this adapter or can give me guidance on how to get it to work?

    I've searched around the forums and tried some things but not sure what the commands do.  If someone can enlighten me, I'd appreciate it very much.

1) I tried running "sudo modprobe pegasus".   Not sure what the command does but  nothing happens.

2) Tried adding network connection info thru Computer -> System Configuration -> Networking but no net access

3)  edited the /etc/network/interfaces file to
    iface wlan0 inet dhcp
    name Wireless LAN card
    wireless_mode managed
    wireless_eesid <the_essid>
    wireless_key s:<my_key>
    wireless_channel 11
    auto wlan0

    Still no net access

4) iwconfig
     wlan0 does not even show up.

5) Ran "sudo ndiswrapper -i NETUSB.inf".  This is the inf file I got from the adapter's CD.  Machine hung.

    I feel I'm shooting in the dark since I don't know what these commands do and in what order I should do them.  Please help!

Ming Hai

---

### Post by ziziom on 2005-03-05
Up!

I have the same adapter, tried the same things, nothing happened. Please Help!

---

### Post by otterit on 2005-03-06
Same here!

---

### Post by KenLin on 2005-03-08
give this a shot, guys

[http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11](http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11)

---

### Post by bankanidhi on 2006-10-21
same with me. I am using Fedora Core 5

---

### Post by az on 2006-10-21
I think it is a prism2_usb device.

See here:

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

you basically have to edit the interfaces files (/etc/network/interfaces)

and enter the configuration stuff:

wireless_mode managed
wireless_enc on
wlan_ng_key0 xx:xx:xx:xx:xx


These devices "speak a different language" than all the other wireless devices, which is why they are less easy to configure in Dapper.  I think the issue has been addressed in Edgy.

---

### Post by svenkatesan on 2008-01-14
I too have wusb 11-2.8v

[PHP]skumar@skumar:~$ sudo ndiswrapper -l
[sudo] password for skumar:
netusb : driver installed
        device (1915:2233) present (alternate driver: at76_usb)
skumar@skumar:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:07:e9:87:98:7f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:5b:c9:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.0-86 wireless=IEEE 802.11b
skumar@skumar:~$ sudo ifconfig wlan0 down
skumar@skumar:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:5b:c9:ed
Sending on   LPF/wlan0/00:0c:41:5b:c9:ed
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
skumar@skumar:~$ sudo ifconfig wlan0 up
skumar@skumar:~$ sudo iwconfig wlan0 essid "2WIRExxx"
skumar@skumar:~$ sudo iwconfig wlan0 mode Managed
skumar@skumar:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:5b:c9:ed
Sending on   LPF/wlan0/00:0c:41:5b:c9:ed
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
skumar@skumar:~$ [/PHP]
I get the same result when I put "key" command too.
Some one Can help me?
Thanks.

---

