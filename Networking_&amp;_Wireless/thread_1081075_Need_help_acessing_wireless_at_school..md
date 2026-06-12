---
title: "Need help acessing wireless at school."
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by maz91379 on 2009-02-26
So I'm not exactly how to access my schools wireless network on my ubuntu partition, my student help service desk helped me get on vista but had no clue what to do with wireless setup for ubuntu. So i think i have 8.10 installed and this is a link to the setup guide for [xp and macs]("http://www.deakin.edu.au/its/wireless/deakin/user-guides.php")  at my school, i need to connect to DeakinSecure do i need to install anything extra ? would really appreciate if someone could help me out.

---

### Post by ajmorris on 2009-02-27
hi there,
First off, we need some information about what wireless hardware you have.
Can you please paste the output:
```
sudo lspci
```

Also, do you know what drivers you are using for your card? i.e ndiswrapper or native?

DeakinSecure uses a WPA2 key, which is sometimes an issue, but can usually be gotten working via different methods.

AJ

---

### Post by maz91379 on 2009-02-27
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

I think im using ndiswrapper but i really have no idea and im at burwood.

---

### Post by ajmorris on 2009-02-27
Ok, you have a Broadcom 4312 Wireless Card. So you have 2 options, the native bcm43xx drivers, or ndiswrapper.

Can you post the output of the following:
```
sudo ndiswrapper -l
```
```
sudo ifconfig
```
```
sudo iwlist scanning
```


AJ

---

### Post by maz91379 on 2009-02-28
```
sudo: ndiswrapper: command not found

```

```
 sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3d:ca:74  
          inet6 addr: fe80::223:8bff:fe3d:ca74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:148371580 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:248 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:8b:b0:9c  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe8b:b09c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:308 errors:0 dropped:0 overruns:0 frame:4
          TX packets:314 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:223179 (223.1 KB)  TX bytes:68008 (68.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2432 (2.4 KB)  TX bytes:2432 (2.4 KB)

```

```
sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:04:ED:95:A0:78
                    ESSID:"cytryny"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-26 dBm  Noise level:-21 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

```
I would assume the first dialogue means i dont have it installed??:confused:

---

### Post by ajmorris on 2009-02-28
> **maz91379 said:**
> ```
sudo: ndiswrapper: command not found

``````
 sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3d:ca:74  
          inet6 addr: fe80::223:8bff:fe3d:ca74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:148371580 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:248 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:8b:b0:9c  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe8b:b09c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:308 errors:0 dropped:0 overruns:0 frame:4
          TX packets:314 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:223179 (223.1 KB)  TX bytes:68008 (68.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2432 (2.4 KB)  TX bytes:2432 (2.4 KB)

``````
sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:04:ED:95:A0:78
                    ESSID:"cytryny"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-26 dBm  Noise level:-21 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

```I would assume the first dialogue means i dont have it installed??:confused:

Sort of. You dont have ndiswrapper installed. But you do have a wireless network interface, so the native drivers are in use. This is, IMO, the preferred way, if you are using a WPA2 encrypted network, as ndiswrapper is a little more annoying, and fiddly to configure with WPA2.

What exactly is the problem with connecting to your wireless network at University? You are using the gnome network manager i assume? (the default network icon in your system tray)... Could you please post any errors you are recieving? Also, you might like to look into the application "wicd" as an alternative to Network Manager.

AJ

---

### Post by maz91379 on 2009-02-28
Well i wasn't receiving any errors however i couldn't get it to connect.
Like the tech guy really wasn't sure what to do, He was just like ummm i haven't seen this before. I installed the network manager hopefully it works better? Like idk if i need to select a encryption setting that i dont have or what in order to make it work.

---

### Post by ajmorris on 2009-02-28
> **maz91379 said:**
> Well i wasn't receiving any errors however i couldn't get it to connect.
Like the tech guy really wasn't sure what to do, He was just like ummm i haven't seen this before. I installed the network manager hopefully it works better? Like idk if i need to select a encryption setting that i dont have or what in order to make it work.


The link to the info about your Uni's wireless network, said WPA2 and nothing about a Pre-Shared Key. So you should choose the non-PSK WPA2 option in your network manager, to put the network encryption key in. It should then connect... If you get no errors being displayed, if it doesnt connect, then we can see if it is a driver issue. Please post the ouput of: ```
sudo dmesg
```from a terminal if this is the case.


AJ

---

### Post by btehan on 2009-03-10
Hey.. this is the configuration you want for DeakinSecure on abuntu

Security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP)
Anonymous Identity:
CA Certificate: /etc/ssl/certs/Thawte_Premium_Server_CA.pem
PEAP Version: 0
Inner Authentication: MSCHAPv2
Username: <yourusername>@deakin.edu.au
Password: <yourpassword>

---

