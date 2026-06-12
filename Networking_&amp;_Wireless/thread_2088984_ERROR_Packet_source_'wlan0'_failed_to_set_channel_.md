---
title: "ERROR: Packet source 'wlan0' failed to set channel 2: mac80211_setchannel() in Kismet"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by mcunille on 2012-11-27
I have installed Ubuntu 12.10 in my computer with an Atheros AR5007 wireless card.
  I want to use Kismet but when I run it it starts displaying the message:

**ERROR: Packet source 'wlan0' failed to set channel *X*: mac80211_setchannel()**

  It keeps displaying the same for every channel except channel 1. I have installed the [compat-wireless-3.6.6-1]("http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases") drivers and patched them with the following [patch]("http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch") in order to use them with aircrack-ng.

  I have installed the latest version of Kismet in the git repository  and I even tried with the svn but it keeps displaying the same error. I  also have set the kismet.conf file with the *ncsource=wlan0* as it is the name of my wireless interface according to iwconfig : 
  ```

lo        no wireless extensions.  

wlan0     IEEE 802.11bg    ESSID:"XXXX"             
Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX              
Bit Rate=18 Mb/s   Tx-Power=20 dBm              
Retry  long limit:7   RTS thr:off   Fragment thr:off           
Power Management:off           
Link Quality=28/70  Signal level=-82 dBm             
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           
Tx excessive retries:0  Invalid misc:282   
Missed beacon:0
```I haven't found any answer since similar errors are supposed to be  fixed with the latest Kismet release but this isn't my case. Any help  will be appreciated. 

  Thank you!

---

