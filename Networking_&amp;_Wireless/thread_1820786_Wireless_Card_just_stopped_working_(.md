---
title: "Wireless Card just stopped working :("
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by scottyedmonds on 2011-08-08
No idea what happened, cant figure it out; I get Wireless disabled by hardware switch, but it's switched on :(

```

scotty@scotty-Pavilion:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:69:6a:e5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.39 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f4000000-f4003fff ioport:4000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 61
       serial: 00:21:5c:13:87:a9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-10-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f4100000-f4101fff

```

---

### Post by chili555 on 2011-08-08
Is it a Dell? Please run and post:```
rfkill list all
```Thanks.

---

### Post by scottyedmonds on 2011-08-08
Oh, and it's a HP DV2990. Ubuntu has been on it and running perfectly for me, for about 8 months
```
scotty@scotty-Pavilion:~$ sudo rfkill list all
[sudo] password for scotty: 
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
scotty@scotty-Pavilion:~$ 

```

---

### Post by chili555 on 2011-08-08
Please try an experiment. In a terminal, please do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Is the wireless working now? If so, we can write one file to make this persistent.

By the way, does your wireless ordinarily turn on and off with Fn+F12? I worked on a case a couple of weeks ago, I worked on a case where the combination was Alt+F12. You might try other combinations.

---

### Post by scottyedmonds on 2011-08-08
unfortunately that didn't work. The onyl thing that every worked to turn it off was the switch, which appears to be working fine, i can turn the Bluetooth on and off no issues

---

### Post by chili555 on 2011-08-08
> unfortunately that didn't work.That doesn't tell me much. What didn't work? The commands made no change? Alt+F12 didn't turn wireless on? Since I suggested you try other combinations, did you try unsuccessfully, Alt+F11? Ctrl+F12? Fn+F2? Any and every other key combination??

---

### Post by scottyedmonds on 2011-08-08
I tried a vast number of key-stroke combinations, I've already done those commands. I'm kind of lost at this point.

---

### Post by lkjoel on 2011-08-09
What's the output of these commands?
```
sudo /etc/init.d/networking restart
sudo ifconfig
sudo iwconfig
sudo nm-tool

```

---

### Post by dlcurry on 2011-08-09
Chilli555,
Seeing a lot of 'wifi worked, upgraded Ubuntu, no work no more' msgs,  including mine.  That tell you anything, maybe a recent update canked a  bunch of vendor/chipsets?

OP - hang tough, you are not alone.
Dave

---

### Post by scottyedmonds on 2011-08-09
```

scotty@scotty-Pavilion:~$ sudo /etc/init.d/networking restart
[sudo] password for scotty: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
scotty@scotty-Pavilion:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
scotty@scotty-Pavilion:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:69:6a:e5  
          inet6 addr: fe80::21d:72ff:fe69:6ae5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:81010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20748288 (20.7 MB)  TX bytes:26279412 (26.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6376 (6.3 KB)  TX bytes:6376 (6.3 KB)

scotty@scotty-Pavilion:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions.

scotty@scotty-Pavilion:~$ sudo nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1D:72:69:6A:E5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        00:21:5C:13:87:A9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


scotty@scotty-Pavilion:~$ 

```

---

### Post by lkjoel on 2011-08-09
Could you give me the output of this command?
```
sudo rfkill list all

```

---

### Post by scottyedmonds on 2011-08-09
```


scotty@scotty-Pavilion:~$ sudo rfkill list all
[sudo] password for scotty: 
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
scotty@scotty-Pavilion:~$ 


```

---

