---
title: "Ibm T41 and cisco wireless card: Can't type my password!"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by striscio on 2011-11-06
Hi, I have a strange problem with my ibm T41 laptop. 
I have a WPA2 wireless network in my home and everything went fine until I decided to upgrade to 11.10.
Now if I decide to join my wireless network I see the popup window which tells me that the network needs a password or a key, but I don't have any box where I can type my password. The 'Connect' button is greyed out and I only can click on Cancel (see attached screenshot)

```
elisa@ThinkPad-T41:~$ lspci -nn | grep 'Wireless'
02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
```

```

elisa@ThinkPad-T41:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0d:60:b1:38:13  
          indirizzo inet:192.168.1.110  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::20d:60ff:feb1:3813/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12621 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:17341105 (17.3 MB)  Byte TX:2062219 (2.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:8a:f1:f4:f2  
          indirizzo inet6: fe80::202:8aff:fef1:f4f2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:15706 dropped:0 overruns:0 frame:15706
          TX packets:29 errors:29 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:4641 (4.6 KB)
          Interrupt:11 Indirizzo base:0x8000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:27479 (27.4 KB)  Byte TX:27479 (27.4 KB)

```


```
elisa@ThinkPad-T41:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-95 dBm
          Rx invalid nwid:28608  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:125386   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-95 dBm
          Rx invalid nwid:28608  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:125386   Missed beacon:0
```

```
elisa@ThinkPad-T41:~$ lsmod | grep "airo"
airo                   77500  0 

```

```
elisa@ThinkPad-T41:~$ dmesg |grep airo
[   18.971810] airo(): Probing for PCI adapters
[   19.574101] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   19.574128] airo(): Found an MPI350 card
[   20.525569] airo(eth1): Firmware version 5.41.00
[   20.525573] airo(eth1): WPA supported.
[   20.525577] airo(eth1): MAC enabled 00:02:8a:f1:f4:f2
[   20.527062] airo(): Finished probing for PCI adapters
[  628.028952] airo(eth1): cmd:3 status:7f03 rsp0:0 rsp1:0 rsp2:0
[  634.660572] PM: resume of drv:airo dev:0000:02:02.0 complete after 744.383 msecs
[  662.385536] airo(eth1): cmd:3 status:7f03 rsp0:0 rsp1:0 rsp2:0
[  667.364565] PM: resume of drv:airo dev:0000:02:02.0 complete after 743.948 msecs

```

```
elisa@ThinkPad-T41:~$ sudo lshw -C network
[sudo] password for elisa: 
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:b1:38:13
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.1.110 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8400(size=64) memory:c0240000-c024ffff
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:f1:f4:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0214000-c0217fff memory:c0400000-c07fffff memory:c0800000-c09fffff

```

```
elisa@ThinkPad-T41:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: C0:3F:0E:72:8C:F0
                    ESSID:"SPRINGFIELD"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-27 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

wifi0     Scan completed :
          Cell 01 - Address: C0:3F:0E:72:8C:F0
                    ESSID:"SPRINGFIELD"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-27 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

```
elisa@ThinkPad-T41:~$ lsb_release -d
Description:	Ubuntu 11.10

```

```
elisa@ThinkPad-T41:~$ uname -mr
3.0.0-12-generic i686

```

```
elisa@ThinkPad-T41:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```

Hope that this helps.

---

### Post by striscio on 2011-11-06
Anyone has an idea?
How to try to connect from the terminal to find out if is a gui problem or something wrong at a lower level?

---

