---
title: "wireless on ASUS laptop 4965.  please, please, please help..."
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by worthspending on 2010-02-04
I have several desktops, servers, remote servers, and one laptop.  Since I have remote servers, I use a custom written script to install remotely via SSH.  To keep the installs uniform, I use the same
script to install on all of my machines and I have been using this method since Edgy.  I have an ASUS g2s-b2 laptop and I am having a world of trouble getting the wireless working in Karmic.  At some point,
I did actually get the wireless working in Karmic using the Gnome desktop.  However, I have not been able to get the wireless working in KDE.  Which is my desktop of choice.  Months have passed since my last attempt and
I decided to give it another try thinking that things may have resolved themselves over the past couple of months.

Here is where I stand:
- I used the script to perform fresh install of 64-bit Karmic.
- there is no gui desktop installed at this time.  gnome or KDE
- I ran:
  apt-get install linux-backports-modules-wireless-karmic-generic
  apt-get install linux-backports-modules-karmic-generic

right now, the wireless adapter appears to be disabled.  I do remember getting the wireless to breathe a little after installing backports.

here are a few more details.
lshw -C network
  *-network
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1d:60:ae:34:cb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.1.160 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:32 memory:fdec0000-fdefffff memory:fdea0000-fdebffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:d3:83:59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:fdffe000-fdffffff


dmesg | grep iwl
[    5.869760] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    5.869763] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    5.870753] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.870761] iwlagn 0000:03:00.0: setting latency timer to 64
[    5.870787] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[    5.910599] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    5.910668] iwlagn 0000:03:00.0: irq 33 for MSI/MSI-X
[    6.227609] phy0: Selected rate control algorithm 'iwl-agn-rs'
[  142.186297] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  142.771842] iwlagn 0000:03:00.0: RF_KILL bit toggled to enable radio.

I would deeply appreciate any insight.

Thanks,

Duck

---

### Post by chili555 on 2010-02-04
> ip=192.168.1.160I see your ethernet has an IP address and I'm not sure the system will be very happy trying to have two simultaneous connections. Please disconnect the cable, open a terminal and do:```
sudo ifconfig eth0 down
rfkill list
sudo rfkill unblock all
rfkill list
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <your_essid>
sudo dhclient wlan0
```You can copy and paste from the terminal to a text document and then copy and paste it here, using the ethernet connection. Thanks.

---

### Post by worthspending on 2010-02-04
ok.  this is strange.  I followed your instructions and I was able to get this thing working.  no gui installed and I was able to ping google.com, connect to another machine on my network, copy files over the network, etc.

all cool!!  then, i installed kubuntu-desktop

when the install completed and rebooted, I ran lshw -C network and both the wired and wireless interfaces WERE ENABLED.

I tried the following:

ifconfig eth0 down
rfkill list       
0: hci0: Bluetooth                            
        Soft blocked: no                      
        Hard blocked: no                      
1: phy0: Wireless LAN                         
        Soft blocked: no                      
        Hard blocked: no                      
rfkill unblock all
rfkill list       
0: hci0: Bluetooth                            
        Soft blocked: no                      
        Hard blocked: no                      
1: phy0: Wireless LAN                         
        Soft blocked: no                      
        Hard blocked: no                      
ifconfig wlan0 up 
iwconfig wlan0 essid <removed>

dhclient wlan0              
Internet Systems Consortium DHCP Client V3.1.2          
Copyright 2004-2008 Internet Systems Consortium.        
All rights reserved.                                    
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)      

Listening on LPF/wlan0/<removed>
Sending on   LPF/wlan0/<removed>
Sending on   Socket/fallback            
DHCPREQUEST of 192.168.1.126 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.126 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8     
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.1.126
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1d:60:ae:34:cb
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A ip=192.168.1.160 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fdec0000-fdefffff memory:fdea0000-fdebffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:d3:83:59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:fdffe000-fdffffff

dmesg | grep 3:00.0
[    0.340357] pci 0000:03:00.0: reg 10 64bit mmio: [0xfdffe000-0xfdffffff]
[    0.340451] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.340457] pci 0000:03:00.0: PME# disabled
[    2.121782] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.124823] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   19.888901] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.888909] iwlagn 0000:03:00.0: setting latency timer to 64
[   19.888942] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   19.929083] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   19.929157] iwlagn 0000:03:00.0: irq 33 for MSI/MSI-X
[   20.283058] iwlagn 0000:03:00.0: firmware: requesting lbm-iwlwifi-4965-2.ucode
[   20.286355] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24


I've tried to release/renew and nothing.  I don't get it.

Thanks,

Duck

---

### Post by chili555 on 2010-02-04
If you installed kubuntu-desktop, Network Manager probably came along with it, after which manual configuration won't work. Can you see the NM icon and see networks and connect?

---

### Post by worthspending on 2010-02-04
Yes, the network manager is there.  The wired connection connects at startup.  I cannot connect using the wireless connection.  I configured it, however, cannot connect.  unplugged the wired connection and it is removed from the network manager.  tried restart with wired connection unplugged and still nothing.  I've read that WCID works like a charm, but, have not installed it.  any ideas?

---

### Post by chili555 on 2010-02-04
With the wire disconnected, do you see your network? What happens when you try to connect?

---

### Post by worthspending on 2010-02-04
No I cannot see the network and cannot connect.  Can't ping anything other than localhost.

ip addr shows no IP and the state is DOWN

iwconfig shows wlan0, but, nothing is associated.

I tried using the connection manager to select the configured wireless connection and connect manually.  nothing happens.  no dialogs.  no errors.  nothing.  is there a log i can check?

---

### Post by chili555 on 2010-02-04
Please reboot with the wire disconnected and look in Network Manager and see if you see anything hopeful, like attached.
If not, please let us see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by worthspending on 2010-02-04
I uninstalled the network manager and followed the same steps from earlier in this post and I was able to connect with no problem.  Is there anything you would like me to try?

---

### Post by chili555 on 2010-02-04
If you are connected with no problem and that was your original goal, there is only one thing left to do. Mark the thread SOLVED. Of course, you could amend /etc/network/interfaces to do all the work for you automagically. Post back if you need an example.

---

### Post by worthspending on 2010-02-04
yes, config for /etc/network/interfaces would be very helpful.

---

### Post by chili555 on 2010-02-04
Here's one:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid <your_essid>

#auto eth0
iface eth0 inet dhcp
```Note that auto eth0 is commented out so it doesn't waste time trying to start with no wire attached.

Static would be:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid <your_essid> 

#auto eth0
iface eth0 inet dhcp
```Substitute your details, obviously. If you use static, don't forget nameservers in /etc/resolv.conf.

---

