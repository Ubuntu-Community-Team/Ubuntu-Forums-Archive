---
title: "can connect to modem via wifi but almost never to internet (thinkpad t420s)"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by kongci on 2012-01-17
Hi!

At home, I can connect to my modem/router but mostly I cannot access the Internet. Sometimes it works but I wasn't able to find a pattern. Other Wifi-networks (at work etc) are working fine.

My laptop is a Thinkpad T420s and I am using Xubuntu 11.10.

I have seen that other people in the forum had similar problems but could not understand how or whether they fixed it.

Any advice/pointers will be appreciated!

```
s@stp:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:9F:73:92

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [haggi] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        08:11:96:95:14:20

  Capabilities:
    Speed:           6 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *haggi:          Infra, 00:1C:28:4C:2A:75, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WPA2

  IPv4 Settings:
    Address:         192.168.13.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.13.1

    DNS:             192.168.13.1


- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             disconnected
  Default:           no
  HW Address:        16:88:68:8C:0B:94

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on
``````
s@stp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"haggi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:28:4C:2A:75   
          Bit Rate=27 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

usb0      no wireless extensions.

``````
s@stp:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlagn

```

---

### Post by sakishrist on 2012-01-17
Hello,

Wild guess: Have you tried to change the DNS manually to see whether the ones that your router uses are problematic?

I am not very familiar with Xfce but there should be an option in your network manager to change the DNS. Try the google one (8.8.8.8 or 8.8.4.4)

Or if you want a quicker way to check if you have internet but a problem with the DNS, try entering an IP of a site instead of it's domain (let's say, try entering [http://74.125.113.106/](http://74.125.113.106/) which is google's website).

If that is the problem, you most probably should talk with the ISP support.

Cheers,
Sakis

---

