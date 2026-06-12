---
title: "Can not ping router in Ubuntu 12.04, works fine in Windows"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by thevadar on 2012-12-23
Hi,

I have recently bought a HP Envy DV7-7201 which had Windows 8 on it. I installed Ubuntu 12.04 alongside it and everything was fine at home. I could access the internet through my wireless router (RTA10235WE) using Ubuntu.

I am visiting family for the holidays who have a Vodafone EasyBox wireless router. Windows 8 connects to the router fine. It uses WPA with TKIP encryption (802.11n).

However, Ubuntu detects the network but does not establish a connection. I can not ping or access the router (I can just fine in Windows).

After reading through lots of similar issues I couldn't solve the issue. Could someone please help me solve this? I would be so grateful. Here is some info others have asked for in similar threads.

vadar@vadar2:~$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr a0:b3:cc:4b:3a:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28928 (28.9 KB)  TX bytes:28928 (28.9 KB)

wlan0     Link encap:Ethernet  HWaddr 84:a6:c8:d5:05:0c  
          inet6 addr: fe80::86a6:c8ff:fed5:50c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4601 (4.6 KB)  TX bytes:20177 (20.1 KB)
```

vadar@vadar2:~$ iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Nieuwelaar_DSL"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 6A:C6:1F:3B:EB:F0   
          Bit Rate=27 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

eth0      no wireless extensions.
```

vadar@vadar2:~$ nm-tool
```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        A0:B3:CC:4B:3A:2F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        84:A6:C8:D5:05:0C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Nieuwelaar_DSL:  Infra, 6A:C6:1F:3B:EB:F0, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA
```

vadar@vadar2:~$ rfkill list all
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

vadar@vadar2:~$ iwlist chan
```
lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
eth0      no frequency information.
```

---

### Post by Hadaka on 2012-12-23
Hi, this may help

[http://ubuntuforums.org/showthread.php?t=2042332&highlight=iwlwifi](http://ubuntuforums.org/showthread.php?t=2042332&highlight=iwlwifi)

---

### Post by thevadar on 2012-12-23
Hi Hadaka,

Thanks for the response but I have tried that fix. I just tried it again to double check but no luck.

I tried both,

```
sudo gedit /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1

sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

Any other suggestions?

---

### Post by ahallubuntu on 2012-12-23
As a side note: is there some reason they are using WPA & TKIP and not WPA2 & AES?  (or is it really set to "TKIP + AES"?)  Because TKIP limits you to 54Mbps (802.11g speeds).  You need to use AES to get the faster speeds 802.11n offers.

Plus, "WPA" itself has a few security holes.  WPA2 is more secure.  If all devices are modern, WPA2 should work fine.  Some old computers may have trouble with WPA2.

Not to say changing it to WPA2/AES will fix your problem (it might!), but if the owners didn't choose those settings on purpose you might make a gentle suggestion about changing them...

---

### Post by fdrake on 2012-12-23
i don't think it's actually ubuntu since it work fine everywherelse .
[http://forum.xda-developers.com/showthread.php?t=1237247](http://forum.xda-developers.com/showthread.php?t=1237247)

try to factory reset the router (if you have permission to do it) or

or just use windows 

or use the wifi connection through your smartphone (via usbcable/hotspot) connected to the laptop.

---

