---
title: "Netgear WG111v3 connect at boot"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by dinkoarun on 2009-09-30
I have an external USB wifi device (Netgear WG111v3) which I configured based on this guide, **[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=732827]("http://ubuntuforums.org/showthread.php?t=732827")[/COLOR]** It works perfectly on Network Manager. However, it connects only after I login with my username and password.

I want the wireless network connection to connect at the time of boot itself. I know I need to configure the ***/etc/network/interfaces*** file. But I don't know the exact configuration to use to setup wireless. As the connection is a WPA2-PSK, do I need to use wpa_supplicant?? If so, what is the configuration I need to use for the wpa_supplicant.conf file??

I am using Ubuntu 9.04 desktop.

Regards,

Arun

---

### Post by chili555 on 2009-09-30
Does it ask for your details every time if you right-click the Network Manager icon, edit connections and check the "Connect automatically" box?

---

### Post by dinkoarun on 2009-10-01
> **chili555 said:**
> Does it ask for your details every time if you right-click the Network Manager icon, edit connections and check the "Connect automatically" box?

Yes, the connect automatically box in checked. I am pretty sure it is the /etc/network/interfaces files that needs to be configured. So when the system boots up, the interface will be activated using the ifup command.

I am using rtl8187 driver for my Netgear WG111v3 USB device. I just need the configuration that needs to be put in the /etc/network/interfaces file and the wpa_supplicant.conf file.

Please help..

---

### Post by dinkoarun on 2009-10-01
Can someone offer a solution, please??

---

### Post by chili555 on 2009-10-01
This thread will show you how to set up /etc/wpa_supplicant.conf. [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

This thread shows a sample *interfaces* file. Of course, customize the file using your details. [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

By the way, the stanza in *interfaces, auto eth0*, tells the system to connect automatically on boot, without the need for 'ifup.'

I don't use WPA myself, so I am fresh out of talent.

---

### Post by dinkoarun on 2009-10-03
Thanks guys, I got my wlan0 to work on bootup. Here are my settings:

/etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf
```

/etc/wpa_supplicant.conf

  GNU nano 2.0.9                      File: /etc/wpa_supplicant.conf                                                    

```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="xx"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=30235b7035esd242d4296d113df12350a461cf66678b121e18168a03d17f08b3a
}
```

---

