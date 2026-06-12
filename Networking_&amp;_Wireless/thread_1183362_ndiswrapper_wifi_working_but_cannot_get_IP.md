---
title: "ndiswrapper wifi working but cannot get IP"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by kevincw01 on 2009-06-10
So I spent some time last night getting my broadcom bcm4328 wireless card working with ndiswrapper and ubuntu.  I finally got it to recognize my card and i can even get it to associate to my hotel's access point.  There are 4 access points within my area and they are all open with dhcp.  Windows has no problems associating and connecting.  So it associates but then after 30 seconds it disconnects and never gets an IP.  The error message is: "No network configuration found for the current AP".  I pasted the complete log named wpasupplicant below (not sure why wpa is involved, there is no encryption but this is the only ndiswrapper log I could find).  

FYI, I did read the ndiswrapper sticky on this forum and i am past the point...my card is recognized and can be controlled, it just can't get an IP from the access points.

Your help/tips/suggestions are appreciated, in advance.
------
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:98:e9 (SSID='Residence_Inn' freq=2437 MHz)
Associated with 00:1f:41:38:9e:69
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:9e:69 completed (auth) [id=0 id_str=]
Associated with 00:1f:41:38:98:e9
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:98:e9 completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:98:e9 (SSID='Residence_Inn' freq=2437 MHz)
Associated with 00:1f:41:38:9e:69
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:9e:69 completed (reauth) [id=0 id_str=]
Associated with 00:1f:41:38:98:e9
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:98:e9 completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:98:e9 (SSID='Residence_Inn' freq=2437 MHz)
Associated with 00:1f:41:38:98:e9
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:98:e9 completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:98:e9 (SSID='Residence_Inn' freq=2437 MHz)
Associated with 00:1f:41:38:98:e9
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:98:e9 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID 'Residence_Inn'
Authentication with 00:00:00:00:00:00 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:98:e9 (SSID='Residence_Inn' freq=2437 MHz)
Associated with 00:1f:41:38:9e:69
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:9e:69 completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:98:e9 (SSID='Residence_Inn' freq=2437 MHz)
Associated with 00:1f:41:38:98:e9
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:98:e9 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with SSID 'Residence_Inn'
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:9c:a9 (SSID='Residence_Inn' freq=2412 MHz)
Associated with 00:1f:41:38:98:e9
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:98:e9 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1f:41:38:98:e9 (SSID='Residence_Inn' freq=2437 MHz)
Associated with 00:1f:41:38:98:e9
CTRL-EVENT-CONNECTED - Connection to 00:1f:41:38:98:e9 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

---

### Post by superprash2003 on 2009-06-10
post output of 
1)iwconfig
2)ifconfig

have you tried using dhclient?

---

