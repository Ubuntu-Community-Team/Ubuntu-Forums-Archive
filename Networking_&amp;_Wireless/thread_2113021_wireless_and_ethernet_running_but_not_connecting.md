---
title: "wireless and ethernet running but not connecting"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by Sharan Srinivas on 2013-02-06
Hey !

 im running an ubuntu 12.04 realease on my hp pavillion dv6 and i am having problems in connecting to the internet (both ethernet and wireless). i did some checking and the  results are shown below . I can see the wireless on the ethernet card accepts the lan cable, i can also see the available connections. But, i am not able to connect to any of them . it tries to connect, times out , tries again times out again and so in.  
**rfkill list all**

0:phy0:    Wireless lan
Soft blocked : no
Hard blocked : no
1:brcmwl -0 : wireless Lan
Soft blocked : no
Hard blocked : no
2:hci -0: Bluetooth
Soft blocked : no
Hard blocked : no
3:hp-wifi: wireless Lan
Soft blocked : no
Hard blocked : no
4:hp -bluetooth: Bluetooth
Soft blocked : no
Hard blocked : no
5:hp -bluetooth: Bluetooth
Soft blocked : no
Hard blocked : no

[B]sudo -lshw -C network
[/B]                                    [FONT=Liberation Sans, sans-serif]*-network               [/FONT] 
        [FONT=Liberation Sans, sans-serif]description: Wireless interface[/FONT]
        [FONT=Liberation Sans, sans-serif]product: BCM4313 802.11b/g/n Wireless LAN Controller[/FONT]
        [FONT=Liberation Sans, sans-serif]vendor: Broadcom Corporation[/FONT]
        [FONT=Liberation Sans, sans-serif]physical id: 0[/FONT]
        [FONT=Liberation Sans, sans-serif]bus info: pci@0000:0a:00.0[/FONT]
        [FONT=Liberation Sans, sans-serif]logical name: eth1[/FONT]
        [FONT=Liberation Sans, sans-serif]version: 01[/FONT]
        [FONT=Liberation Sans, sans-serif]serial: 08:ed:b9:39:bf:10[/FONT]
        [FONT=Liberation Sans, sans-serif]width: 64 bits[/FONT]
        [FONT=Liberation Sans, sans-serif]clock: 33MHz[/FONT]
        [FONT=Liberation Sans, sans-serif]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
        [FONT=Liberation Sans, sans-serif]configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg[/FONT]
        [FONT=Liberation Sans, sans-serif]resources: irq:19 memory:d4500000-d4503fff[/FONT]
   [FONT=Liberation Sans, sans-serif]*-network[/FONT]
        [FONT=Liberation Sans, sans-serif]description: Ethernet interface[/FONT]
        [FONT=Liberation Sans, sans-serif]product: RTL8111/8168B PCI Express Gigabit Ethernet controller[/FONT]
        [FONT=Liberation Sans, sans-serif]vendor: Realtek Semiconductor Co., Ltd.[/FONT]
        [FONT=Liberation Sans, sans-serif]physical id: 0[/FONT]
        [FONT=Liberation Sans, sans-serif]bus info: pci@0000:0b:00.0[/FONT]
        [FONT=Liberation Sans, sans-serif]logical name: eth0[/FONT]
        [FONT=Liberation Sans, sans-serif]version: 07[/FONT]
        [FONT=Liberation Sans, sans-serif]serial: 08:2e:5f:73:f2:55[/FONT]
        [FONT=Liberation Sans, sans-serif]size: 10Mbit/s[/FONT]
        [FONT=Liberation Sans, sans-serif]capacity: 1Gbit/s[/FONT]
        [FONT=Liberation Sans, sans-serif]width: 64 bits[/FONT]
        [FONT=Liberation Sans, sans-serif]clock: 33MHz[/FONT]
        [FONT=Liberation Sans, sans-serif]capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT]
        [FONT=Liberation Sans, sans-serif]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT]
        [FONT=Liberation Sans, sans-serif]resources: irq:43 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff[/FONT]
  
[B]                            ifconfig

[/B]
[FONT=Liberation Sans, sans-serif]sharan@sharan-PC:~$ ifconfig[/FONT]
 [FONT=Liberation Sans, sans-serif]eth0      Link encap:Ethernet  HWaddr 08:2e:5f:73:f2:55  [/FONT] 
           [FONT=Liberation Sans, sans-serif]UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
           [FONT=Liberation Sans, sans-serif]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
           [FONT=Liberation Sans, sans-serif]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
           [FONT=Liberation Sans, sans-serif]collisions:0 txqueuelen:1000 [/FONT] 
           [FONT=Liberation Sans, sans-serif]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
           [FONT=Liberation Sans, sans-serif]Interrupt:43 Base address:0xe000 [/FONT] 
 

 [FONT=Liberation Sans, sans-serif]eth1      Link encap:Ethernet  HWaddr 08:ed:b9:39:bf:10  [/FONT] 
           [FONT=Liberation Sans, sans-serif]inet6 addr: fe80::aed:b9ff:fe39:bf10/64 Scope:Link[/FONT]
           [FONT=Liberation Sans, sans-serif]UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
           [FONT=Liberation Sans, sans-serif]RX packets:0 errors:0 dropped:0 overruns:0 frame:8492[/FONT]
           [FONT=Liberation Sans, sans-serif]TX packets:0 errors:23 dropped:0 overruns:0 carrier:0[/FONT]
           [FONT=Liberation Sans, sans-serif]collisions:0 txqueuelen:1000 [/FONT] 
           [FONT=Liberation Sans, sans-serif]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
           [FONT=Liberation Sans, sans-serif]Interrupt:19 [/FONT] 
 

 [FONT=Liberation Sans, sans-serif]lo        Link encap:Local Loopback  [/FONT] 
           [FONT=Liberation Sans, sans-serif]inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
           [FONT=Liberation Sans, sans-serif]inet6 addr: ::1/128 Scope:Host[/FONT]
           [FONT=Liberation Sans, sans-serif]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
           [FONT=Liberation Sans, sans-serif]RX packets:1364 errors:0 dropped:0 overruns:0 frame:0[/FONT]
           [FONT=Liberation Sans, sans-serif]TX packets:1364 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
           [FONT=Liberation Sans, sans-serif]collisions:0 txqueuelen:0 [/FONT] 
           [FONT=Liberation Sans, sans-serif]RX bytes:108392 (108.3 KB)  TX bytes:108392 (108.3 KB)[/FONT]
  
[B]                                iwconfig
[/B]
[FONT=Liberation Sans, sans-serif]lo        no wireless extensions.[/FONT]
 

 [FONT=Liberation Sans, sans-serif]eth1      IEEE 802.11abg  ESSID:off/any  [/FONT] 
           [FONT=Liberation Sans, sans-serif]Mode:Managed  Access Point: Not-Associated   [/FONT] 
           [FONT=Liberation Sans, sans-serif]Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
           [FONT=Liberation Sans, sans-serif]Power Management:on[/FONT]
            
 [FONT=Liberation Sans, sans-serif]eth0      no wireless extensions[/FONT]
  [B]sudo /etc/NetworkManager/NetworkManager.conf
[/B]
[FONT=Liberation Sans, sans-serif]sharan@sharan-PC:~$ sudo cat /etc/NetworkManager/NetworkManager.conf[/FONT]
 

 [FONT=Liberation Sans, sans-serif][main][/FONT]
 [FONT=Liberation Sans, sans-serif]plugins=ifupdown,keyfile[/FONT]
 [FONT=Liberation Sans, sans-serif]dns=dnsmasq[/FONT]
 

 [FONT=Liberation Sans, sans-serif]no-auto-default=08:2E:5F:73:F2:55,[/FONT]
 

 [FONT=Liberation Sans, sans-serif][ifupdown][/FONT]
 [FONT=Liberation Sans, sans-serif]managed=true[/FONT]
  [B]sudo /etc/network/interfaces
[/B]
[FONT=Liberation Sans, sans-serif]sharan@sharan-PC:~$ sudo cat /etc/network/interfaces[/FONT]
 [FONT=Liberation Sans, sans-serif]auto lo[/FONT]
 [FONT=Liberation Sans, sans-serif]iface lo inet loopback[/FONT]
  
**lspci**

                                  [FONT=Liberation Sans, sans-serif]sharan@sharan-PC:~$ lspci[/FONT]
 [FONT=Liberation Sans, sans-serif]00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)[/FONT]
 [FONT=Liberation Sans, sans-serif]01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev ff)[/FONT]
 [FONT=Liberation Sans, sans-serif]08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)[/FONT]
 [FONT=Liberation Sans, sans-serif]0a:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)[/FONT]
 [FONT=Liberation Sans, sans-serif]0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)[/FONT]
  
 im not able to figure out the errors . To me, the ethernet and there wireless interface look fine. I need internet now very urgently ... can some one help me out in this   ?

I picked up those above commands by reading the posts on similar topics and i have no idea on how to proceed now. any help is greatly appreciated

---

### Post by Sharan Srinivas on 2013-02-06
UPDATE :  i went to my university to test the wireles connection. at first it did not connect. then i went to EDIT CONNECTIONS and removed all the wired and wireless connected and then reconnected to the university`s internet by creatiing a brand new connection. i was able to access the wireless but not the ethernet connection.

I then went back home and tried the same thing again , but it did not work.  I could access the SAME  wireless connection at home from a different computer and via my phone ( Samsung Galaxy S3 ) 

Sharan

---

