---
title: "Network manager Vs command line"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by rodhash on 2011-01-02
Hello guys,

The network-manager connects really easy to LEAP and WPA2 networks, however how can I do that through command line for both networks?


Thanks,

---

### Post by mikewhatever on 2011-01-02
Here is a good guide.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by rodhash on 2011-01-06
Hello,

I followed all of the procedures but I still not able to connect through wpa_supplicant.

This is a quick view of the error:
```

root@rod-homecomputer:~# wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:25:9c:d8:ec:8b (SSID='hashnet' freq=2412 MHz)
Associated with 00:00:00:00:00:00
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

And this is my current wpa_supplicant.conf file:
```

root@rod-homecomputer:~# cat /etc/wpa_supplicant.conf 
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="hashnet"
        #psk="mykey"
        psk=mykeyinhex
        proto=RSN WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
}
root@rod-homecomputer:~# 

```

Also this is my iwlist scan:
```

root@rod-homecomputer:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:D8:EC:8B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"hashnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000001cb557f
                    Extra: Last beacon: 140ms ago
                    IE: Unknown: 0007686173686E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD770050F204104A0001101044000102103B000103104700100656C686C6960656C686C69626A61676102100104C696E6B73797320627920436973636F102300085752543136304E4C1024000876312E30302E30311042000231371054000800060050F2040001101100085752543136304E4C100800020084
                    IE: Unknown: DD0A00037F04010000000000

root@rod-homecomputer:~# 

```


Has someone any idea why I can't connect?

Thanks.

---

### Post by rodhash on 2011-01-06
Is the wext driver able to connect on WPA2 networks?

---

### Post by kevdog on 2011-01-07
It depends on your network card and the driver you are using for your network card.

---

### Post by rodhash on 2011-01-07
At first the adapter didn't work. I had to update the firmware, the ar9271.fw. Then I was able to see the wlan0 adapter.

The driver is the native one, the ath9k_htc, but with the firmware upgraded.

It looks working, I can scan the network, I just can't connect on it.

It's an USB TL-WN422G.


If anyone has any idea please let me know. Thanks.

---

### Post by rodhash on 2011-01-07
Guys,

How do I check if my current driver / adapter is able to connect on WPA2 network??

I have a TP LINK - TL WN422G V2.

I've upgraded the firmware (ar9271) and the current driver in use is ath9k_htc.

I've tried the windows driver, but the ndiswrapper didn't recognize the driver on CD or the downloaded driver at the atheros site.


Thanks.

---

### Post by PatchesTheCaveman on 2011-01-07
Atheros 9000 series chipsets should definitely support WPA.

Since you needed a firmware upgrade to get it working, perhaps you need a driver update too.  On a terminal, run:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-$(lsb_release -cs)-generic
```

If that doesn't work you could also try the Madwifi driver.

---

### Post by kevdog on 2011-01-07
I'm no expert on Atheros 9000 chipsets, however you need to find a compatible driver and not use ndiswrapper.  This may take you awhile and a lot or reading to find.  Once you have found the driver, we can help install, troubleshoot it.  Someone reported madwifi as a possible option.  If this indeed is an option, let me know and we can either install or compile the driver from source.  If you can, I would suggest testing WPA2 capabilities last once troubleshooting if the driver will work at all to connect to an open network and work reliably.

---

