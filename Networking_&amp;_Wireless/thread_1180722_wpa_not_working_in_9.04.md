---
title: "wpa not working in 9.04"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by whitebox on 2009-06-07
hi

i have just installed ubuntu 9.04 on my samsung q35 laptop, and i used the netowkr manager to connect to my ap using wpa personal.

it does connect, but the ip issued is not correct. my ap is configured to issue ip from 192.168.x.x but i got ip of 10.x.x.x




what's wrong here?



fs@ydag:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg

 9.976228] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    9.976232] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    9.976357] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.976372] iwl3945 0000:02:00.0: setting latency timer to 64
[    9.976415] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    9.976721] iwl3945 0000:02:00.0: irq 2301 for MSI/MSI-X


another funny thing is wpa_supplicant does not read my /etc/wpa_supplicant.conf  

fs@ydag:~$ ps aux | grep wpa
root      2768  0.0  0.1   4276  1868 ?        S    17:56   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log



fs

---

