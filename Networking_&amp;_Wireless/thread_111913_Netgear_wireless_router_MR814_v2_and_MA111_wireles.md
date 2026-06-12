---
title: "Netgear wireless router MR814 v2 and MA111 wireless USB adaptor."
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by br14n on 2006-01-03
I cannot get these to connect, details as follows:-

I use a Medion Notebook MD2592 with Netgear Router MR814v2 & MA111 adapter.

They do not connect.

listing of /etc/network/interfaces


# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script echo
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp

iface wlan0 inet dhcp
wireless-channel 11
wireless-mode ad-hoc
wireless-essid netgear
wireless-key open

auto eth0

iwconfig wlan0
wlan0     IEEE 802.11-DS  ESSID:"netgear"  Nickname:"netgear"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:0F:C8:75:F6:CF
          Bit Rate:2 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=0/92  Signal level=-100 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:58:35:CE
                    ESSID:"netgear"
                    Mode:Master
                    Encryption key:off
                    Channel:11
                    Quality:40/92  Signal level:-48 dBm  Noise level:-88 dBm

lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0846:4110 NetGear, Inc.
Bus 001 Device 001: ID 0000:0000
lshw
 *-usb
                   description: Generic USB device
                   vendor: NetGear, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.32
                   capabilities: usb-1.configuration: driver=prism2_usb maxpower=500mA speed=12. Mb/s

*-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: 90
             serial: 00:40:ca:bd:c7:7c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 ip=192.168.0.2 multicast=yes
             resources: ioport:1800-18ff iomemory:e0005000-e0005fff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:03:f6:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

 *-usb
                   description: Generic USB device
                   vendor: NetGear, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.32
                   capabilities: usb-1.10
                   configuration: driver=prism2_usb maxpower=500mA speed=12.0MB/s

This computer has Ubuntu 5.10 installed & dual boots with XP, with which this equipment works OK.
I wonder if anyone can offer any advice on this?

---

### Post by cwaldbieser on 2006-01-03
[QUOTE=br14n]I cannot get these to connect, details as follows:-

I use a Medion Notebook MD2592 with Netgear Router MR814v2 & MA111 adapter.

They do not connect.

listing of /etc/network/interfaces


# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script echo
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp

iface wlan0 inet dhcp
wireless-channel 11
wireless-mode ad-hoc
wireless-essid netgear
wireless-key open

auto eth0

iwconfig wlan0
wlan0     IEEE 802.11-DS  ESSID:"netgear"  Nickname:"netgear"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:0F:C8:75:F6:CF
          Bit Rate:2 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=0/92  Signal level=-100 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:58:35:CE
                    ESSID:"netgear"
                    Mode:Master
                    Encryption key:off
                    Channel:11
                    Quality:40/92  Signal level:-48 dBm  Noise level:-88 dBm

lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0846:4110 NetGear, Inc.
Bus 001 Device 001: ID 0000:0000
lshw
 *-usb
                   description: Generic USB device
                   vendor: NetGear, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.32
                   capabilities: usb-1.configuration: driver=prism2_usb maxpower=500mA speed=12. Mb/s

*-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: 90
             serial: 00:40:ca:bd:c7:7c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 ip=192.168.0.2 multicast=yes
             resources: ioport:1800-18ff iomemory:e0005000-e0005fff irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:03:f6:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

 *-usb
                   description: Generic USB device
                   vendor: NetGear, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.32
                   capabilities: usb-1.10
                   configuration: driver=prism2_usb maxpower=500mA speed=12.0MB/s

This computer has Ubuntu 5.10 installed & dual boots with XP, with which this equipment works OK.
I wonder if anyone can offer any advice on this?[/QUOTE]

Here is a little script I use to get mine working.  It required installing the prism2 driver.

```

#!/bin/bash
 
#My wireless network initialization.
modprobe prism2_usb
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=NETGEAR authtype=opensystem
sudo dhclient

```
This script assumes the system is open and the network name is the default, NETGEAR.  You can change the settings once you get it up and running.

---

### Post by Lambert on 2006-01-03
>  wireless-mode ad-hoc 
Why are you running in ad-hoc mode?

> In computer networking, **ad-hoc** is a connection method for wireless LANs that requires no base station &#8212; devices discover others within range to form a network for those computers. 
If you are connecting to a router/access point change this from ad-hoc to managed.

---

### Post by br14n on 2006-01-04
Many thanks to you both for your help, after many hours of getting nowhere I can now connect to the internet without my wired connection. Fantastic!!.
However, I'm running in open mode & now  I must try WEP. I will let you know how I  get on!
Brian.

---

### Post by az on 2006-01-04
[QUOTE=br14n]Many thanks to you both for your help, after many hours of getting nowhere I can now connect to the internet without my wired connection. Fantastic!!.
However, I'm running in open mode & now  I must try WEP. I will let you know how I  get on!
Brian.[/QUOTE]

There is a bug report about this device. It is apparently supposed to work out-of-the-box once you install linux-wlan-ng. You should be able to set up your device and connect on boot with the networking Gnome GUI tool.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

What I need to do to get it to work is to put this script into /etc/hotplug/usb/prism2_usb

Being that the module is hotplug loaded, that script is run when it is plugged in.

Here it is:
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="####PUTYOURWEPHE RE!!!!!###"
wlanctl-ng wlan0 lnxreq_autojoin ssid="###PUT you essid here###" authtype="sharedkey"
sleep 2
dhclient wlan0


(Put your wep where indicated...)

I have used this device for a while and it used to be flakey. Even in windows, it only connects half the time. However, using the prism2_usb driver and this script, it never fails. It is an unelegant solution, but it works for me.


Add to the bug report, please, since it seems to apply to you.  Thanks!

---

### Post by br14n on 2006-01-04
Thanks AZZ for your advice, however I have decided for the present, to turn on the access control together with 
an access control list which allows access to designated MAC addresses only. I'm concerned to read that people have reported problems with encryption. So I'll see how it goes and I may well try this out later. Thanks once again,
Brian.

---

