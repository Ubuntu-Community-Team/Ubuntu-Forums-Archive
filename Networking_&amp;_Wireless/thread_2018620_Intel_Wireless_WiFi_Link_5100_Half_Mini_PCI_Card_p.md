---
title: "Intel Wireless WiFi Link 5100 Half Mini PCI Card problem"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by sn0m on 2012-07-06
Hi Guys
I can't connect to wireless router in 2.4GHZ band. Does anyone know any solution to it?
the following are my wireless specs:
sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 00
       serial: 00:22:fb:4c:14:bc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=8.83.5.1 build 33692 ip=192.168.0.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:dea00000-dea01fff

 IEEE 802.11abgn  ESSID:"default"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C4:3D:C7:3D:37:43   
          Bit Rate=48 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:143   Missed beacon:0

eth0      no wireless extensions.

???? any help is appreciated
thanks
sokol

---

### Post by praseodym on 2012-07-06
Did you deactivate the N-mode (bug!)?
> 
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

---

### Post by sn0m on 2012-07-07
> **praseodym said:**
> Did you deactivate the N-mode (bug!)?

Hi
thanks for your response.
I did all the above but still can't connect. It can see the router but dosen't connect, ie asking for the password again, while it is fine in the 5 ghz band.

---

### Post by praseodym on 2012-07-07
Deactivate the N-Mode in your router.

---

