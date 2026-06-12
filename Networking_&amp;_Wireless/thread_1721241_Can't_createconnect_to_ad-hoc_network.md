---
title: "Can't create/connect to ad-hoc network"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by Vorisaj on 2011-04-04
Hi, i have ubuntu 11.04 (try 10.04... same problem) and ACER aspire 1360. I see all ah-hoc networks around, but i cant connect. It still connecting and after one minutes it disconnected. :( I try to connect to Ad-hoc network with WPA,WEP and with no security... same result. If i try to create network, same... connecting and after one minute disconnected. 

I have wifi router with infrastructure mode(security: WEP key) and i have no problem. I can connect.

Syslog -> trying to create network( name: "asd" )
```
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0) starting connection 'asd'
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0/wireless): connection 'asd' requires no security.  No secrets needed.
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Config: added 'ssid' value 'asd'
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Config: added 'mode' value '1'
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Config: added 'frequency' value '2412'
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Config: added 'key_mgmt' value 'NONE'
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> Config: set interface ap_scan to 2
Apr  4 14:26:33 Pukkynator wpa_supplicant[915]: Trying to associate with SSID 'asd'
Apr  4 14:26:33 Pukkynator kernel: [ 1936.238661] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C0010015)
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  4 14:26:33 Pukkynator NetworkManager[812]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  4 14:27:33 Pukkynator NetworkManager[812]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Apr  4 14:27:33 Pukkynator NetworkManager[812]: <info> (wlan0): device state change: 5 -> 9 (reason 11)
Apr  4 14:27:33 Pukkynator NetworkManager[812]: <warn> Activation (wlan0) failed for access point (asd)
Apr  4 14:27:33 Pukkynator NetworkManager[812]: <info> Marking connection 'asd' invalid.
Apr  4 14:27:33 Pukkynator NetworkManager[812]: <warn> Activation (wlan0) failed.
Apr  4 14:27:33 Pukkynator NetworkManager[812]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Apr  4 14:27:33 Pukkynator NetworkManager[812]: <info> (wlan0): deactivating device (reason: 0).


```any ideas?

---

### Post by Vorisaj on 2011-04-06
anyone? :(

---

### Post by rockstarsavin on 2011-05-01
Same problem, it was working with 10 when i upgraded to 11, it says connected and show the connected icon, but I cannot access the internet and when I ping the default gateway 192.168.0.1 there is no reply. But surprisingly I am able to connect to other adhoc networks not mine. Now I have to use windows to access internet. 

Please Gurus, Help !!!!!!!!!!!!1

---

### Post by SuperBo on 2011-05-06
I have the same problem, how can I fix this.

---

