---
title: "A new and exciting issue with the rt2860sta module on 10.10!"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by not_a_phd on 2010-11-01
I have been fighting this for about week now, but I am highly motivated to see this through. 

I have a 10.10 install on a eeePC901, with the rt2860 wireless chipset.

Following the instructions on this forum, I have blacklisted the rt2800 and rt2x00 modules  that came  with stock Ubuntu to keep them from interfering with the rt2860sta module. After following some directions for patching, compiling and installing RaLink's drivers (Thanks  Sven!), and installing the RaLink firmware, I am  able to connect to both a WEP and a WPA access point with a common  driver configuration. (Woo hooh!) 

The problem now is that my connection is still not close to being right. In the  background, it is disconnecting and reconnecting about once every  5-seconds. I can see the following messages repeat every 5-sec when tailing my  syslog:

```

Oct 31 14:39:39 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  associated -> completed
[COLOR=Red]Oct 31 14:39:44 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys[/COLOR]
[COLOR=Red]Oct 31 14:39:44 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys[/COLOR]
Oct 31 14:39:44 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  completed -> disconnected
Oct 31 14:39:44 jim-laptop-0 wpa_supplicant[807]: Trying to associate with SSID 'roxiedog'
Oct 31 14:39:44 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Oct 31 14:39:44 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 31 14:39:46 jim-laptop-0 kernel: [ 5126.839732] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 104
Oct 31 14:39:46 jim-laptop-0 wpa_supplicant[807]: Associated with 00:0f:66:0b:32:f7
[COLOR=Green]Oct 31 14:39:46 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-CONNECTED -  Connection to 00:0f:66:0b:32:f7 completed (reauth) [id=1 id_str=][/COLOR]
Oct 31 14:39:46 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  associating -> associated
Oct 31 14:39:46 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  associated -> completed
[COLOR=Red]Oct 31 14:39:53 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 31 14:39:53 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys[/COLOR]
Oct 31 14:39:53 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  completed -> disconnected
Oct 31 14:39:53 jim-laptop-0 wpa_supplicant[807]: Trying to associate with SSID 'roxiedog'
Oct 31 14:39:53 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Oct 31 14:39:53 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 31 14:39:55 jim-laptop-0 NetworkManager[768]: <info> (ra0):  roamed from BSSID 00:0F:66:0B:32:F7 (roxiedog) to (none) ((none))
Oct 31 14:39:55 jim-laptop-0 kernel: [ 5135.858012] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 104
Oct 31 14:39:55 jim-laptop-0 wpa_supplicant[807]: Associated with 00:0f:66:0b:32:f7
[COLOR=Green]Oct 31 14:39:55 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-CONNECTED -  Connection to 00:0f:66:0b:32:f7 completed (reauth) [id=1 id_str=][/COLOR]

```


When I ping my router, I drop packets during these  disconnect/reconnect events resulting in ~28% packet loss. The situation is far worse when running  wicd instead of NetworkManager. With wicd, it does not auto-reconnect. 

At home, I am using a Wireless-G router, so I dropped back to WirelessMode=4 in the RT2860STA.dat file with no success. 

My questions are as follows:
1. Has anyone else seen (and fixed) this behavior? I have not run across it in the forums yet.
2. Why is the wpa_supplicant running at all when I am in WEP mode?
3. Can I increase the debug level on the wpa_supplicant to see why it keeps disconnecting me? If so how? 
4. Better yet, can one of you tell me why it is disconnecting me based upon the cryptic "remove keys" debug output.

I have to wonder how many of those helped in this forum are suffering from this and do not realise it. The NetworkManager gives no real indication of a problem. The sufferer will have periodically slow internets, and the occasional page that doesn't load.

Thank you in advance for your help!!

---

### Post by not_a_phd on 2010-11-01
Stumped? I have more clues for you. 

I managed to find a tutorial on ConnMan debugging on the Kubuntu Wiki[https://wiki.kubuntu.org/ConnMan/Debugging](https://wiki.kubuntu.org/ConnMan/Debugging) . After installing the "indicator-network" package on my machine, and then running:

```
sudo indicator-network-debug start
```

I was able to see a world of new debug messages crop up in my syslog, of which I understand very little. But, for the good of the Ubuntu community, I am determined to understand what is happening!

Below is a snippet from my syslog that starts with a DISCONNECT, shows the reconnect, and ends with another DISCONNECT. The pattern of messages repeats approximately every 5-seconds. I apologize for the length.

The first think to note is that I am in ***way*** over my head. Is there anyone out there that has a clue what the messages around the disconnect events mean? I am thinking that these should give someone with savy an idea of why the wpa_supplicant keeps cutting me off.

As an aside, I would like to tag this message with eeePC901, ra2860sta, wpa_supplicant, and wireless. But, I have not yet figured out how to tag a message.

```
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_string() network 0x21dcdad8 key WiFi.Security value wep
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() element 0x21dcdad8 name 000f660b32f7
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() name WiFi.Security type 115 value 0xbfe5d418
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/element.c:unregister_property() property 0x21dcb428
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/profile.c:__connman_profile_update_network() network 0x21dcdad8
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/service.c:__connman_service_update_from_network() network 0x21dcdad8
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/service.c:__connman_service_lookup_from_network() network 0x21dcdad8
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/network.c:connman_network_get_string() network 0x21dcdad8 key Name
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/network.c:connman_network_get_uint8() network 0x21dcdad8 key Strength
Nov  1 19:54:45 jim-laptop-0 connmand[2569]: src/network.c:connman_network_get_bool() network 0x21dcdad8 key Roaming
[COLOR="Red"]Nov  1 19:54:47 jim-laptop-0 wpa_supplicant[2582]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  1 19:54:47 jim-laptop-0 wpa_supplicant[2582]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys[/COLOR]
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 64
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 64 type 16 flags 0x0000 seq 0
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69699 change 0
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 64
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 64 type 16 flags 0x0000 seq 0
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69699 change 0
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state COMPLETED ==> DISCONNECTED
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 DISCONNECTED
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 436
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 436 type 16 flags 0x0000 seq 0
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 {RX} 4820 packets 884323 bytes
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 {TX} 1977 packets 138710 bytes
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 {update} flags 69635 <UP,LOWER_UP>
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 {newlink} index 5 address 00:15:AF:CB:58:25 mtu 1500
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 {newlink} index 5 operstate 5 <DORMANT>
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:47 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  completed -> disconnected
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:47 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state DISCONNECTED ==> SCANNING
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 SCANNING
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member Scanning
Nov  1 19:54:47 jim-laptop-0 connmand[2569]: ra0 scanning started
Nov  1 19:54:49 jim-laptop-0 kernel: [ 1158.682127] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 104
Nov  1 19:54:49 jim-laptop-0 kernel: [ 1158.682957] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Nov  1 19:54:49 jim-laptop-0 wpa_supplicant[2582]: Trying to associate with 00:0f:66:0b:32:f7 (SSID='roxiedog' freq=2437 MHz)
Nov  1 19:54:49 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  scanning -> associating
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 52
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 52 type 16 flags 0x0000 seq 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 52
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 52 type 16 flags 0x0000 seq 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member Scanning
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 scanning finished
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member ScanResultsAvailable
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:scan_results_available() task 0x21dcb8c8
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state SCANNING ==> ASSOCIATING
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 ASSOCIATING
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 56
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 56 type 16 flags 0x0000 seq 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 60
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 60 type 16 flags 0x0000 seq 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:scan_results_reply() task 0x21dcb8c8
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:properties_reply() task 0x21dcb8c8
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:properties_reply() capabilties 17 frequency 2437 quality 86 noise 164 level 200 maxrate 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/device.c:connman_device_get_network() device 0x21dd6148 identifier 000f660b32f7
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_name() network 0x21dcdad8 name roxiedog
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() element 0x21dcdad8 name 000f660b32f7
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() name Name type 115 value 0xbfe5d428
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:unregister_property() property 0x21dce340
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_blob() network 0x21dcdad8 key WiFi.SSID size 8
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_array_property() element 0x21dcdad8 name 000f660b32f7
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_array_property() name WiFi.SSID type 121 value 0xbfe5d418
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:unregister_property() property 0x21dccd18
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_string() network 0x21dcdad8 key WiFi.Mode value managed
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() element 0x21dcdad8 name 000f660b32f7
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() name WiFi.Mode type 115 value 0xbfe5d418
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:unregister_property() property 0x21dc6e30
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:properties_reply() roxiedog (managed wep) strength 86 (no WPS)
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_available() network 0x21dcdad8 available 1
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_strength() network 0x21dcdad8 strengh 86
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() element 0x21dcdad8 name 000f660b32f7
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() name Strength type 121 value 0xbfe5d3fc
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:unregister_property() property 0x21dcb898
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_uint16() network 0x21dcdad8 key Frequency value 2437
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_uint16() network 0x21dcdad8 key WiFi.Channel value 6
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_set_string() network 0x21dcdad8 key WiFi.Security value wep
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() element 0x21dcdad8 name 000f660b32f7
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:set_static_property() name WiFi.Security type 115 value 0xbfe5d418
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/element.c:unregister_property() property 0x21dc6e48
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/profile.c:__connman_profile_update_network() network 0x21dcdad8
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/service.c:__connman_service_update_from_network() network 0x21dcdad8
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/service.c:__connman_service_lookup_from_network() network 0x21dcdad8
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_get_string() network 0x21dcdad8 key Name
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_get_uint8() network 0x21dcdad8 key Strength
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/network.c:connman_network_get_bool() network 0x21dcdad8 key Roaming
Nov  1 19:54:49 jim-laptop-0 wpa_supplicant[2582]: Associated with 00:0f:66:0b:32:f7
Nov  1 19:54:49 jim-laptop-0 wpa_supplicant[2582]: CTRL-EVENT-CONNECTED - Connection to 00:0f:66:0b:32:f7 completed (reauth) [id=0 id_str=]
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 52
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 52 type 16 flags 0x0000 seq 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:49 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  associating -> associated
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 64
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 64 type 16 flags 0x0000 seq 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 436
Nov  1 19:54:49 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  associated -> completed
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 436 type 16 flags 0x0000 seq 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 {RX} 4829 packets 884943 bytes
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 {TX} 1991 packets 138710 bytes
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 {update} flags 69699 <UP,RUNNING,LOWER_UP>
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_lower_up() ipconfig (nil)
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 {newlink} index 5 address 00:15:AF:CB:58:25 mtu 1500
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 {newlink} index 5 operstate 6 <UP>
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69699 change 0
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state ASSOCIATING ==> ASSOCIATED
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 ASSOCIATED
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state ASSOCIATED ==> COMPLETED
Nov  1 19:54:49 jim-laptop-0 connmand[2569]: ra0 COMPLETED
[COLOR="red"]Nov  1 19:54:54 jim-laptop-0 wpa_supplicant[2582]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  1 19:54:54 jim-laptop-0 wpa_supplicant[2582]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys[/COLOR]
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 64
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 64 type 16 flags 0x0000 seq 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69699 change 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 64
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 64 type 16 flags 0x0000 seq 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69699 change 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state COMPLETED ==> DISCONNECTED
Nov  1 19:54:54 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  completed -> disconnected
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 DISCONNECTED
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 64
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 64 type 16 flags 0x0000 seq 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69699 change 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 64
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 64 type 16 flags 0x0000 seq 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69699 change 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state COMPLETED ==> DISCONNECTED
Nov  1 19:54:54 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  completed -> disconnected
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 DISCONNECTED
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() buf 0xbfe5c72c len 436
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/rtnl.c:rtnl_message() NEWLINK len 436 type 16 flags 0x0000 seq 0
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: src/ipconfig.c:__connman_ipconfig_newlink() index 5
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 {RX} 4880 packets 889341 bytes
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 {TX} 1994 packets 138710 bytes
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 {update} flags 69635 <UP,LOWER_UP>
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 {newlink} index 5 address 00:15:AF:CB:58:25 mtu 1500
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 {newlink} index 5 operstate 5 <DORMANT>
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/wifi.c:wifi_newlink() index 5 flags 69635 change 0
Nov  1 19:54:54 jim-laptop-0 NetworkManager[782]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member StateChange
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/supplicant.c:state_change() state DISCONNECTED ==> SCANNING
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 SCANNING
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: plugins/supplicant.c:supplicant_filter() task 0x21dcb8c8 member Scanning
Nov  1 19:54:54 jim-laptop-0 connmand[2569]: ra0 scanning started 
```

---

### Post by not_a_phd on 2010-11-02
OK. That last one **totally** did not work. While I got increased output, it was actually from a second network connection manager (ConnMan). If I had taken the time to read the surrounding wiki pages, I would have understood that before installing ConnMan on my machine *next to* NetworkManager!

Long story short, I completely hosed my install, and will have to start from square one. In anticipation of running into the same problems, it would be nice to know how to set the debug options for wpa_supplicant. All of the info that I find on this refer to boot config files that DO NOT exist on the Ubuntu distribution. I have grepped the /etc directory and find mention of wpa_supplicant in the dbus configuration area, indicating to me that I could send the "Level 0" debug command to wpa_supplicant through dbus. But, I can find no documentation on how to do this anywhere.

---

### Post by lunatico on 2010-11-04
:confused:

---

### Post by not_a_phd on 2010-11-04
Thank you lunatico! You have succinctly summarized my situation, and you have given me evidence that I am not a community of one! :)  

I am still plodding along on this. I believe the problem is an adverse interaction between the NetworkManager controlled wpa_supplicant and my vendor-supplied self-compiled drivers. However, with the wpa_cli/wpa_gui interface broken in all distributions, I am unable to jump in and see exactly why the wpa_supplicant is disconnecting me every 5-seconds on a WEP network. 

I have resorted to grepping my way through source-code to search for all possible origins of the syslog messages that I have seen. 

I feel like I am just one compiler/config-file/makefile setting away from solving this! I just don't presently have enough insight into the problem to figure out which one it is... But, I will press on. I will fight the fight. I will win the race. If not for me, for all of the children of the world!!! :rolleyes:

---

### Post by lunatico on 2010-11-04
> **not_a_phd said:**
> But, I will press on. I will fight the fight. I will win the race. If not for me, for all of the children of the world!!! :rolleyes:

Hahaha that's very inspiring man! You should run for president of the world. I'll vote for you.

As I said on my other thread your problem looks different to mine, it's worst. I don't get the reconnections that often, mine are more like every 20 mins or so, and some times it's one, and some times its two or three or even four in a row.

It's driving me crazy!!! And this wasn't happening a month ago.

---

### Post by not_a_phd on 2010-11-04
> **lunatico said:**
> Hahaha that's very inspiring man! You should run for president of the world. I'll vote for you.

As I said on my other thread your problem looks different to mine, it's worst. I don't get the reconnections that often, mine are more like every 20 mins or so, and some times it's one, and some times its two or three or even four in a row.

It's driving me crazy!!! And this wasn't happening a month ago.


I have found that mine are like every 5-10min or so on a WPA network, but every 5-s on a WEP...

---

### Post by lunatico on 2010-11-04
> **not_a_phd said:**
> I have found that mine are like every 5-10min or so on a WPA network, but every 5-s on a WEP...

uhm maybe it is similar.... I just skimmed through the logs and I get in average ~12 reconnections per hour.

---

### Post by not_a_phd on 2010-11-04
Have you tried looking at the behavior of yours with a WEP network to see if it is any different?

---

### Post by not_a_phd on 2010-11-04
Solution for me:

1. I reverted to the ubuntu supplied rt2860sta.ko module. No more messing with compiled drivers for me.

2. Blacklisted rt2800pci and rt2x00pci module in /etc/modprobe.d/blacklist.conf file.

3. In a fresh boot at home (in range of my WEP router), I manually set the essid and key using iwconfig in the command line:
```

sudo iwconfig wlan0 essid "my_ssid_name"
sudo iwconfig wlan0 key mywepkey

```

4. I then used the network-manager icon to connect to my network.

Worked like a charm! This was the first time I was able to connect to a WEP enabled network with the rt2860sta driver.

I haven't yet tested to see if it will come back after a reboot, but the good folks that first posted this workaround in the "closed" bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432211) assure me that it should continue to work.

I would like to know why my compiled driver clashed with network manager so badly, but I don't think I will ever find out.

---

