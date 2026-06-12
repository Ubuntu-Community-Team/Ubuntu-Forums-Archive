---
title: "Wireless - manual configuration"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by Athunye on 2010-03-05
I created my wpa_supplicant.conf this way:
```

# wpa_passphrase Dlink_Router my_passwd > /etc/wpa_supplicant.conf

```But when I run
```

wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D wext

```it returns:
```

Trying to associate with 00:21:91:6e:07:56 (SSID='Dlink_Router' freq=2452 MHz)
Associated with 00:21:91:6e:07:56
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
CTRL-EVENT-SCAN-RESULTS

```Actually, this runs like a loop. It never stops returning the same message again and again.
I'm lost.

Just to give some more information:
```

fernando@athunye, Fri Mar 05 10:12:18 
~ $  
bash >>> sudo iwlist wlan0 scan
[sudo] password for athunye: 
wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:6E:07:56
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Dlink_Router"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014447c1972
                    Extra: Last beacon: 576ms ago
                    IE: Unknown: 000C446C696E6B5F526F75746572
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 32080C1218602430486C
                    IE: Unknown: CC0700CC020000018A
                    IE: Unknown: CC0700CC0300000100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

fernando@athunye, Fri Mar 05 10:12:37 
~ $  
bash >>> 

```Any help would be appreciated.

---

### Post by Kostas2010 on 2010-03-19
Same problem here. 

Perhaps there is another application that is blocking the device. 

I would appreciate some help.

---

