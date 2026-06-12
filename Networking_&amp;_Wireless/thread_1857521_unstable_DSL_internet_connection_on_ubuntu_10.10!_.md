---
title: "unstable DSL internet connection on ubuntu 10.10! plz help!"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by kaparthy on 2011-10-10
Okay, i've been having this problem for a while with ubuntu 10.10 as well as xubuntu 11.04. after a startup, the dsl connection is okay and working fine but after an hour or so, it simply disconnects and tries to reconnect but turns out unsuccessful. 
after this one hour, i will not be able to connect to the internet unless i restart the system (toshiba satellite l-30)!. this is the ONLY but a major problem i have with ubuntu as well as xubuntu that i cannot come over even with a fresh reinstall of the system. Plz enlighten me! I will provide you with all the info that u need if u can help me! :)

new discovery:- it stops working even when the laptop is idle for a few minutes! (i have to restart it again to make it work)

---

### Post by kaparthy on 2011-10-10
no one? are you serious?????

---

### Post by papibe on 2011-10-10
Hi kaparthy,

Are you using a wired or wireless connection?
Do you have a router or just a modem?

Could you post the result of these commands?
```
$ sudo lshw -C network

$ lspci -nn | grep -i eth

$ lsmod

$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Please paste your result using the # tagss (available when replying).

Regards.

---

### Post by kaparthy on 2011-10-11
Thnx Papibe!, I am using a wired Cisco DPQ2160 modem connection and i dont have a router. and here are the results u need,

**1)****sudo lshw -C network** (it took a few seconds before completely displaying the result)
 result:
```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:5f:c7:f0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:a000(size=256) memory:d0210000-d02100ff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wlan0
       version: 01
       serial: 00:16:e3:56:2d:a3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:d0200000-d020ffff

```

**2)lspci -nn | grep -i eth**
result:
```
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
09:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
```

**3)lsmod**
result:
```
Module                  Size  Used by
xt_TCPMSS               2815  1 
xt_tcpmss               1177  1 
xt_tcpudp               1927  1 
iptable_mangle          1371  1 
ip_tables              10460  1 iptable_mangle
x_tables               15921  5 xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_mangle,ip_tables
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
arc4                    1165  2 
pppoe                   9015  2 
pppox                   2054  1 pppoe
snd_hda_codec_realtek   217980  1 
joydev                  8735  0 
snd_hda_intel          22107  2 
radeon                825934  3 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
ath5k                 130051  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  0 
mac80211              231541  1 ath5k
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath                     8153  1 ath5k
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  6 radeon,ttm,drm_kms_helper
cfg80211              144470  3 ath5k,mac80211,ath
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ati_agp                 5202  0 
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
led_class               2633  1 ath5k
i2c_algo_bit            5168  1 radeon
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
shpchp                 29886  0 
i2c_piix4               8635  0 
agpgart                32011  3 ttm,drm,ati_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
8139too                19581  0 
8139cp                 16934  0 
hid                    67742  1 usbhid
mii                     4425  2 8139too,8139cp
sata_sil                7035  1 
pata_atiixp             3288  0 

```

**4)ifconfig**
result:
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:5f:c7:f0  
          inet6 addr: fe80::216:36ff:fe5f:c7f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:388140 (388.1 KB)  TX bytes:43460 (43.4 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:123.201.236.182  P-t-P:123.201.236.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:234566 (234.5 KB)  TX bytes:31207 (31.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:e3:56:2d:a3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
[B]
5)route -n[/B]
result:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
123.201.236.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         123.201.236.1   0.0.0.0         UG    0      0        0 ppp0
```

**6)nslookup ubuntu.com**
result:
```
Server:		203.109.88.226
Address:	203.109.88.226#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156

```

**7)dig ubuntu.com**
result:
```
; <<>> DiG 9.7.1-P2 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22795
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ubuntu.com.			IN	A

;; ANSWER SECTION:
ubuntu.com.		542	IN	A	91.189.94.156

;; AUTHORITY SECTION:
ubuntu.com.		94351	IN	NS	ns2.canonical.com.
ubuntu.com.		94351	IN	NS	ns3.canonical.com.
ubuntu.com.		94351	IN	NS	ns1.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.	88476	IN	A	91.189.94.173
ns2.canonical.com.	88476	IN	A	91.189.94.219
ns3.canonical.com.	88476	IN	A	209.6.3.210

;; Query time: 16 msec
;; SERVER: 203.109.88.226#53(203.109.88.226)
;; WHEN: Tue Oct 11 11:41:10 2011
;; MSG SIZE  rcvd: 156

```

thnx again!

---

### Post by kaparthy on 2011-10-11
Additional information: the network manager icon on top panel does not show "dsl connection 1" or any other network connections once disconnected. after restarting the system, when i go to the edit connections --> dsl, it tells me that "dsl connection 1" (my default one) has NEVER been used! i think it'll tell me that it was used x minutes ago even when the computer is restarted ryt? maybe some  network related stuff is resetting on its own when the computer is on for an hour or so? what do u say guys?

---

### Post by papibe on 2011-10-11
It looks like you have your IP, routes, and DNS.

Could you post your /etc/network/interfaces ?
Also could you post the result of this command?
```
$ sudo dmesg | grep -i ppp
```
Regards.

---

### Post by kaparthy on 2011-10-11
i did **cat /etc/network/interfaces** and here's the result:

auto lo
iface lo inet loopback

and for the second code: **sudo dmesg | grep -i ppp** :

[    0.964926] PPP generic driver version 2.4.2

sorry man, i had to "quick reply" and didnt get them in code form.
thnx!
        and, when i try to reestablish the connection by setting up by using "sudo pppoeconf", it searches for "pppoe concentrators" for the two network devices but fails.

---

### Post by papibe on 2011-10-11
I was unable to get enough information to guide you how to configure your DSL connection using Network Manager (the GUI application). However I found this [guide]("https://help.ubuntu.com/community/ADSLPPPoE"). It involves uninstalling the network-manager package, and configure your connection by editing the necessary files.

I hope it helps, I'm not very familiar with that kind of connection. Let's hope that someone els pitch in.

Regards.

---

