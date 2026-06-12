---
title: "Configuring dlink router in Ubuntu 12.04 LTS"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by sandy0594 on 2013-04-11
Hi All,

I have been using Ubuntu for a while,recently I switched my router from ADSL to a wifi one (DLINK DIR-600L).My internet connection is a PPPOE.My ISP guy configured it for me to work in Windows(W7).But when i try to use internet from Ubuntu(12.04 LTS) I can't able to connect it.

When I was on wired connection I was able to access internet

When I hit ifoconfig in terminal,this is what I get

```

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:50:83:1f  
          inet6 addr: fe80::beae:c5ff:fe50:831f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:43996 (43.9 KB)  TX bytes:7756 (7.7 KB)
          Interrupt:45 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

Can someone please guide me how to configure ubuntu network settings so that I can access internet.

Thanks in advance!!

---

### Post by ahallubuntu on 2013-04-11
~

---

### Post by sandy0594 on 2013-04-11
> **ahallubuntu said:**
> You mean, you are trying to use wireless/wifi to access your D-Link router instead of a wired connection?

If so, whats' the output of this command:

sudo lshw -C network

Yes I am using wifi router(DLINK WIRELESS N 150 ROUTER DIR-600L) now.For my PC I am connecting it through cable(from dlink router).
DLINK router is connected to a ADSL motorola modem(ISP provider's)

This is the o/p I got when i hit sudo lshw -C network

```

 *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:50:83:1f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:45 memory:febc0000-febfffff ioport:ec00(size=128)

```

---

### Post by sandy0594 on 2013-04-13
Installed n/w drivers but still can't access internet

When i hit [COLOR=#000000] sudo lshw -C network,this is what i got now[/COLOR]
```

*-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:50:83:1f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:45 memory:febc0000-febfffff ioport:ec00(size=128)



```

Any ideas,why I can't access internet still?

---

### Post by Iowan on 2013-04-13
Does **ifconfig** now show info for wireless?

---

### Post by sandy0594 on 2013-04-13
This is what I get when i hit ifconfig

```

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:50:83:1f  
          inet6 addr: fe80::beae:c5ff:fe50:831f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:15574 (15.5 KB)  TX bytes:4549 (4.5 KB)
          Interrupt:45 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



```

---

### Post by Iowan on 2013-04-13
Sorry, I think I'm still confused...
eth0 appears to be a wired connection. Does wireless come into play, or are you using the DLink primarily as a router?

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by sandy0594 on 2013-04-13
I think I am confusing you guys.It's just I have DLink router,but for PC I still have wired access through this router using **ethernet cable**

---

### Post by Iowan on 2013-04-13
That's what I was beginning to wonder...
Does the DLink have a DHCP Server - and is Ubuntu (via Network Manager) configured to get DHCP address? Otherwise, you may need to set up a static address.

---

### Post by sandy0594 on 2013-04-13
When I go to network manager it's not allowing me to add any new connections either wired or wireless,don't know what to do.Can you guide me how to configure DHCP via network manager or probably terminal?

---

### Post by sandy0594 on 2013-04-13
Hey Guys,

Tried the below lines and now I am able to access internet..:)

```


sudo nano /etc/NetworkManager/NetworkManager.conf[COLOR=#222222][FONT=Verdana]
```Changed [/FONT][/COLOR][FONT=Ubuntu Beta] the line [/FONT]*managed=false*[FONT=Ubuntu Beta] to [/FONT]*managed=true * and ```
[COLOR=#222222]sudo service network-manager restart[/COLOR]
```

Source:[http://askubuntu.com/questions/71159/network-manager-says-device-not-managed](http://askubuntu.com/questions/71159/network-manager-says-device-not-managed)
Thanks all for your support

---

### Post by varunendra on 2013-04-13
> **sandy0594 said:**
> Hey Guys,

Tried the below lines and now I am able to access internet..:)

```


sudo nano /etc/NetworkManager/NetworkManager.conf[COLOR=#222222][FONT=Verdana]
```Changed [/FONT][/COLOR][FONT=Ubuntu Beta] the line [/FONT]*managed=false*[FONT=Ubuntu Beta] to [/FONT]*managed=true * and ```
[COLOR=#222222]sudo service network-manager restart[/COLOR]
```

Source:[http://askubuntu.com/questions/71159/network-manager-says-device-not-managed](http://askubuntu.com/questions/71159/network-manager-says-device-not-managed)
Thanks all for your support

Which means that eth0 interface is being handled by **/etc/network/interfaces** file also. Normally, it is not a good idea for a common interface to be managed by multiple mechanisms, hence the default behaviour of NM is to ignore interfaces that appear in /etc/network/interfaces file.

Since the interface is working fine now, there is no need for any further treatment, but just in case you face any issues again regarding ethernet (like settings changing by themselves), consider backing up the file and removing the 'eth0' related entries from it -
```
cd /etc/network
sudo cp interfaces interfaces.bak
gksu gedit interfaces
```

Remove all the lines related to 'eth0' interface, proofread, save and close the file.

A standard /etc/network/interfaces file has only these entries -
> auto lo
iface lo inet loopback

Enjoy!

---

### Post by sandy0594 on 2013-04-14
Looks like my network setting were short lived,today when i booted to Ubuntu it's not picking any network and as per @varunendra advice I managed to have just the below lines

```
[COLOR=#000000]*auto lo*[/COLOR]
[COLOR=#000000]*iface lo inet loopback*[/COLOR]
```



Tried restarting netowrk-manager and saw that in network-manager.conf managed = true only

What can I do next to access internet?
Thanks in advance!!

---

### Post by steeldriver on 2013-04-14
Can you post the outputs of these commands please?

```

nmcli nm status

nmcli dev status

nmcli con status

nmcli dev list iface eth0

```

---

### Post by sandy0594 on 2013-04-14
Below are the o/p's

```

sandy@ubuntu:~$ nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         disconnected    enabled         enabled    enabled         disabled  
sandy@ubuntu:~$ nmcli dev status
DEVICE     TYPE              STATE        
eth0       802-3-ethernet    disconnected 
sandy@ubuntu:~$ nmcli con status
NAME                      UUID                                   DEVICES    DEFAULT  VPN   MASTER-PATH                                 
sandy@ubuntu:~$ nmcli dev list iface eth0
GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           802-3-ethernet
GENERAL.VENDOR:                         Atheros Communications Inc.
GENERAL.PRODUCT:                        AR8151 v2.0 Gigabit Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.HWADDR:                         BC:AE:C5:50:83:1F
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     not connected
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     10 Mb/s
WIRED-PROPERTIES.CARRIER:               on



```

---

### Post by steeldriver on 2013-04-14
Does the module appear to be loaded this time?

```
lsmod | grep atl
```

It's odd that it was working for a while - I seem to recall people having to pull the atl1c driver in from compat-wireless (yes I know it's not wireless!) in the past but I don't know what would cause it to work yesterday then not today

Obviously try a different cable if you have one - just so we can rule out that it really is 'disconnected'

EDIT: can we also see the PCI ID just to check that atl1c is listed as the correct driver?

```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

---

### Post by sandy0594 on 2013-04-14
Thanks for your reply,here are the Outputs 

```
$ lsmod | grep atlatl1c                  36718  0
$ lspci -nn | grep -e '\[0200\]' -e '\[0200\]'
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)

```

There's no chance that there's some problem with lan port.It's working well for my other O.S(W7)

---

### Post by varunendra on 2013-04-14
Can you confirm what Iowan asked in post #10? Since you have removed eth0 related entries from /etc/network/interfaces file, you won't have the problem in changing settings in NM as you mentioned in post #11.

Notice this part in your nmcli dev list command output -
> CAPABILITIES.SPEED:                     10 Mb/s
It means you are physically connected and a speed has been negotiated, although it is not a good one (should be at least 100 Mbps unless the router is really ancient), but that we fix later with 'mii-tool' command.

Also, double check your /etc/network/interfaces file, then change the "managed=true" back to "false" in NetworkManager.conf file.

I have the same card with same driver in my laptop, so can confirm that the default driver is good (at least in kernel 3.2.0-36).

---

### Post by wildmanne39 on 2013-04-14
Hi, managed=true should be managed=false if you are now letting network manager manage your connections.
Thanks

---

### Post by sandy0594 on 2013-04-14
As per your suggestions,modified the network-manager.conf from managed=true to false and created a new wired connection by giving device MAC address and IP4 is automatic(DHCP).Now,I am able to access internet.Even rebooted the PC and it works fine.

Thanks all for your replies and support!!

---

### Post by varunendra on 2013-04-15
> **sandy0594 said:**
> Now,I am able to access internet.Even rebooted the PC and it works fine.

Congrats! Hope it stays this way this time :)

---

### Post by wildmanne39 on 2013-04-15
Glad it is working.
Enjoy!!!

---

