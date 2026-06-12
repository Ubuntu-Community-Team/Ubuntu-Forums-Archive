---
title: "Belkin USB Intermittent connection problem"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by David Miller on 2009-01-18
I have been trying to get a Belkin F5D7050A usb wireless adapter to work for the last few days. I am running Ubuntu 8.10 from a completely fresh install. The version is 3003uk

The device works  to just 'plug&play', in a limited sense. It recognises the device, connects, and serves some webpages, but then gives intermittent page load errors - the address seems valid but could not be loaded. But only for some sites. some work fine.

This is a problem because affected sites include google.com google.co.uk and ubuntuforums.org - which makes it hard to even search for the solution!

I have attempted to install the driver manually, but that broke everything & resulted in no connection at all, I have attempted to use ndiswrapper, but similarly that doesn't seem to work for me. Probably I am doing something stupid. 

Any help or advice would be much appreciated.

This is my output from lsusb: 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0411:0098 MelCo., Inc. 
Bus 003 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And this from iwconfig wlan0:

wlan0     IEEE 802.11bg  ESSID:"Belkin_N1_Wireless_12237B"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:12:23:7B   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=34/100  Signal level:-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Bit stumped here, have just moved, and a hardwire ethernet connection isn't an option anymore!

---

### Post by David Miller on 2009-01-19
Bump...

Have just discovered that this problem also stops me from accessing the Ubuntu repositories & therefore updating/installing software also... Getting to be a real headache. If anyone has any suggestions, even if it's of the level of 'Sorry that usb adapter is a pain & you're much better off getting hold of an XYZ then that would be much appreciated.

---

### Post by Rofko on 2009-03-12
Did you ever get anywhere with this? I have the veru same problem with my usb wireless, which is a d-link dwl-g122. Anyone?

---

### Post by David Miller on 2009-03-13
I have no real idea what the problem was here, the only way I solved it was by testing the USB on another machine at a friends house, where it worked fine, so I concluded that there was probably some compatibility issue with the router? 

I had another router available as it happened, and after changing it over there have been no problems...

So not really a solution, but that's what worked for me

---

