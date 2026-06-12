---
title: "USB wireless adapter listed as device not ready"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by jamesya on 2010-06-11
Hi

I am new to linux.  for the past three days I have been trying to install a usb wireless adapter (a second wireless card  in addition to the build into my machine)

the card type is EW-7711USN  based on Ralink chipset of  RT3070STA. 

I downloaded the latest driver from here [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
and followed the instructions here : [http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870)

but so far all I've managed to accomplish is have the adapter going from "disconnected" to not ready

can anybody please help me move forward with this ?

my iwconfig output is :


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Gateway9"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:1B:C0:B0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

your help will be greatly apreciated

---

### Post by jeffus_il on 2010-06-14
I'm about to try this myself:

> Works with 8.04 LTS - RT3070STA driver from Edimax compiles (need to compile with support for NetworkManager, also need to copy RT2870STA.dat as RT3070STA.dat in driver root directory), connects to open and WPA networks, monitor mode doesn't work. Newer RT3070 driver from Ralink compiles, but card is not recognized.

From here:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

---

### Post by jeffus_il on 2010-06-14
Got it working using the rt3070sta driver from the Ralink site.
It needs two changes, one in the code to resolve usb errors when loading the module,
another renaming the file RT2870STA.dat and making an addition to /etc/Wireless.

If you need the details, send me a private message and I'll post them, I don't remember the exact ones now.

---

