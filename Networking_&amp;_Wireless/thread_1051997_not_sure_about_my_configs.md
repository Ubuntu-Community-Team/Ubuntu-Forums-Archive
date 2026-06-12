---
title: "not sure about my configs"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by AndreyPutilov on 2009-01-27
Hello
I`ve installed Ubuntu 8.10 on my notebook and realised that there is no driver for my Atheros AR242x wireless adapter. I installed madwifi drivers, and I see the list of networks. But it is a problem to connect. When I try 30 times 1 of them succeedes.
I am not sure that everything properly configured.
Here is the output of some commands:

andrey@ANDREY:~$ sudo lshw -C network
[sudo] password for andrey: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:4e:42:9b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:e1:90:ac:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:b7:40:e6:0e:8f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
andrey@ANDREY:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:4F:62:14:01:45   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:2298  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

andrey@ANDREY:~$ tail -f /var/log/messages
Jan 27 15:59:29 ANDREY pppd[5987]: Connect: ppp0 <--> /dev/ttyACM0
Jan 27 15:59:29 ANDREY pppd[5987]: CHAP authentication succeeded: Congratulations!
Jan 27 15:59:29 ANDREY pppd[5987]: CHAP authentication succeeded
Jan 27 15:59:29 ANDREY kernel: [  234.519301] PPP BSD Compression module registered
Jan 27 15:59:30 ANDREY kernel: [  234.561397] PPP Deflate Compression module registered
Jan 27 15:59:31 ANDREY pppd[5987]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 27 15:59:31 ANDREY pppd[5987]: local  IP address 10.20.52.132
Jan 27 15:59:31 ANDREY pppd[5987]: remote IP address 10.64.64.64
Jan 27 15:59:31 ANDREY pppd[5987]: primary   DNS address 217.77.161.130
Jan 27 15:59:31 ANDREY pppd[5987]: secondary DNS address 217.77.161.131
Jan 27 16:15:54 ANDREY -- MARK --
Jan 27 16:35:54 ANDREY -- MARK --

Thanks

---

