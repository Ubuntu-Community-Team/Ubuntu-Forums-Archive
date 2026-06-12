---
title: "ndiswrapper networkmanager trouble"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by jemdos on 2010-08-10
Greetings from Sunny Spain

I've been wasting several hours trying to get wireless working on my desktop pc, using and old DLW-G132 D-Link USB stick.

I've been forced to use ndiswrapper and some old windows drivers. Got lights blinking on the stick, and looks like it could work (it works under windows). But it does not connect, and asks again and again and again for the WPA password.

Toying with syslog viewer and comparing logs with my inspiron 1525 that works flawlessly, I've detected that, when the laptop tryes to connect, at "activation stage 2 of 5", passes data about ssid, scan_ssid, key_mngt and psk values. No such thing happens with the desktop pc.

jemdos@Nazgul:~$ dmesg | grep -e ndis -e wlan
[  219.719176] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  220.013456] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[  220.118301] usbcore: registered new interface driver ndiswrapper
[  221.051207] ndiswrapper: driver neta5agu (D-Link,10/06/2004,1.0.1.41) loaded
[  221.417501] wlan0: ethernet device 00:15:e9:a2:9d:52 using NDIS driver: neta5agu, version: 0x10000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 2001:3A02.F.conf
[  221.417527] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[  221.453842] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  421.032851] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[B][  421.032858] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  421.032862] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  426.038558] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  426.038572] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  426.038581] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)[/B]
[  431.043953] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  431.043967] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  431.043976] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  436.049372] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  436.049386] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  436.049395] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  441.055029] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  441.055043] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  441.055052] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  446.060564] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  446.060578] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  446.060587] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  451.066222] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  451.066236] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  451.066244] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  456.071885] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  456.071899] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  456.071908] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  461.076578] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  461.076592] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  461.076601] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  466.082307] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  466.082322] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  466.082330] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  471.087979] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  471.087993] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  471.088001] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  476.093673] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  476.093686] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  476.093695] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  481.099318] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  481.099332] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  481.099341] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  519.566062] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  519.566076] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  519.566085] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  524.572028] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  524.572043] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  524.572051] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  529.577691] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  529.577705] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  529.577714] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  534.580564] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  534.580578] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  534.580587] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  539.586215] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  539.586229] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  539.586237] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  544.591882] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  544.591896] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  544.591904] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  549.596579] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  549.596593] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  549.596602] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  554.602237] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  554.602251] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  554.602259] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  559.608864] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  559.608878] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  559.608886] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  564.614547] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  564.614562] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  564.614570] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  569.618548] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  569.618562] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  569.618571] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[  574.622530] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  574.622545] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[  574.622553] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C0010015)
[ 1052.023864] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1062.035772] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1072.045674] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1082.056497] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1092.067980] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1102.075560] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1115.372392] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1125.385648] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1135.396690] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1145.407777] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1155.416375] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1165.427515] ndiswrapper (iw_set_auth:1602): invalid cmd 12

---

