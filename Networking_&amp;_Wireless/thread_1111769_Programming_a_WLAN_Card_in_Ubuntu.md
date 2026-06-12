---
title: "Programming a WLAN Card in Ubuntu"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by aloknrao on 2009-03-31
Hello

I am new to Ubuntu and require some help regarding a project I have to do.
I have a laptop running Ubuntu and I am able to connect to the internet on Ubuntu without any problems. For my project, I need to find out the SSID of the AP to which the laptop is connected to? 
I want to know how this is done in Ubuntu/Linux? Is there any tutorial or guide regarding this? Please let me know.
Thanks & Regards

---

### Post by chili555 on 2009-03-31
Please open a terminal and type:```
iwconfig
```That means, roughly, 'what is my wireless configuration?' You will see something like this:> eth1      IEEE 802.11abg  ESSID:"[COLOR="Red"]mylilrouter[/COLOR]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:9F:CC:E6:EA:7C   
          Bit Rate=2 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=48/100  Signal level:-80 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0So, the ESSID that I am currently connected to is 'mylilrouter.'

---

