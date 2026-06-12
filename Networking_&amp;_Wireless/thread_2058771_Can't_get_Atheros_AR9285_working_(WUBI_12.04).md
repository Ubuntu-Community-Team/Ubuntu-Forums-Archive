---
title: "Can't get Atheros AR9285 working (WUBI 12.04)"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by Simplyred37 on 2012-09-16
Hi all, I hope everybody is enjoying the weekend.  I have an HP G62 laptop whith an Atheros AR9285 wireless chipset which didn't get recognized by the WUBI installation (Ubuntu 12.04).
I have searched around and here are a couple of system outputs that might provide information on my system configuration : 

This is the output of "rfkill list" :
Code: 

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

This is the output of "sudo lshw -class network"  : 

Administration
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: XXXXXXXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-30-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 64:31:50:59:b7:33
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.115 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0010000-f0010fff memory:f0000000-f000ffff memory:f0020000-f002ffff

This is the output of "ifconfig" :

eth0      Link encap:Ethernet  HWaddr 64:31:50:59:b7:33  
          inet addr:192.168.0.115  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6631:50ff:fe59:b733/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95348508 (95.3 MB)  TX bytes:5594868 (5.5 MB)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168497 (168.4 KB)  TX bytes:168497 (168.4 KB)

wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:39:6c:81  
          inet6 addr: fe80::4e0f:6eff:fe39:6c81/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


This is the out output of "iwconfig" : 
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"1429"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:17:9A:2F:5E:B8   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

eth0      no wireless extensions.

I am hoping that someone can help me with this.
Again, I am a beginner with Ubuntu so would appreciate if you would go easy on me! I have noticed that the system might have detected-loaded the wrong chip&#349;et-driver ("driver=r8169").   

Does that help ? Let me know if there any tests I can do ....

Thanks in advance !!!

Daniel from Montreal, Canada!!!!

---

### Post by Simplyred37 on 2012-09-16
Hi again, here is the output of nm-tool : 
```
 


- Device: wlan0  [1429] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        4C:0F:6E:39:6C:81

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    thaiga:          Infra, 84:C9:B2:69:39:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA
    1429:            Infra, 00:17:9A:2F:5E:B8, Freq 2447 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    BELL365:         Infra, 00:23:51:E3:BB:09, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP

``` 

It seems as if Ubuntu is trying to connect to my home WiFi network and it asks me for the WPA2 key, which I enter, but it doesn't seem to accept it as valid.  And it keeps trying to connect, but can't, and it will come back again, asking me to enter my WPA2.  Thought I'd provide this extra info, which I overlooked to include in my original post.  Thanks in advance !!!  Daniel.

---

