---
title: "Belkin F5D7050 v4001 - Need to configure on ubuntu 8.04"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by rameshbabukv on 2009-05-16
I am trying to configure the **Belkin F5D7050 v4001** on Ubuntu 8.04. 
I am using Linux Kernel 2.6.24-22-generic/
From the forum I understood that v4001 is supported in this kernel.

lsusb on my terminal yields the following:

Bus 002 Device 005: ID 050d:705c Belkin Components

iwconfig commands outputs the following:

[B]lo        no wireless extensions.

eth251    no wireless extensions.

eth227    IEEE 802.11b/g  ESSID:"Antharjaala"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/B]
I have cofigured my ADSL modem in DHCP mode. I have verified the connectivity between Belkin USB adaptor and ADSL modem, which works fine with Windows Vista.

I am not sure why does it detect the interface as "eth227" instead of "wlan0".

I have installed ubuntu on HP dv6000 laptop, on which built-in wlan is not working anymore.

I need to get Belkin modem working on Ubuntu. I searched and researched the forums about the Belkin adoptors, none of them are conclusive

Any help?

Thanks
Ramesh.

---

