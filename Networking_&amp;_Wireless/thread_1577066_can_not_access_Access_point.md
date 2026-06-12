---
title: "can not access Access point"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by ilna on 2010-09-18
The aim is to share my internet access (ADSL/pppoe) with my son's PC. Just now I have configure AP/hostapd
```

interface=wlan0
driver=nl80211
ssid=myAp
country_code=RUS
hw_mode=g
channel=11

macaddr_acl=0

wpa=1
wpa_key_mgmt=WPA-PSK
wpa_passphrase=tratata
rsn_pairwise=CCMP
```

with this wlan0 interface in /etc/network/intefaces:
```

auto wlan0
iface wlan0 inet static
address 10.8.0.1
network 10.8.0.0
netmask 255.255.255.0
broadcast 10.8.0.255
```

Also I have installed dhcp3 server with /etc/dhcp3/dhcpd.conf:
```

ddns-update-style none;
option domain-name "myNet";
option domain-name-servers 208.67.222.222, 208.67.220.220;
default-lease-time 42300;
max-lease-time 84600;
log-facility local7;
subnet 10.8.0.0 netmask 255.255.255.0 {
  range 10.8.0.100 10.8.0.200;
  option routers 10.8.0.1;
}
```

and /etc/default/dhcp3-server:
```

INTERFACES="wlan0"
```

Also have added to iptables:
```

sudo /sbin/iptables -A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmt
sudo /sbin/iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j MASQUERADE
```

hostapd does start with this config, and from son's client PC (Kubuntu Maverick was installed from CD) I see this the AP:
```

~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: tratata
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=48 dBm  
                    Encryption key:on
                    ESSID:"myAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000444124b3
                    Extra: Last beacon: 470ms ago
                    IE: Unknown: 0006616E6C694150
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

I have configured connection on son's PC via kde network manager frontend with defaults wrt IP (dhcp), WPA/WPA2 Personal security, Infrastructure mode, BSSID as MAC in AP. Clicking on this connection in network applet (in system tray) does nothing.

Where to dig in? Which additional information I must supply?

P.S. You see, on son's PC I have CD distribution only without an opportunity to install other software.

---

