---
title: "iwconfig command giving strange results"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by mike998 on 2009-12-09
I'm having some difficulty with the iwconfig command.
When I use it as a regular user, I don't get any information, however when I use it as root, I get my wireless information.  I am running 9.10 x64.  Example below of what I mean.
```
mike@Bane:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:201  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

mike@Bane:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"TWINTOWN"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-52 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:0   Missed beacon:0

```

The ultimate aim for this is to hopefully fix the problem I'm having with conky showing my ESSID as not associated when run as the normal user and showing the ESSID when run as root.  My suspicions lie with the network-manager applet.

---

### Post by mike998 on 2009-12-10
Hate to do this, but... *BUMP*

Does anybody know why iwconfig gives no output as a regular user but does when sudo'd to root?

How can I modify my system to allow iwconfig to display wireless information to the regular user?

---

