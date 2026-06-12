---
title: "ipw2200 + wpa FINALLY WORKING"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by roots on 2006-06-01
hola.

just wanted to share some info on how i finally got my ipw2200 + wpa working on my acer 382tmi notebook running dapper 6.06 rc.

what i did:

-a fresh dapper rc install
-an install of network manager and wpa_supplicant via the VERY HELPFUL install script that can be found here: [HTML]http://www.ubuntuforums.org/showthread.php?t=144820[/HTML]

(i used version 0.5.3 but had NO new ipw/ieee drivers installed)

-a couple of little mods as follows: original post: [HTML]http://www.ubuntuforums.org/showthread.php?t=161585[/HTML]

1. ENABLE essid broadcast if you have it disabled, otherwise it won't work
2. do

```
sudo gedit /etc/modprobe.d/ipw2200
``` 

and disable hardware encryption by adding the line

```
options ipw2200 hwcrypto=0
```

then shutdown network manager, reload ipw2200 an restart network manager

```
sudo killall NetworkManager
sudo modprobe -r ipw2200
sudo modprobe ipw2200
sudo NetworkManager

```

with these few steps i finally got my wireless network with wpa working. only drawback is, that i have to activate it on every startup and enter the keyring password i was  asked when first activating the connection.

some more interesting notes:

1. the warning that occurs with ipw2200

```
roots@acid:~$ dmesg | grep ipw
[4294696.751000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294696.751000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294696.751000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4294696.752000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294696.984000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```

doesn't seem to be crucial for wlan & wpa functionality - at least it seems for me.

2. when using a hidden essid and enabled hardware encryption, syslog shows

```
Jun  1 10:04:22 acid NetworkManager: <information>^IActivation (eth1/wireless): access point 'blahblah' is unencrypted, no key
needed.

```

which is not correct because i have wpa enabled.


good luck & cheers,
roots

---

### Post by bradh on 2006-06-01
"only drawback is, that i have to activate it on every startup and enter the keyring password i was asked when first activating the connection."

Is there any way to do away with the keyring requirement?  I find this annoying - I would like the flexibility of choosing which wireless connection to use upon startup, especially if I'm away from home.

---

### Post by roots on 2006-06-01
good question, i found some hints in the forums but don't have the time to look into it any deeper atm... so - if you should find any valuable info, please let me/us know!

cheers,
roots

---

### Post by tone77 on 2006-06-04
I used the script to install nm & wpa_supplicant, but when I get to the 'sudo gedit /etc/modprobe.d/ipw2200' step, I don't have the ipw2200 driver file, which is strange, b/c I have an ipw2200 wifi card.

any thoughts?

---

### Post by roots on 2006-06-05
is the ipw2200 driver not installed?

check with

```
dmesg | grep ipw
```

and if it returns zero result, have a look if you got the driver files on your system at all

```
locate ipw2200
```

if this returns zero result too, you'll have to download & install the driver first, check the forums, there are some howtos for setting up the ipw2200.

good luck!


cheers,
roots

---

### Post by roots on 2006-06-05
ah sorry, i didn't read your post thoroughly... ;) 

the (config) file your'e supposed to edit in /etc/modprobe.d usually doesn't exist in first place (at least on my system), so you have to create it and add the line mentioned above.

however, if it still won't work out, refer to my last post.


cheers,
roots

---

### Post by tone77 on 2006-06-05
Roots, thanks for the replies.   

The ipw2200 driver is installed, but I am still having trouble.  I will dig deeper tonight, when I have time to play.

cheers,
tone77

---

### Post by roots on 2006-06-05
checking your syslog for output about the ipw2200 driver would be a reasonable step to start with...


cheers,
roots

---

### Post by tone77 on 2006-06-06
still can't get connected

the driver is present
 ```
dmesg | grep ipw
[4294686.672000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294686.672000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294686.672000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4294687.465000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294687.900000] ipw2200: Radio Frequency Kill Switch is On:
[4294687.900000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
```

I have added the file /etc/modprobe.d/ipw2200


I have tried all WPA Personal & WPA2 Personal with all combinations of the type, but no luck.  Maybe you can see something I'm not. The output of syslogs is as follows:


```

Jun  6 21:29:29 localhost NetworkManager: <information>^Imatch
Jun  6 21:29:29 localhost NetworkManager: <debug info>^I[1149647369.376669] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'Jacksonville'
Jun  6 21:29:29 localhost NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Jacksonville
Jun  6 21:29:29 localhost NetworkManager: <information>^IDeactivating device eth1.
Jun  6 21:29:31 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jun  6 21:29:31 localhost NetworkManager: <information>^IDevice eth1 activation scheduled...
Jun  6 21:29:31 localhost NetworkManager: <information>^IDeactivating device eth0.
Jun  6 21:29:31 localhost dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Jun  6 21:29:32 localhost NetworkManager: <information>^IActivation (eth1) started...
Jun  6 21:29:32 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  6 21:29:32 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  6 21:29:32 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  6 21:29:32 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  6 21:29:32 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  6 21:29:32 localhost NetworkManager: <information>^IActivation (eth1/wireless): access point 'Jacksonville' is encrypted, and a key exists.  No new key needed.
Jun  6 21:29:32 localhost NetworkManager: <information>^Imatch
Jun  6 21:29:32 localhost last message repeated 8 times
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'AP_SCAN 2'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was '0'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid '
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 scan_ssid 1'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 proto WPA2'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 psk <key>'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0'
Jun  6 21:29:33 localhost NetworkManager: <information>^ISUP: response was 'OK'
Jun  6 21:29:33 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Global control interface '/var/run/wpa_supplicant-global'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX global ctrl_iface - hexdump_ascii(len=49):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Initializing interface (2) 'eth1'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAPOL: SUPP_PAE entering state DISCONNECTED
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAPOL: KEY_RX entering state NO_KEY_RECEIVE
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAPOL: SUPP_BE entering state INITIALIZE
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAP: EAP entering state DISABLED
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAPOL: External notification - portEnabled=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAPOL: External notification - portValid=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):   capabilities: key_mgmt 0xf enc 0xf
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Own MAC address: 00:16:6f:6b:c2:07
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_set_wpa
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): =0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_set_countermeasures
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_set_drop_unencrypted
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Setting scan request: 0 sec 100000 usec
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Added interface eth1
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Wireless event: cmd=0x8b06 len=8
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=9):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):                  AP_SCAN 2
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=11):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):                    ADD_NETWORK
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE: ADD_NETWORK
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=43):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):        SET_NETWORK 0 ss
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):         id 4a61636b736f6
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):                    e76696c6c65
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='4a61636b736f6e76696c6c65'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): ssid - hexdump_ascii(len=12):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):      4a 61 63 6b 73 6f 6e 76 69 6c 6c 65              Jacksonville
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=25):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):         SET_NETWORK 0 sc
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):                    an_ssid 1
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE: SET_NETWORK id=0 name='scan_ssid' value='1'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): scan_ssid=1 (0x1)
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=24):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):         SET_NETWORK 0 pr
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):                    oto WPA2
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE: SET_NETWORK id=0 name='proto' value='WPA2'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): proto: 0x2
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=30):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):         SET_NETWORK 0 ke
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):               y_mgmt WPA-PSK
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='WPA-PSK'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): key_mgmt: 0x2
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=82): [REMOVED]
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE: SET_NETWORK id=0 name='psk' value='<removed for posting>'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EMOVED]
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): RX ctrl_iface - hexdump_ascii(len=16):
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581):         ENABLE_NETWORK 0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): CTRL_IFACE: ENABLE_NETWORK id=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Setting scan request: 0 sec 0 usec
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): State: DISCONNECTED -> SCANNING
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Trying to associate with SSID 'Jacksonville'
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Cancelling scan request
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: clearing own WPA/RSN IE
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Automatic auth_alg selection: 0x1
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: No WPA/RSN IE available from association info
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: Set cipher suites based on configuration
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: clearing AP WPA IE
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: clearing AP RSN IE
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: using GTK CCMP
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: using PTK CCMP
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: using KEY_MGMT WPA-PSK
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): WPA: Set own WPA IE default - hexdump(len=22): 
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): No keys have been configured - skip key clearing
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_set_drop_unencrypted
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): State: SCANNING -> ASSOCIATING
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): wpa_driver_wext_associate
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): Setting authentication timeout: 60 sec 0 usec
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAPOL: External notification - EAP success=0
Jun  6 21:29:33 localhost NetworkManager: <information>^Iwpa_supplicant(7581): EAPOL: External notification - EAP fail=0
Jun  6 21:30:33 localhost NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>60s), failing activation.
Jun  6 21:30:33 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jun  6 21:30:33 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (Jacksonville)
Jun  6 21:30:33 localhost NetworkManager: <information>^IActivation (eth1) failed.
Jun  6 21:30:33 localhost NetworkManager: <information>^IDeactivating device eth1.
Jun  6 21:30:33 localhost dhclient: receive_packet failed on eth1: Network is down
Jun  6 21:30:35 localhost NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.
Jun  6 21:30:35 localhost NetworkManager: <information>^IWill activate connection 'eth0'.

```

cheers,
tone

---

