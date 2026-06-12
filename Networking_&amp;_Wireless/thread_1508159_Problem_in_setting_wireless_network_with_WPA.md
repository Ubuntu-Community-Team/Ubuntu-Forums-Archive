---
title: "Problem in setting wireless network with WPA"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by amitkhanna on 2010-06-12
Hi 

I'm having some problem in setting up network using iwconfig with WPA. The steps i followed are:

# wpa_passphrase amit mytestkey > wpa_supplicant.conf
# sudo /etc/init.d/NetworkManager stop
# ifconfig wlan0 down
# iwconfig wlan0 essid amit
# ifconfig wlan0 up
# wpa_supplicant -iwlan0 -c./wpa_supplicant.conf

and i got the following error:

ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1e:40:d3:8a:96 (SSID='amit' freq=2412 MHz)
CTRL-EVENT-SCAN-RESULTS 
Associated with 00:1e:40:d3:8a:96
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1e:40:d3:8a:96 (SSID='amit' freq=2412 MHz)
Associated with 00:1e:40:d3:8a:96
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1e:40:d3:8a:96 (SSID='amit' freq=2412 MHz)
Associated with 00:1e:40:d3:8a:96
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1e:40:d3:8a:96 (SSID='amit' freq=2412 MHz)
Associated with 00:1e:40:d3:8a:96
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1e:40:d3:8a:96 (SSID='amit' freq=2412 MHz)
Associated with 00:1e:40:d3:8a:96
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-SCAN-RESULTS 


But when i try connecting it using network manager it works fine. I've checked the psk in wpa_supplicant.conf and network manager both are correct.

How can i solve this problem.

Thanks
Amit Khanna

---

