---
title: "Wireless on IBM Thinkpad X31"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by phenixdoc on 2012-05-03
Hi all, ive been cracking at this for 4-5 days now, can't get wireless to work on my ibm thinkpad x31, the wireless card is [Cisco Aironet Wireless 802.11b]("http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b"), PCIID is 14b9:a504.
Ive formatted and decided to setup ubuntu instead of windows for the god knows what time but as always something has to go wrong, its like the world doesn't want me using linux :)

heres all the output i can think of, tried to disable geode-aes and padlock-aes as was suggested here in the forums somewhere (they are listed in modprobe -l but not in the modprobe modules file), tried installing xp (again) and updating firmware, need ideas ppl :) don't wanna give up and go back to windows.

Also note that wifi0 is listed in ifconfig only if i up it, it starts off and lshw lists card as disabled, then i do ifconfig wifi0 up and it appears and lshw no longer lists it as off.

Nothing that i do helps, i can see all the wireless networks but can't connect, it tries to connect for ~20 secs and then says disconnected and tries again.

The 2 networks ive tried to connect to are both unsecure (no wep, no wpa, no nothing)

```

lsb_reslease -d
	Description:	Ubuntu 11.10


iwconfig

eth0      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-105 dBm
          Rx invalid nwid:3698  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33659   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-105 dBm
          Rx invalid nwid:3698  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33659   Missed beacon:0


ifconfig (wifi0 appears onlu after i up it, it starts down)

eth0      Link encap:Ethernet  HWaddr 00:02:8a:ed:02:be  
          inet6 addr: fe80::202:8aff:feed:2be/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:666 dropped:0 overruns:0 frame:666
          TX packets:24 errors:24 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4380 (4.3 KB)
          Interrupt:11 Base address:0x8000 
wifi0     Link encap:UNSPEC  HWaddr 00-02-8A-ED-02-BE-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:0 errors:666 dropped:0 overruns:0 frame:666
          TX packets:24 errors:24 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:4380 (4.3 KB)
          Interrupt:11 Base address:0x8000 


iwlist scan
eth0      Scan completed :
          Cell 01 - Address: 00:1B:2F:E3:59:B8
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/100  Signal level=-78 dBm  Noise level:-105 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100

wifi0     No scan results


lshw (after i up wifi0 the disabled dissapears)
           *-network DISABLED
                description: Wireless interface
                product: Cisco Aironet Wireless 802.11b
                vendor: AIRONET Wireless Communications
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 00
                serial: 00:02:8a:ed:02:be
                width: 32 bits
                clock: 33MHz
                capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
                configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
                resources: irq:11 ioport:8000(size=256) memory:c0200000-c0203fff memory:c0400000-c07fffff memory:c0800000-c09fffff


lsmod
	airo 77500 0


lspci -nn
	02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]


modprobe -l
	kernel/drivers/net/wireless/airo.ko
	kernel/drivers/net/wireless/airo_cs.ko


/proc/driver/aironet/eth0/Status
	Status: CFG ACT PRIV KEY 
	Mode: 18f
	Signal Strength: 0
	Signal Quality: 176
	SSID: 
	AP: 
	Freq: 0
	BitRate: 11mbs
	Driver Version: airo.c 0.6 (Ben Reed & Javier Achirica)
	Device: 350 Series
	Manufacturer: Cisco Systems
	Firmware Version: 5.41
	Radio type: 2
	Country: 0
	Hardware Version: 28
	Software Version: 541
	Software Subversion: 0
	Boot block version: 159


uname -mr
	3.0.0-12-generic i686

dmesg
	[    8.823533] airo(): Probing for PCI adapters
	[    8.823603] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
	[    8.823630] airo(): Found an MPI350 card

	[    9.772346] airo(eth0): Firmware version 5.41.00
	[    9.772350] airo(eth0): WPA supported.
	[    9.772354] airo(eth0): MAC enabled "my MAC adress"

	[    9.773564] airo(): Finished probing for PCI adapters

```

---

### Post by steeldriver on 2012-05-03
Hmm... well right now I'm on an X30 running  11.10 Xubuntu, but I long since abandoned that internal Aironet in favor of a cheap Cardbus card, since afaik there's no driver that gives you anything better than WEP, and it's only 802.11b anyway

I believe I *did* get it working at one point - if you don't get any help here then PM me and I will see if I can dig out my notes

FWIW your X31 *may* accept one of the Intel 2200bg cards, which may be better supported and at least allow WPA (my X30 doesn't - or at least doesn't boot if it detects it at post time, it actually *works* fine - there's a BIOS whitelist based on the PCI ID)

---

### Post by bm2598 on 2012-08-17
I have a similar looking problem trying to run either Lubuntu 12.4 or Linux Mint Maya (both  derived from Ubuntu 12.4) on my X30 with the same Cisco Aironet card. Ubuntu 10.4 LTS works out of the box incidentally .

I can get round it by stopping Network Manager, disabling wpa_supplicant and obtaining an IP address manually.

$ sudo stop network-manager

$ sudo ps aux | grep wpa
root      1454  0.1  0.3   5940  1656 ?        Ss   22:51   0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant

$ sudo kill -15 1454
$ sudo dhclient -v eth1

If I can get Network Manager to work I'll post again.

---

### Post by kenton_r on 2012-08-21
I have the same problem with my thinkpad t40. I tried stopping the NM and wpasupplicant, but I had another instance of the wpasupplicant running not as root but my account. This process was always changing its pid. And I could not get dhclient to connect. Any thoughts?

---

