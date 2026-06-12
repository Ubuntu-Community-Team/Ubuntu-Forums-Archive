---
title: "Belkin F5D7050, Ubuntu 11.04, CLI"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by aristidesfl on 2011-06-24
I'm trying to configure my belkin dongle, but I get some errors when restarting networking :(
Do you know what it might be?

Thanks

[SIZE="3"]info[/SIZE]
```
ubuntu: 11.04 
wireless adapter: belkin F5D7050 
chipset:RT73 (RT2500 eventually) 
wlan encryption: WPA2 AES PSK
```

[SIZE="2"]/etc/network/interfaces
[/SIZE]```
auto lo 
iface lo inet loopback

auto wlan0 
iface wlan0 inet dhcp 
wpa-ssid (use my ssid here) 
wpa-ap-scan 1 
wpa-proto RSN 
wpa-pairwise CCMP 
wpa-group CCMP 
wpa-key-mgmt WPA-PSK 
wpa-psk (use my hex key her)

```

[SIZE="2"]sudo /etc/init.d/networking restart[/SIZE]
```
Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
Reconfiguring network interfaces&#8230;
cat: /var/run/wpa_supplicant.wlan0.pid: No such file or directory 
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1 
ssh stop/waiting 
ssh start/running, process 17152

```

[SIZE="2"]iwconfig[/SIZE]
```
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off Power Management:on
```

---

### Post by aristidesfl on 2011-06-28
bump

---

