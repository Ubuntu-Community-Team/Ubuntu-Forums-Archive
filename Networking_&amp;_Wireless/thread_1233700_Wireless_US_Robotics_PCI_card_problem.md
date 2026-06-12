---
title: "Wireless US Robotics PCI card problem"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Aspra on 2009-08-07
I have a weird situation where the network card (USR5416) is detected and locates my network, and several other around my neighborhood but does not connect to it. This is in Live disc mode, so I thought ill just install ubuntu and figure it out then. Well I installed ubuntu, and now it doesn't detect my network or any other one. I am using 9.04. 

Thanks for any help, US Robotics is pretty bad when it comes to Linux.





specs:
- EVGA 790i Motherboard
- Intel Quad core 9300
- EVGA 8800gts 512

---

### Post by superprash2003 on 2009-08-07
post output of 
1)lshw -C network
2)sudo iwlist scanning
3)iwconfig

---

### Post by Aspra on 2009-08-09
> **superprash2003 said:**
> post output of 
1)lshw -C network
2)sudo iwlist scanning
3)iwconfig

sudo iwlist scanning:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

lshw -C network:
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: wlan0
       version: 00
       serial: 00:c0:49:cc:1f:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=32 module=acx multicast=yes wireless=IEEE 802.11b+/g+


iw config:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"USR5465"  Nickname:"acx v0.3.36"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=31/100  Signal level=4/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by RedSingularity on 2009-08-10
What is your lspci output?

---

### Post by superprash2003 on 2009-08-12
doesnt seem to detect any now.. output says NO SCAN RESULTS.. some wifi cards come with a wifi switch , check to make sure its ON

---

