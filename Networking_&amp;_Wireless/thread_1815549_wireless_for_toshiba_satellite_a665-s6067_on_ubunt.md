---
title: "wireless for toshiba satellite a665-s6067 on ubuntu 11.04?"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by weeman1 on 2011-07-31
hey all. im running ubuntu 11.04 on unity 2D. my wired connection works, but i cannot enable my wireless internet. just wondering if theres any way i can get wireless???

i plan on using ubuntu for an OS when i am programming during school and would like to have the wireless.

---

### Post by wildmanne39 on 2011-07-31
Hi, run these commands in a terminal please:
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
nm-tool
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lkjoel on 2011-07-31
Could you also give us the output of:
```
uname -a
```
```
lsb_release -a
```
```
ifconfig
```
```
sudo /etc/init.d/networking restart
```

---

### Post by weeman1 on 2011-07-31
Sorry for the late reply guys! I posted this right before I went to work and just came back an hour ago!

wildmanne39:
```
clement@ubuntu:~$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
clement@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

clement@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
clement@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        70:5A:B6:C3:58:6C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             68.238.64.12


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             unavailable
  Default:           no
  HW Address:        00:26:4D:93:7C:BD

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



```

---

### Post by weeman1 on 2011-07-31
reply for lkjoel:

```
clement@ubuntu:~$ uname -a
Linux ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
clement@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty
clement@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:c3:58:6c  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::725a:b6ff:fec3:586c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:981786 (981.7 KB)  TX bytes:140874 (140.8 KB)
          Interrupt:45 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

clement@ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for clement: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]
```

---

### Post by nm_geo on 2011-07-31
This normally indicates a hard ware switch turned off,

clement@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    **[COLOR=Red]Hard blocked: yes[/COLOR]**

---

### Post by wildmanne39 on 2011-07-31
Hi, nm_geo is correct it looks like there is a hardware switch off, you can turn it on with like f12  fn f12 something like that, or you may have a sliding switch like on hp laptops.

Also would you please run this command and post the outcome here.
```
modinfo rtl8191SE | grep 8172

```
Thank you

---

### Post by weeman1 on 2011-08-01
Here's the outcome:

clement@ubuntu:~$ modinfo rtl8191SE | grep 8172
ERROR: modinfo: could not find module rtl8191SE

---

### Post by wildmanne39 on 2011-08-01
Hi, run these commands please
```
sudo lshw -C network
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

Did you find the switch or correct key to turn your wireless on?
Thank you

---

