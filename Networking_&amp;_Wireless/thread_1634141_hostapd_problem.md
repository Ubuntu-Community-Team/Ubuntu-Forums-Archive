---
title: "hostapd problem"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by gab.00.00 on 2010-11-30
hello

I have a problem with my DWA-556 when using it as an access point with madwifi and hostapd.

The access point appears normally to users when starting hostapd, but when more than one user connects to it, it disappears.

Another problem is that when i stop hostapd to change the channel, the network doesn't appear to users after restarting hostapd.

This is my hostapd.conf file:
interface=ath0
driver=madwifi
logger_syslog=0
logger_syslog_level=0
logger_stdout=0
logger_stdout_level=0
dump_file=/tmp/hostapd.dump.0.0
ctrl_interface=/var/run/hostapd1
ssid="Atheros Wireless Network"
hw_mode=g
beacon_int=100
max_num_sta=255
rts_threshold=2347
fragm_threshold=2346
supported_rates=10 20 55 110 60 90 120 180 240 360 480 540
preamble=1
auth_algs=1
ignore_broadcast_ssid=0
wep_default_key=0




And these are the steps to start hostapd:
 ifconfig eth0 down 
 wlanconfig ath0 destroy 
 wlanconfig ath create wlandev wifi0 wlanmode ap
iwconfig ath0 essid "Atheros Wireless Network" channel 11
iwpriv ath0 mode 11g 
ifconfig ath0 192.168.1.11 netmask 255.255.255.0 up 
 ifconfig eth0 10.0.0.1 netmask 255.255.255.0 up
service network-manager stop
hostapd -dd /home/thaer/hostapd-0.7.3/hostapd/hostapd.conf

---

