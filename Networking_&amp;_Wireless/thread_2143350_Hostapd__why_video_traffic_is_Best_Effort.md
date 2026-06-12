---
title: "Hostapd : why video traffic is Best_Effort ?"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by Balb on 2013-05-08
Hello !

I set up a testbed to watch video streaming traffic over 802.11 WLAN.
So I used a Linux computer as AP with ath9k_htc driver and Hostapd.
But when I sniff the traffic with Wireshark, frames that carrying video have QoS Control but it's Best Effort Access Category and I would like theese frames are in Video Access Category. 

Does someone know where is the probleme ?

Here is my hostapd conf file :
```
interface=wlan2bridge=br0
driver=nl80211
ssid=testlabo
hw_mode=g
channel=1
wmm_enabled=1
```

I already tried with the complete conf file with all WMM caracteristics but it didn't change anything...

Thanks,

---

### Post by Balb on 2013-05-14
Up ?!

---

### Post by amare87 on 2013-09-02
Sometimes you have to change the incoming video traffic manually. try iptables command to change the DSCP value and it suppose to map with AC. Refer the link for DSCP and AC mapping [http://www.teldat.org/portal/downloadcenter/dateien/workshops/current_en/ws_wlan_html_en_HTML/vowlan_infra_qos_wmm.html](http://www.teldat.org/portal/downloadcenter/dateien/workshops/current_en/ws_wlan_html_en_HTML/vowlan_infra_qos_wmm.html) 
Here is a command that can be used to set traffic to video "iptables -t mangle -A POSTROUTING -s <video source's ip> -j DSCP --set-dscp 40"

---

