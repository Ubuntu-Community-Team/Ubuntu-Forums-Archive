---
title: "LAN/WAN lost after upgrade and restart"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by kfstephensii on 2013-05-06
I upgraded my laptop to 13.04 and everything went fine. It restarted and requested a partial upgrade which went well. When starting the computer at home that evening, I was unable to connect to wireless network or use wired connection.
Being a dual-boot machine, I checked and all the hardware works in Windows.

The machine connects but I can transfer no data. I tried wifi dongles and had identical result: connection but no data.

I've spent hours with no success. This makes the machine almost a brick since I work mainly with files in the cloud.

Here are my results from running wireless_script as mentioned elsewhere in the forums. 
[http://pastebin.ubuntu.com/5638525/](http://pastebin.ubuntu.com/5638525/)

If any additional information is needed, I'm glad to oblige.

---

### Post by chili555 on 2013-05-06
This is a well-known issue. Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it works, let's try to troubleshoot the issue in the router. I have an Intel device using iwlwifi and an N router and mine works perfectly. Therefore, I suspect it's actually a router issue. We'll find out.

Reference:> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:D7:19:41:54:xx   
          [COLOR="#FF0000"]Bit Rate=216 Mb/s [/COLOR]  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  

---

### Post by kfstephensii on 2013-05-06
When I run
```
sudo modprobe -r iwlwifi
```
I receive
```
FATAL: Module iwlwifi is in use.
```

---

### Post by chili555 on 2013-05-06
> **kfstephensii said:**
> When I run
```
sudo modprobe -r iwlwifi
```
I receive
```
FATAL: Module iwlwifi is in use.
```Please try:```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```wlan0 should come right back up; check:```
iwconfig
```Now does it connect and pass traffic?

---

### Post by kfstephensii on 2013-05-06
Here's what I did not the system response:
```

$ sudo ifconfig wlan0 down
$ sudo modprobe -r iwldvm
$ sudo modprobe -r iwlwifi
Error: missing module name.
FATAL: Error running remove command for iwlwifi
$ sudo modprobe iwlwifi 11n_disable=1

```

Being at school, I have to open a browser to enter my credentials to access the wifi. I was able to reach the page and do so, being informed that I connected. However, I cannot access any webpages from there or update any cloud drives, weather, ...
After this, I ran the following:
```

$ iwconfig
wmx0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"HSUOpenRange"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:55:B4:6E:F0   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:3   Missed beacon:0

```

If it is useful to know, I am able to access the network when I boot from the LiveCD.

---

### Post by chili555 on 2013-05-06
Please run and pastebin the wireless script again. Also, let us see:```
cat /sys/bus/pci/drivers/iwlwifi/module/parameters/11n_disable 

```Let's make sure the parameter stuck.

---

### Post by kfstephensii on 2013-05-06
The option did stick:
```

$ cat /sys/bus/pci/drivers/iwlwifi/module/parameters/11n_disable
1

```

The new results from wireless_script are at: [http://pastebin.ubuntu.com/5638816/](http://pastebin.ubuntu.com/5638816/)

---

### Post by chili555 on 2013-05-06
Excellent. The parameter is there.

Here is the only thing I see that's a bit mysterious:> IPv4 Settings:
    Address:         10.70.3.20
    Prefix:          24 (255.255.255.0)
    Gateway:         10.70.3.254

    [COLOR="#FF0000"]DNS:             10.16.1.1
    DNS:             10.16.1.2[/COLOR]

Is the DNS nameserver that the gateway assigned actually reachable?```
ping -c3 10.16.1.1
```Can you open web pages by number?```
firefox http://173.194.75.99
```Can you ping Google by number?```
ping -c3 173.194.75.99
```

I suspect a DNS problem.

---

### Post by kfstephensii on 2013-05-06
In Chromium, I was able to reach Google using [http://173.194.75.99](http://173.194.75.99).

Here are the results from the pings:
```

kenny:~$ ping -c3 10.16.1.1
PING 10.16.1.1 (10.16.1.1) 56(84) bytes of data.
64 bytes from 10.16.1.1: icmp_req=1 ttl=127 time=167 ms
64 bytes from 10.16.1.1: icmp_req=2 ttl=127 time=1.06 ms
64 bytes from 10.16.1.1: icmp_req=3 ttl=127 time=1.07 ms

--- 10.16.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.061/56.467/167.261/78.343 ms
kenny:~$ ping -c3 173.194.75.99
PING 173.194.75.99 (173.194.75.99) 56(84) bytes of data.
64 bytes from 173.194.75.99: icmp_req=1 ttl=44 time=66.6 ms
64 bytes from 173.194.75.99: icmp_req=2 ttl=44 time=66.3 ms
64 bytes from 173.194.75.99: icmp_req=3 ttl=44 time=65.4 ms

--- 173.194.75.99 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 65.466/66.167/66.650/0.588 ms

```

---

### Post by chili555 on 2013-05-06
Frankly, I am just a bit stumped. I suspect it has to do with the re-direct to supply your credentials. When you run the live CD, authenticate and then run:```
nm-tool
```Are all these settings similar?> IPv4 Settings:
    Address:         10.70.3.20
    Prefix:          24 (255.255.255.0)
    Gateway:         10.70.3.254

    DNS:             10.16.1.1
    DNS:             10.16.1.2Are there any clues, errors, warnings, easter eggs, etc. here?```
dmesg | grep -e wlan -e iwl
```

---

### Post by kfstephensii on 2013-05-06
Here are the results from dmsg: [http://pastebin.ubuntu.com/5638924/](http://pastebin.ubuntu.com/5638924/).
Let me restart the machine from the CD and I'll let you know.

---

### Post by kfstephensii on 2013-05-06
Here are the results from the LiveCD:
```

ubuntu@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        00:1D:E1:4A:C7:9A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [HSUOpenRange] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        64:80:99:3E:DA:74

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HSUWireless:     Infra, 00:21:55:B4:6E:F1, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 Enterprise
    HSUWireless:     Infra, 00:18:B9:3C:13:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    HP-nomodel.5CF9E1: Infra, 02:2E:BE:CC:5E:CB, Freq 2437 MHz, Rate 11 Mb/s, Strength 22
    HSUOpenRange:    Infra, 00:18:B9:3C:13:A1, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    HSUWireless:     Infra, 00:21:55:B4:68:B1, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 Enterprise
    HSUOpenRange:    Infra, 00:21:55:B4:68:B0, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    *HSUOpenRange:   Infra, 00:21:55:B4:6E:F0, Freq 2412 MHz, Rate 54 Mb/s, Strength 45

  IPv4 Settings:
    Address:         10.70.7.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.70.7.254

    DNS:             10.16.1.1
    DNS:             10.16.1.2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        D0:67:E5:35:E7:E6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

---

