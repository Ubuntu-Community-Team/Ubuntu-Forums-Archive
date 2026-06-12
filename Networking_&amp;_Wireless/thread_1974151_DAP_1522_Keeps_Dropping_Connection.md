---
title: "DAP 1522 Keeps Dropping Connection"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by HouTex on 2012-05-05
I recently upgraded to 11.10 and I plan to upgrade to 12.04 in a few months.

My internet connection from one of my WAPs works great (an old Linksys), but when I connect with my newer D-Link 1522 (in our distant bedroom where the Linksys does not reach very well) I get constant freezes and disconnects.  Here is the print out of iwconfig from both WAPs.  Any help would be appreciated.

With the Linksys:

wlan0     IEEE 802.11abgn  ESSID:"*******"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:AF:F7:*********  
          Bit Rate=18 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:515   Missed beacon:0

With the D-Link DAP 1522 [note the better strenth--and it still disconnects!:

wlan0     IEEE 802.11abgn  ESSID:"*******"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C:D9:98:*********  
          Bit Rate=104 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by HouTex on 2012-05-06
Not sure I would call this "solved" but after reviewing other threads involving a similar problem, I disabled 802.11n through the DAP 1522 setup program.  I set it for only 802.11 g or b and it now works very well.  One of the threads suggested that there is a glitch in the 11.10 software for the "n" format.  It worked fine in 10.04.

---

