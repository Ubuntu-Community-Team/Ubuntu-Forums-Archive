---
title: "Wireless with wpa freezes my laptop"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by fbnsantos on 2010-06-14
Hello, 

I have laptop acer 5738z with ubuntu 10.04, wireless card atheros ar5b91. And when I use the wpa encryption system, after 1 to 10 min utes it freezes my laptop. Can anybody help-me with this problem?.... I use this scritp to start the connection:

rm /var/run/wpa_supplicant/wlan0
iwconfig wlan0 essid eduroam
wpa_supplicant -i wlan0 -W -D wext -c /etc/feup-wifi.conf -B  
sleep 5
dhclient wlan0
#watch -n 1 "wpa_cli status"

---

