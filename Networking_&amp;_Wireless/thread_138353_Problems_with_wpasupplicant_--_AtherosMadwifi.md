---
title: "Problems with wpasupplicant -- Atheros/Madwifi"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by techflavor on 2006-03-01
I am having troubles getting my WRT54G router to assign me an IP address when  my wireless security settings are enabled.  I have it setup using WPA2 (TKIP+AES).  

I seem to have properly configured wpasupplicant because I see where it says WPA negotiation complete.  So it seems to me like it is working... See below.

```
root@techflavor:/home/chris# wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -w
ioctl[SIOCSIWPMKSA]: Operation not supported
Trying to associate with 00:06:25:c5:8b:fd (SSID='techflavor' freq=2437 MHz)
Associated with 00:06:25:c5:8b:fd
WPA: Key negotiation completed with 00:06:25:c5:8b:fd [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:06:25:c5:8b:fd completed (auth)

```

Once wpa negotiation is complete, when I do a 'iwconfig ath0', it looks like everything is right (to my knowledge):

```
root@techflavor:/home/chris# iwconfig ath0
ath0      IEEE 802.11g  ESSID:"techflavor"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:C5:8B:FD
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX   Security mode:restricted
          Power Management:off
          Link Quality=40/94  Signal level=-55 dBm  Noise level=-95 dBm
          Rx invalid nwid:4133  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

```


But whenever I attempt an 'ifup ath0', it says 'No DHCPOFFERS received'.

I have tried different security configurations using WPA but I cannot get an IP address assigned through DHCP.  

Note that I am able to get an IP address from DHCP when connected to the router using no security encryption or when using WEP.

---

### Post by firecat53 on 2006-03-03
I'm not familiar with configuring WPA2, but here's a few things to try:

1. Drop your WPA down to just WPA/PSK (TKIP) and see if that works.

2. Try assigning a static IP address. I know the older madwifi drivers had issues with WPA and dynamic IPs.

3. Try compiling WPA and madwifi from source. Perhaps WPA2 is better supported in newer versions of both

4. Also post your wpa_supplicant.conf and /etc/default/wpasupplicant if still no success. 

Good luck!

Scott

---

