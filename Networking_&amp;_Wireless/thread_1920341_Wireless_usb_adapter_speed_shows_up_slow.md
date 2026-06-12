---
title: "Wireless usb adapter speed shows up slow"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by FireFighter on 2012-02-04
I recently purchased a Panda usb wireless n adapter for an old laptop. It was advertised to operate up to 150Mps. However, the connection information says that it is connected only at 54Mps. I bought this to replace a pcmia wireless g card rated at that speed. Any ideas on how to get this up to the advertised speed or at least faster than it is now?

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"*******"  Nickname:"RT3070STA"
          Mode:Managed  
          Frequency=2.437 GHz  
          Access Point:30:46:9A:42:43:F6   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-51 dBm  
          Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  
          Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   
          Missed beacon:0

lsmod | grep rt2
rt2870sta             461811  1

Any pointers and help would be greatly appreciated!

Firefighter

---

