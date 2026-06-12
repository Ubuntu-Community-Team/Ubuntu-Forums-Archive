---
title: "Atheros AR2413 can't connect to wireless-network"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by r!ots on 2009-12-03
Hey guys,

I recently did a fresh ubuntu karmic koala install on a friend's Fujitsu-Siemens Amilo A1650G laptop. So far everything works quite alright, only problem we have is the wireless. It uses an Atheros AR2413 ethernet controller.

When freshly installed, with the ath5k drivers in use, the network-manager finds the networks in range, but isn't able to connect to them. It goes on and on, trying to connect but isn't able to get an ip-adress and eventually asks for the password again. Somewhere I read using WiCD would solve the issue, but it didn't. Installing the ubuntu-backport-modules didn't help either. So I did some research, after which I installed the latest trunk MadWifi-drivers, but again the wireless networks can be seen, but I can't connect to them.

Do you have any ideas what could be the issue? Any help would be great, since a laptop without wireless network capabilities is quite useless. For now I set up a dual boot with WinXP, but it would be nice to uninstall windows again.

Some more information:

```
richard@elsuri:~$uname -a
Linux elsuri 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
```

```
richard@elsuri:~$ lspci -nnk | grep -i net -A2
02:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci, ath5k
02:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp
```

```
richard@elsuri:~$ egrep -v "^$|^#" /etc/network/interfaces
auto eth0
iface eth0 inet dhcp
```

```
richard@elsuri:~$ ifconfig
ath0      Link encap:Ethernet  Hardware Adresse 00:02:e3:46:d2:11  
          inet6-Adresse: fe80::202:e3ff:fe46:d211/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  Hardware Adresse 00:0a:e4:af:8a:69  
          inet Adresse:192.168.0.104  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::20a:e4ff:feaf:8a69/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3994 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6027753 (6.0 MB)  TX bytes:580311 (580.3 KB)
          Interrupt:23 Basisadresse:0xa000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  Hardware Adresse 00-02-E3-46-D2-11-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:49441 errors:0 dropped:0 overruns:0 frame:4458
          TX packets:13021 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:280 
          RX bytes:6393013 (6.3 MB)  TX bytes:924850 (924.8 KB)
          Interrupt:20
```

```
richard@elsuri:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"flinkblink"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1E:58:82:B0:99   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-50 dBm  Noise level=-96 dBm
          Rx invalid nwid:19867  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
richard@elsuri:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

```
richard@elsuri:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wifi0     no frequency information.

ath0      26 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)
```

```
richard@elsuri:~$ lsmod | grep ath
ath_rate_sample        12508  1 
ath_pci               196820  0 
wlan                  228528  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               362144  3 ath_rate_sample,ath_pci
```

```
richard@elsuri:~$ dmesg | grep ath
[    2.062153] device-mapper: multipath: version 1.1.0 loaded
[    2.062159] device-mapper: multipath round-robin: version 1.0.0 loaded
[   18.174545] ath_pci 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.769960] MadWifi: ath_attach: Switching rfkill capability off.
[   19.285715] ath_pci: wifi0: Atheros 2413: mem=0xc0200000, irq=20
[   35.936045] ath0: no IPv6 routers present
```

And this is the network I try to connect to:

```
richard@elsuri:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
Cell 05 - Address: 00:1E:58:82:B0:99
                    ESSID:"flinkblink"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=44/70  Signal level=-51 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:ath_ie=dd0900037f01010020ff7f
```

I tried connecting to another WPA2-encrypted and to one with WEP-encryption, but again with no luck..

---

### Post by amsum on 2009-12-03
Atheros Cards are facing some problem in Karmic.
Try this one.

Look into the file 
/etc/modprobe.d/blacklist-ath_pci.conf

and then comment out the line... 
blacklist ath5k

so it should look like
#blacklist ath5k

Now Save it and reboot the system. It must recognize the wireless after rebooting.

---

### Post by drpjkurian on 2009-12-04
Hi
You can give a try to my thread if nothing else works.

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by r!ots on 2009-12-04
Hey,

the wireless is recognized on booting with the ath_pci(MadWifi)-drivers loaded. The problem isn't the detection of the wireless controller, the problem is to connect to a wireless network. The attempts always end in a time out. 
Uncommenting the blacklisting of the ath5k-driver wouldn't help, since I don't want to load them. They were loaded by default on the fresh install, but didn't work either.

@drpjkurian: I already read and tried the suggestions you posted in your thread. Again to no avail..

---

### Post by Longhorn_ on 2009-12-07
I'm having same problem (with amilo L1310G and rather annoying software -controlled wlan on/off switch..)

With fresh installation of 9.10 I got a list of wlan -networks. Now after some hassle (with ndiswrapper etc) I can't see anything with wireless anymore...

lspci | grep Ath
```
02:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```lshw -C network
```
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:a9:7f:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.55+,05/05/2005,4.1.2.56 latency=128 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:23 memory:c0200000-c020ffff
 ....and here was info about wired network....

```Now wlan seems to be disabled (how to enable it again?) and the driver is not the correct one.. I've done the comment-out at /etc/modprobe.d/blacklist-ath_pci.conf

Any help? I'm getting frustrated...

---

### Post by Longhorn_ on 2009-12-07
OMG.

I decided to try once more by myself.

I did what drpjkurian has written behind his mysterious link there (steps 1-14 and restart, no wicd), and it just worked! It was like sixth link with series of commands to follow, but first one that helped me!

Thanks a lot! :)

---

### Post by drpjkurian on 2009-12-08
> **Longhorn_ said:**
> OMG.

I decided to try once more by myself.

I did what drpjkurian has written behind his mysterious link there (steps 1-14 and restart, no wicd), and it just worked! It was like sixth link with series of commands to follow, but first one that helped me!

Thanks a lot! :)

Hi Longhorn

You are most welcome

With regards
Dr Kurian

---

### Post by timmyhiggy on 2010-05-12
Hi

I am having a problem with my wireless card (atheros ar5005g) which seems to have a similar problem, in that I type the WPA code in but it never actually connects. I am using 10.04, would the instructions given in the linked thread still be relevant?

---

### Post by loghete on 2010-05-13
I'm having exactly the same problem with my AR2413, first on 9.10 (but that eventually fixed itself, somehow) and now on 10.04. I still haven't found a solution..

---

### Post by cancer_22k on 2010-08-18
Hi Guys,

I am facing the same problem (same as loghete). Any help is highly appreciated.

regards

---

### Post by loghete on 2010-09-15
Yes, I too am still having this problem. Been using a cable connection all this time, but I'd still be more than pleased if I got the wi-fi working :)

---

