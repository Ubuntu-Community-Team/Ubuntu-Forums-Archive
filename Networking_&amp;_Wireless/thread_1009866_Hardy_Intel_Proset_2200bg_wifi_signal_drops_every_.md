---
title: "Hardy: Intel Proset 2200bg wifi signal drops every few minutes"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by anil_robo on 2008-12-13
I am using Hardy Heron on a laptop manufactured by a Philipino company "Neo". The wifi adapter is "Intel Corporation PRO/Wireless 2200BG Network Connection ". It was working fine as long as I used Windows xp that came pre-installed with it. But after installing Ubuntu, I notice that the signal strength keeps dropping to 0, and eventually getting disconnected. Internet has become "unbrowseable" as a result. 

Output of iwconfig:

```
 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"2wire155"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:14:95:00:BC:F9   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:E020-BF78-77CC-F4DF-77B7-9DA9-A9CF-C797-881D-1386-CF5B-04CF-785C-9B3E-70CE-6190   Security mode:open
          Power Management:off
          Link Quality=21/100  Signal level=-27 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:526  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:50
```A screenshot of Network Tools shows there are too many reception errors:

[IMG]http://img214.imageshack.us/img214/2756/screenshotdevicesnetworux3.jpg[/IMG]

Can someone tell me why is Ubuntu getting very low signal and getting disconnected every few minutes? The same laptop was working great with Windows XP before :(

---

