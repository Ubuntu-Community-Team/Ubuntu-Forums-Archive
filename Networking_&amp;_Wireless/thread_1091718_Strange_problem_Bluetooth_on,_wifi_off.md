---
title: "Strange problem: Bluetooth on, wifi off?"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by _Smiler_ on 2009-03-09
I am having trouble with extremely slow internet ever since I reinstalled Ubuntu the other day, my Bluetooth light is on and my wifi light is off? Could this explain the insufferably slow connection? I've searched all over google as I'm sure it's just a case of a simple terminal command.

Could someone please help, I have 245 updates to get through and god knows how many emails awaiting deletion :)

Asus F5SR,Ubuntu 8.10

this is the output of lshw
> description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:43:21:33:39
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.64 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn


iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHomeHub2-MJ9N"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:4E:01:A7:B6   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=32/100  Signal level:-74 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


ndiswrapper -l
> setup : invalid driver!


I've tried downloading the windows driver from Asus' website - it's a zip file. When I extract it, it doesn't seem to have a .inf file, just .ini. Nor a .sys for that matter. It does have a .dll. I cannot extract it's setup.exe through cabextract nor unshield - i get the error no valid cabinets found.

iwconfig wlan0 up
> iwconfig: unknown command "up"

I can't think of anymore commands that might be useful.

Thanks to anyone that might be able to help!

---

