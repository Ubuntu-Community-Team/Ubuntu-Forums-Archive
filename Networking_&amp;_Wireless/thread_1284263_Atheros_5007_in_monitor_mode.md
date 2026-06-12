---
title: "Atheros 5007 in monitor mode"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by michelf on 2009-10-06
Hi guys,

I've been messing with my wireless configs since i upgraded to 9.04, somehow i've managed to get it working but now i can't get the wireless card in monitor mode, which i was able to do before the upgrade. I don't know where to look or what files should i delete to start from scrap, if you guys could point me in the right direction it would be great.

Here's some relevant info.

root@loki:/home/drak# lspci | grep Ath
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


root@loki:/home/drak# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


root@loki:/home/drak# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:0b:43:##:##  
          inet addr:10.80.##.##  Bcast:10.80.##.##  Mask:255.255.##.##
          inet6 addr: fe80::214:bff:####:####/## Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12919222 (12.9 MB)  TX bytes:529233 (529.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5272 (5.2 KB)  TX bytes:5272 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:##:##:##  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-C4-##-##-##-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
root@loki:/home/drak# dmesg | grep ath
[    3.220355] device-mapper: multipath: version 1.0.5 loaded
[    3.220358] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.561453] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.561469] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   12.561571] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   12.675524] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   12.676122] ath_hal: module license 'Proprietary' taints kernel.
[   12.677456] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   12.694797] ath_pci: 0.9.4
[ 2930.307585] ath5k phy0: unsupported jumbo

root@loki:/home/drak# airmon-ng 


Interface	Chipset		Driver

wlan0		Atheros 	ath5k - [phy0]

root@loki:/home/drak# airmon-ng check


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
2914	NetworkManager
2933	wpa_supplicant
2938	avahi-daemon
2939	avahi-daemon
3229	dhclient

Thanks in advance,

Michel

---

### Post by jessiebrownjr on 2009-10-06
hey hey, i have a 5008...


you would type airmon-ng start (nic name)
mine is wlan0

Once you type that, you can type iwconfig and bam, you see your new interface.


Got monitor working and want to inject now?
First off you need to "killall" NetworkManager and then wpa_supplicant.
they WILL CRASH YOU if you attempt to inject when you are using them... For monitor mode only , I don't think it matters... 

Note.. killall NetworkManager kills your internet connection, deal with it :-)

On a side note, might want to strip your real MAC/ips off that post, don't want ppl spoofing as you right? :-)

---

### Post by michelf on 2009-10-07
Worked fine! 

Tested with airodump-ng

Now i'll try to make kismet work...

---

### Post by MARAUDER2003 on 2009-10-11
Hi, i'm also trying to make kismet work. It seems i get the dhclient thing interfering with my collecting interface (in my case wlan0). I'm using ath5k. How do you go about killing this dhclient thing, I THINK i read somewhere i also have to turn off the wpa supplicant thing too. Just like jessiebrownjr said. Any help with this? I used the madwifi driver before with my 5007 and kismet and i don't remember killing any clients, do you know why? thanks. Alan

---

