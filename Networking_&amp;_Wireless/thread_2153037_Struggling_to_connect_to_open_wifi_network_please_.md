---
title: "Struggling to connect to open wifi network please help urgent!"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by TiffanyRobin on 2013-06-09
I've been trying to connect to an open wifi network in America where I'm working over summer. It's only connected once since I got here on the 8th. I'm a novice to Ubuntu and I have 12.04. I don't know if it's just a really bad network or if there is an issue with my netbook. Please help me fix this as I want to skype home!

---

### Post by ohnonot on 2013-06-10
hello!
there's not enough info in your post.

what kind of open wifi? where? does it work with other computers? did you connect succesfully to other networks? in what way is it "open"? you have to go through some commercial website?
how exactly does the network manager react? how did you set up the connection?

all this preferably with relevant info copy-pasted into code tags (the # sign when you 'Go Advanced')

---

### Post by TiffanyRobin on 2013-06-10
Hi.

I'm sorry, I'm just totally new to linux and I don't really know what I'm doing! By open I mean there's no password needed to connect. You just connect to the wifi, and browse, there's no browser log in or anything. It does work with other computers but it does drop out a lot, it seems to be worse on my netbook though and there's no network diagnostics like there is on windows (as far as I know).

---

### Post by steeldriver on 2013-06-10
There's quite a lot of network diagnostics in the standard Ubuntu 12.04 - although you may need to open up a terminal window and type some commands

If you want to see general info about your devices and connections (including the visible wireless access points), you can use

```
nm-tool
```

(it will also tell us a little about your wireless hardware / driver). To see information about just the wifi access points, you can try

```
nmcli dev wifi list
```

Is this a 'campus' type open network? sometimes the Linux wireless drivers have problems when there are multiple access points sharing the same SSID (as used on large campuses / hospitals / workplaces to provide access across a wide area), the driver can get confused about which is the closest/strongest one that it should try to associate to - iirc it sometimes helps to fix to a single access point by putting its MAC in the BSSID field

---

### Post by TiffanyRobin on 2013-06-10
I don't really know if it's a campus type network - how would I find out? It's actually connected at the minute but it keeps dropping out and obviously not good to skype with! When I type in nm-tool it shows:

```
State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        E8:03:9A:1C:48:21


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [TRENDnet] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        78:92:9C:75:12:2E


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TRENDnet:        Infra, C8:D7:19:D7:30:37, Freq 2442 MHz, Rate 54 Mb/s, Strength 35
    West Chop Wifi:  Infra, 00:02:6F:F9:14:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    *TRENDnet:       Infra, 00:14:D1:C1:C9:23, Freq 2442 MHz, Rate 54 Mb/s, Strength 45
    belkin.ae2:      Infra, EC:1A:59:31:5A:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2


  IPv4 Settings:
    Address:         192.168.1.118
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1



```


The network I'm trying to connect to is TRENDnet

---

### Post by steeldriver on 2013-06-10
Well right there I see 2 access points with the name (SSID) TRENDnet, so that's exactly what I was referring to - I don't *know* that it's your issue, but you could try editing your connection either via the wireless icon on the top panel, or by typing

```
nm-connection-editor
```

Then navigate to the wireless connection, choose 'Edit...' and in the main 'Wireless' properties tab, enter the MAC that you're currently connected to (00:14:D1:C1:C9:23) into the BSSID: box, and save

If that doesn't help, then another source of connection instability with the iwlwifi driver in particular is Wireless-N mode - although the advertised 54Mb/s rate suggests the access point is using Wireless-G mode, you can disable N mode to see if that helps

```

sudo modprobe -rv iwlwifi

sudo modprobe -v iwlwifi 11n_disable=1
```

If *that* helps it can be written into a config file - otherwise it reverts when you reboot

---

