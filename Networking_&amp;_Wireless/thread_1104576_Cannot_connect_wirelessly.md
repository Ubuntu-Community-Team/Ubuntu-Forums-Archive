---
title: "Cannot connect wirelessly"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by RoyT on 2009-03-23
I am running ubuntu version 8.04 and have just run the update.
I am using a Netgear RangeMax WNDR 3300. I am running both N and G with security set to WPA-PSK[TKIP] + WPA2-PSK[AES] with a passphrase that contains numbers, letters, and an @ sign. Friends with MACs and Windows laptops have not had a problem connecting. I have been using Ubuntu and have put in on an old Dell 600M laptop and am trying to get the wireless to connect.
It appears the radio is working OK as I got as far as getting wireless networks to show up under the Networking icon. The panel shows the ESSID and a signal indicator (orange bar). So, I assume that there is at least radio communication.
But, when I select my network and type in the passphrase in the panel that pops-up, nothing more happens. I realize that this could be a fault with the access point, but the fact that others can connect leaves me at a loss as to what might be the problem. Below are outputs from 
sudo lshw -C network
ifconfig
iwconfig
(most of which I do not understand)
Also, while experimenting I changed the "hosts" entries under system->administration->network for wireless.
There were two entries like
127.0.1.1 foo-laptop
127.0.1.1 localhost
originally. Now, I cannot recover that same configuration. It wants to only have one or the other. Or, if I put them on one line they show up on one line and not on two separate lines that I saw before I started messing with it. Does this matter and if so how can I get things back the way they were?

Thanks... below is the output (BTW, I am sending this from the laptop using the wired connection.)

rt@foo-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a3:4d:a0
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.16 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:04:23:6f:c7:a9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated



rt@foo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:a3:4d:a0  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fea3:4da0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1166180 (1.1 MB)  TX bytes:178037 (173.8 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:6f:c7:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rt@foo-laptop:~$ 
rt@foo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"foonet-N"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

