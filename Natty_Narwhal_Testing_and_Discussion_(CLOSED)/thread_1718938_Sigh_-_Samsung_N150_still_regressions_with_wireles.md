---
title: "Sigh - Samsung N150 still regressions with wireless driver"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2011-04-01
Since Lucid I have been getting problems with wireless connectivity on Ubuntu, Lucid was OK, but maverick was impossible to connect to. I migrated early to Natty in the hopes of getting through the problems. Unfortunately no .... natty connects about 80 % of the time, although when coming back from suspend the device is seen as disabled and will not come up - requires a reboot. 

Failures to connect consist of either continuous asking for the password or a device disabled state. Both require a reboot. 

Still that was an improvement, until the latest beta (or kernel) who knows. Now the driver just remains active and connected, it just boes not seem to talk to any programs on the computer.

Heres a syslog section of the incident.

> Apr  1 07:47:14 sammy 40grub2: debug: parsing: ### BEGIN /etc/grub.d/41_custom ###
Apr  1 07:47:14 sammy 40grub2: debug: parsing: if [ -f  $prefix/custom.cfg ]; then
Apr  1 07:47:14 sammy 40grub2: debug: parsing: source $prefix/custom.cfg;
Apr  1 07:47:14 sammy 40grub2: debug: parsing: fi
Apr  1 07:47:14 sammy 40grub2: debug: parsing: ### END /etc/grub.d/41_custom ###
Apr  1 07:47:14 sammy 50mounted-tests: debug: /usr/lib/linux-boot-probes/mounted/40grub2 succeeded
Apr  1 07:47:14 sammy linux-boot-prober: debug: linux detected by /usr/lib/linux-boot-probes/50mounted-tests
Apr  1 07:48:48 sammy kernel: [  835.005505] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr  1 07:50:32 sammy wpa_supplicant[536]: CTRL-EVENT-DISCONNECTED bssid=74:ea:3a:da:ff:1e reason=0
Apr  1 07:50:32 sammy kernel: [  938.604069] ===========>RemovePeerTS,74:ea:3a:da:ff:1e
Apr  1 07:50:32 sammy kernel: [  938.604081] ====>remove Tx_TS_admin_list
Apr  1 07:50:32 sammy kernel: [  938.604480] ===>ieee80211_associate_procedure_wq(), chan:1
Apr  1 07:50:32 sammy kernel: [  938.620816] =================>ieee80211_authentication_req():auth->algorithm is 0
Apr  1 07:50:32 sammy kernel: [  938.625824] Associated successfully
Apr  1 07:50:32 sammy kernel: [  938.625831] Using G rates:108
Apr  1 07:50:32 sammy kernel: [  938.625835] Successfully associated, ht enabled
Apr  1 07:50:32 sammy NetworkManager[489]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  1 07:50:32 sammy kernel: [  938.635470] ====================>rx ADDBAREQ from :74:ea:3a:da:ff:1e
Apr  1 07:50:32 sammy kernel: [  938.635490] =====>to send ADDBARSP
Apr  1 07:50:32 sammy wpa_supplicant[536]: Associated with 74:ea:3a:da:ff:1e
Apr  1 07:50:32 sammy NetworkManager[489]: <info> (wlan0): supplicant connection state:  disconnected -> associated
Apr  1 07:50:32 sammy NetworkManager[489]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr  1 07:50:32 sammy kernel: [  938.641058] ============>normal associate
Apr  1 07:50:32 sammy wpa_supplicant[536]: WPA: Key negotiation completed with 74:ea:3a:da:ff:1e [PTK=CCMP GTK=TKIP]
Apr  1 07:50:32 sammy wpa_supplicant[536]: CTRL-EVENT-CONNECTED - Connection to 74:ea:3a:da:ff:1e completed (reauth) [id=0 id_str=]
Apr  1 07:50:32 sammy NetworkManager[489]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr  1 07:50:32 sammy kernel: [  938.663081] alg name:CCMP
Apr  1 07:50:32 sammy kernel: [  938.663616] alg name:TKIP
Apr  1 07:50:32 sammy NetworkManager[489]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr  1 07:50:48 sammy kernel: [  955.006792] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr  1 07:52:48 sammy kernel: [ 1075.007988] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr  1 07:54:48 sammy kernel: [ 1195.007625] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr  1 07:56:48 sammy kernel: [ 1315.005711] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr  1 07:58:48 sammy kernel: [ 1435.006247] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr  1 08:00:48 sammy kernel: [ 1555.008197] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr  1 08:02:48 sammy kernel: [ 1675.006356] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData


---

### Post by beew on 2011-04-01
Have you checked out this ppa and its support forum?
[https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/%7Evoria/+archive/ppa")

Link to support forum is on the LP page linked to above.

---

