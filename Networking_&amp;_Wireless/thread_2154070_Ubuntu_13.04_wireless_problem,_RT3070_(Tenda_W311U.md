---
title: "Ubuntu 13.04 wireless problem, RT3070 (Tenda W311U)"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by johnyy on 2013-06-13
Hello,

I am installing Ubuntu 13.04 on a desktop computer that connect to internet via Tenda W311U. According to the company's webpage and the driver I downloaded from it, this device uses RT3070 chipset. 

What I did so far is compile the driver with two security fetures turned on and insert the mod into system. At some point I see my SSID from command iwlist ra0 scanning. But after restart I am back to no where.

I am connecting with cable not, it is a ugly line on the floor which I would really like to remove.

Any help/suggestion is appreciated. 

```
lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 003: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter


```
```

lsmod | grep rt
rt5370sta             797094  0 
parport_pc             28152  1 
parport                46345  3 lp,ppdev,parport_pc

```
```

iwconfig
ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


eth0      no wireless extensions.


lo        no wireless extensions.



```

---

### Post by chili555 on 2013-06-13
> ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless AdapterThis device should work without any compiling in 13.04 using the driver rt2800usb:> $ modinfo rt2800usb | grep 3070
alias:          usb:v[COLOR="#FF0000"]148F[/COLOR]p[COLOR="#FF0000"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*Unless, of course, something else is wrong. Let's try it:```
sudo modprobe -r rt5370sta
sudo modprobe rt2800usb
```Was a wireless interface created, ideally wlan0?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```After you detach the ethernet cable, does it connect? Are there any informative messages?```
dmesg | grep -e rt5 -e rt2
```

---

### Post by johnyy on 2013-06-13
Thanks for your quick reply!

I forgot to mention it's because rt2800usb wasn't working properly so I started to try another driver.

The Connection Manager says I am connected but I can't get internet. Not even 192.168.0.1 which is the gateway for the AP.


iwconfig
```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"YHome"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: C8:3A:35:4E:87:38   
          Bit Rate=45 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:8   Missed beacon:0

```



sudo iwlist wlan0 scan is scaning properly

```

 Cell 02 - Address: C8:3A:35:4E:87:38
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"YHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000026c2569f66
                    Extra: Last beacon: 1116ms ago
                    IE: Unknown: 000559486F6D65
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16070F0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```

dmesg | grep -e -rt5 -e rt2
```

[  295.862560] rtusb init rt2870 --->
[  295.863403] usbcore: registered new interface driver rt2870
[ 3941.507251] usbcore: deregistering interface driver rt2870
[ 3946.807043] usbcore: registered new interface driver rt2800usb

```

---

### Post by chili555 on 2013-06-13
> wlan0     IEEE 802.11bgn  ESSID:"YHome"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: C8:3A:35:4E:87:38   
          Bit Rate=45 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:8   Missed beacon:0Looks pretty solid! Now let's dig deeper:```
ifconfig
route -n
nm-tool
cat /etc/resolv.conf
cat /etc/network/interfaces
```Thanks.

---

### Post by johnyy on 2013-06-13
Tried the following after disabling Ethernet

ifconfig

```

wlan0     Link encap:Ethernet  HWaddr 00:b0:8c:06:ca:d4  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2b0:8cff:fe06:cad4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29973 (29.9 KB)  TX bytes:58352 (58.3 KB)

```

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

nm-tool
```

- Device: wlan0  [YHome] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        00:B0:8C:06:CA:D4


  Capabilities:
    Speed:           135 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Kole:            Infra, 00:24:A5:15:6E:7B, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Doraemon:        Infra, B0:48:7A:BF:94:1A, Freq 2417 MHz, Rate 54 Mb/s, Strength 55 WPA
    *YHome:          Infra, C8:3A:35:4E:87:38, Freq 2442 MHz, Rate 54 Mb/s, Strength 79 WPA2
    calahk:          Infra, 64:70:02:52:B8:4E, Freq 2427 MHz, Rate 54 Mb/s, Strength 55
    Now24:           Infra, 30:85:A9:6A:31:F2, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2


  IPv4 Settings:
    Address:         192.168.0.200
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             203.185.0.33
    DNS:             203.185.0.34
    DNS:             203.185.0.35

```

cat /etc/resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```


cat /etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
allow-hotplug wlan0

```

---

### Post by chili555 on 2013-06-13
> inet addr:192.168.0.[COLOR="#FF0000"]200[/COLOR]Is this a static IP you set up or did the router give you that one by DHCP?> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
allow-hotplug wlan0I wonder what that is about?? Please comment that last part out; thus:```
gksudo gedit /etc/network/interfaces
```Add a hashmark:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
**#**allow-hotplug wlan0
```Proofread, save and close gedit. Reboot and let us hear your report:```
sudo modprobe rt2800usb
ping -c3 192.168.0.1
ping -c3 www.google.com
```All your other readings look great.

---

### Post by johnyy on 2013-06-13
DHCP gave me 192.168.0.200 for the wireless card
and 192.168.0.100 for the Ethernet card.

Amazing the wifi is working now! Thank you very much! I spent quite a few hours trying to install a proper driver and gotten nowhere.

Final question:
What does allow-hotplug wlan0 do and why it is preventing the wifi traffic to go through?

Aside from that, bravo! And thanks again.

---

### Post by chili555 on 2013-06-13
> What does allow-hotplug wlan0 do and why it is preventing the wifi traffic to go through?I haven't any idea. I'm sort of a zombie killer kind of technician; if I don't understand it (and Google doesn't help me much), I comment it out (kill it!!) and see what happens. It seems to have worked!

Please mark the thread Solved. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by dvdhudson33 on 2013-06-14
Reading this, I guess I'm lucky that mine (a Tenda W311M, which I bought home from the shop about 2 hours ago) worked with Ubuntu straight out of the box.   What makes it better is that it wouldn't run on Windows 7 without drivers on the CD.  Ha!

---

### Post by johnyy on 2013-06-14
> **dvdhudson33 said:**
> Reading this, I guess I'm lucky that mine (a Tenda W311M, which I bought home from the shop about 2 hours ago) worked with Ubuntu straight out of the box.   What makes it better is that it wouldn't run on Windows 7 without drivers on the CD.  Ha!

Lucky you..

I spent at least 4 hours trying to compile and install a new driver without success.

---

