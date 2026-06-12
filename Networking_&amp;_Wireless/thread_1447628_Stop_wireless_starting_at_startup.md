---
title: "Stop wireless starting at startup"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by amichael on 2010-04-05
Ubuntu 9.10
Acer 7736


This machine has a combined key/indicator light to turn the wireless networking on/off

The change of state of the switch is detected by software

with the switch off iwconfig shows

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and with it on

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Please how can I configure the wireless connection to not start?

---

### Post by Iowan on 2010-04-05
Limited as my wireless experience is...
If you use Network Manager, you *should* be able to uncheck the "Connect Automatically" box and restart/reboot.

---

### Post by amichael on 2010-04-06
Thank you.
My version NetworkManager Applet 0.7.996 does not seem to have the option you mention
There never has been any wireless connection so the enable wireless option is greyed out (and unselected)

---

