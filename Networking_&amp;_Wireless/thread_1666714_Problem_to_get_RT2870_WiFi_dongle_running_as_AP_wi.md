---
title: "Problem to get RT2870 WiFi dongle running as AP with rt2800usb driver"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by Walmit on 2011-01-14
Dear all,
 
 I am trying to use a WiFi USB dongle as software access point and I have some problems to set the dongle in master mode.
 
 The USB dongle is based on the RaLink RT2870 chip and it is used with the rt2800usb driver from the compat-wireless package. I have read on some forums that this driver should support the &#8216;master&#8217; mode for this chip.
 
 The driver has successfully been compiled (from the compat-wireless-2.6.36-5-spn version) on Ubuntu 10.10 and is correctly loaded on the dongle.

    ```

Output from nm-tool:

Device: wlan0  [Auto xxxx_demo] ---------------------------------------------- 
   Type:              802.11 WiFi 
   Driver:            rt2800usb 
   State:             connected 
   Default:           no 
   HW Address:        00:0E:8E:28:05:2B
 
```I am able to connect as client to neighboring WiFi access points without any problem. However, I get an error message when trying to set the dongle in &#8216;master&#8217; mode. It seems that this mode is not supported by the driver.

    ```

$ sudo iwconfig wlan0 mode master 
 Error for wireless request "Set Mode" (8B06) : 
     SET failed on device wlan0 ; Invalid argument. 

```So, here are my questions:

[LIST=1]
[*]Has anyone succeeded in using a RT2870 chip with the rt2800usb driver in &#8216;master&#8217; mode (or with another driver)?
[*]Does the rt2800usb driver require some &#8216;customization&#8217; in order to be used in master mode?
[*]Does the rt2800usb driver support the &#8216;master&#8217; mode?
[*]Is it possible to use the RT2870 chip with Hostapd in AP/master mode?
[/LIST]
 
 Thanks in advance for any help.
 
Walmit

---

### Post by Walmit on 2011-01-14
I finally succeed in putting the rt2870 in master by using hostapd. 

 I had to use the following configuration file for hostapd:
```

interface=wlan0
 driver=nl80211
 ssid=test
 hw_mode=a
 channel=60
 ieee80211n=1
 beacon_int=100
 macaddr_acl=0
 auth_algs=3

```Starting hostapd put the WiFi dongle in master mode:
> 
*wlan0     IEEE 802.11abgn  Mode:Master  Frequency:5.3 GHz  Tx-Power=3 dBm    *
           *Retry  long limit:7   RTS thr=2347 B   Fragment thr=2346 B    *
           *Power Management:on *
I am now able to associate to this 'AP' with another WiFi client. Well, I still don't have connection between the client and the AP due to IP address assignment problems. Probably something wrong with hostapd configuration (maybe I should use DHCP).

---

### Post by Walmit on 2011-01-14
Well, I still can't get 40MHz channel working (probably wrong configuration of hostapd)

---

### Post by nemo136 on 2011-02-18
Any news on this problem? I have got a similar usb key and would like to set up an access point using hostapd, if you finally succeeded to set your AP, could you post your working configuration file for hostapd ?

---

### Post by nemo136 on 2011-02-19
I  tried to set up the access point without success. Operations I did:
- blacklisted rt2870sta
- copy rt2870.bin from the 2870sta package driver to /lib/firmware
- configure hostap with a working configuration from another card (wpa/psk)

Hostapd launches without problem, but I cannot connect and I have this error message when a client tries to connect : 
```
 
unknown vendor specific information element ignored (vendor OUI 00:10:18 len=9)
STA 90:21:00:00:00:00 sent probe request for our SSID
MGMT (TX callback) ACK
mgmt::proberesp cb
MGMT
mgmt::auth
authentication: STA=90:21:00:00:00:00 auth_alg=0 auth_transaction=1 status_code=0 wep=0
wlan0: STA 90:21:00:00:00:00 IEEE 802.11: authentication OK (open system)
wlan0: STA 90:21:00:00:00:00 MLME: MLME-AUTHENTICATE.indication(90:21:00:00:00:00, OPEN_SYSTEM)
wlan0: STA 90:21:00:00:00:00 MLME: MLME-DELETEKEYS.request(90:21:00:00:00:00)
authentication reply: STA=90:21:00:00:00:00 auth_alg=0 auth_transaction=2 resp=0 (IE len=0)
MGMT (TX callback) ACK
mgmt::auth cb
handle_auth_cb - too short payload (len=26)

```

My kernel is 2.6.32-5 (the server is debian, but it should be the same behavior as ubuntu)
So, if anyone managed to configure an access point ...

EDIT : [link]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5756") to similar thread

---

### Post by Walmit on 2011-02-20
Hello Nemo,

Yes, I finally succeed in getting hostapd working with wpa but I have never encountered the problem of "too short payload". 

I did the same as you: blacklisting rt2870sta and copying the last version of the firmware to /lib/firmware.
Below, the part of the configuration file related to wpa settings (I use an adapted version of the configuration file available at /etc/hostapd/hostapd.conf):
```

wpa=1
wpa_passphrase=0123456789

wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP

wpa_ptk_rekey=600

```I work with hostapd version 0.6.9 and wpa_supplicant version 0.6.9. Which version of hostapd are you using?
Did you check if you can connect to your AP without wpa encryption?

Best regards

---

### Post by PaulReaver on 2011-02-20
> **Walmit said:**
> maybe I should use DHCP

Bingo

hostapd dhcp and firewall rules should do it :)

what type off internet connection does the host machine have?  
wired, dialup, mobilebroadband?

---

