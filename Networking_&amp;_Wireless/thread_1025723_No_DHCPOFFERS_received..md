---
title: "No DHCPOFFERS received."
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by firmamentalfalcon on 2008-12-30
I've looked online and followed many guides and can't seem to get internet to work reliably.  I have a Thinkpad X61 running Xubuntu through Wubi.  I have tried Ubuntu and Kubuntu already and internet does not work on those either.  I've tried Network Manager, Wicd, and command line interface.

Wicd was able to connect for a few minutes twice (was able to visit [www.google.com](www.google.com)) but it usually gets stuck at obtaining ip address.  Network Manager and Wicd sometimes show that they are connected, but pinging google (64.233.169.99) cannot find google. 

When Wicd says it is connected but cannot ping, (The 1 Mb/s is also sometimes a higher number like 48 Mb/s but it still cannot ping)
Here's my lshw.  I believe the driver is there.
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: **:**:**:**:**:**
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=***.***.*.*** latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g 


iwconfig gives:
ath0      IEEE 802.11g  ESSID:"**********"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-51 dBm  Noise level=-98 dBm
          Rx invalid nwid:57918  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig gives
ath0      Link encap:Ethernet  HWaddr **:**:**:**:**  
          inet addr:***.***.*.***  Bcast:***.***.*.***  Mask:255.255.255.0
          inet6 addr: ****::***:****:****:****/** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1240 (1.2 KB)  TX bytes:9687 (9.6 KB)

-----------------------------------------------------------------
When I use command line, I followed these instructions: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

After running, I get
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The few times I got the lease, iwconfig shows that I was connected but I wasn't able to ping google either.

I have also tried the pci=noacpi when loading xubuntu.  I've followed a lot of guides already and it would be great if someone points me in the correct direction.

---

