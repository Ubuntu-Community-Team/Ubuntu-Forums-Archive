---
title: "Wireless disconnecting after unplugging laptop - but power management off"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by ruthi13 on 2012-05-07
Hi again!

Thanks for all the help last time - turns out I just needed the network key instead of the password! D'uh!

I now have another problem though - the wireless disconnecting after the power source is unplugged. Apparently, power management is off so doesn't seem to be that. I'm not a programmer so any info given will have to be really step-by-step!

Here's the iwconfig code:

ruth@letni:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BTHub3-8G79"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:3B:8C:50:EA   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

Any use?

Thanks in advance - I'm getting puzzled! Ruth.(Ubuntu 11.10)

---

### Post by ruthi13 on 2012-05-07
Addition to above: wireless also disconnects and refuses to reconnect after suspension/hibernating too!

---

