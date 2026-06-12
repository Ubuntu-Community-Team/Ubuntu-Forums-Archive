---
title: "WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2011-07-05
I'm running 11.04 (64bit) and have been running my own mail server for quite some time. When I couldn't retrieve my mail this morning from another machine, I checked the mail server and found the following errors in syslog
-------------------------------
Jul  6 06:46:12 ml wpa_supplicant[1113]: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
Jul  6 06:46:12 ml wpa_supplicant[1113]: WPA: Invalid EAPOL-Key MIC - dropping packet
Jul  6 06:51:00 ml wpa_supplicant[1113]: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
Jul  6 06:51:00 ml wpa_supplicant[1113]: WPA: Invalid EAPOL-Key MIC - dropping packet
Jul  6 06:51:01 ml wpa_supplicant[1113]: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
Jul  6 06:51:01 ml wpa_supplicant[1113]: WPA: Invalid EAPOL-Key MIC - dropping packet
Jul  6 07:09:01 ml CRON[31078]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 07:17:02 ml CRON[31095]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 07:20:15 ml wpa_supplicant[1113]: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK

-------------------------------------------------------

I 'fixed' this by clicking on the network icon in the menu bar, which seemed to just reconnect

running iwconfig I get

---------------------------
wlan0     IEEE 802.11bgn  ESSID:"TheAustrians2"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1F:33:23:E7:3C   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:306  Invalid misc:8261   Missed beacon:0
---------------------------------

Given that this is my mail server, I'd appreciate if anybody has any suggestions/explanations

Thanks

---

