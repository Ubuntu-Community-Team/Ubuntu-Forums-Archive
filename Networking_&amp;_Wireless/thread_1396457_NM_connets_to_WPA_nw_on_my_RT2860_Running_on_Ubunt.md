---
title: "NM connets to WPA n/w on my RT2860 Running on Ubuntu 9.10, but not commandline"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by sweekar on 2010-02-02
I've been trying unsuccessfully to connect to wireless network using commandline.

Here's a list of the things I tried.

Network that I'm trying to connect to:

```

--snip--


Cell 03 - Address: XX:22:XX:46:XX:B3
                    ESSID:"dlink-vikram"
                    Mode:Managed
                    Channel:6
                    Quality:86/100  Signal level:-56 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
--snip--

```


wp_supplicant with the foll. config file:
```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=0

network={
ssid="myssid"
scan_ssid=1
proto=RSN WPA
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP WEP104 WEP40
psk="password in quotes"
}
```


Next, I tried this:
```

sudo ifconfig ra0 up
sudo iwconfig ra0 essid <YOUR WIRELESS ROUTER's ESSID>
sudo iwconfig ra0 key <YOUR KEY>
sudo dhclient ra0 
```

....nada


Then this:

i```
face ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "myssid"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="A shared key"
        pre-up ifconfig ra0 up

sudo ifup ra0
```

still no luck.... :(

Any pointers?

---

### Post by chili555 on 2010-02-02
I have never had any luck trying to get a system with Network Manager installed to connect by command line. Does NM allow you to connect at all? If you are a command line junkie, like me, you might be happier simply removing NM altogether. If you still might take the computer down to the cyber cafe for coffee, then NM is a lot easier, but the command line is certainly do-able.

I think the system wants but one set of hands on the steering wheel.

---

### Post by sweekar on 2010-02-08
Hey... thanks. Uninstalling NM got it working! :)

---

### Post by steliyan on 2010-02-09
Please, delete this.

---

