---
title: "Wireless not connecting"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by NewBee2113 on 2010-08-21
Cannot get wireless to connect.  I am pretty sure drivers and everything works because wireless authentication comes up, but when I enter password (which I know is correct as a windows laptop I have next to me works) nothing happens.

Also, the wireless finder (similar to MAc Airport) logo keeps "spinning like a pinwheel.

Here is iwconfig:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Please help. I have Ethernet plugged in, but need Wifi for laptop.

It is a Gateway (a bit old) with Realtek 8185 

Thanks

---

### Post by NewBee2113 on 2010-08-29
help, please....

---

### Post by dineshs on 2010-08-30
Did you ensure that the wireless is enabled in the router?
And regarding security
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)

---

### Post by NewBee2113 on 2010-09-11
Yes, I am sure.  I am sitting next to my ubuntu computer with my other wireless laptop and it works fine, and use the same password.

---

### Post by MaindotC on 2010-09-11
Your output indicates that your wireless card isn't operating or configured properly.  I know you said authentication pops up, but are you sure that's the network authentication or is that the password for your keyring?  Just to be sure, please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).

Assuming that your wireless card is operating as it should then is there any way you can disable the protection on the access point and just ensure you can connect to it?  If you can then we can verify your card is working and that it would be an issue with the authentication.

---

