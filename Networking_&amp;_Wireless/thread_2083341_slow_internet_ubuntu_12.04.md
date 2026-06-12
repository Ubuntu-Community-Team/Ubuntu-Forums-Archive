---
title: "slow internet ubuntu 12.04"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by miro71 on 2012-11-12
Hi, previously was using windows and there wasn't any problems. Now on ubuntu my internet connection seems very slow, its hard to browse web and also downloading files not working properly. I decided to download and install all avaible updates trough the updater, but the connection is too slow.

_**Info:**_
ping
```
miroelo82@ubuntu:~$ ping google.com
PING google.com (74.125.136.139) 56(84) bytes of data.
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=1 ttl=42 time=49.9 ms
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=4 ttl=42 time=50.6 ms
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=8 ttl=42 time=50.2 ms
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=11 ttl=42 time=48.9 ms
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=14 ttl=42 time=50.1 ms
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=17 ttl=42 time=53.7 ms
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=20 ttl=42 time=50.3 ms
64 bytes from 74.125.136.139: icmp_req=24 ttl=42 time=49.5 ms
64 bytes from ea-in-f139.1e100.net (74.125.136.139): icmp_req=25 ttl=42 time=51.0 ms

```lshw -c network
```
miroelo82@ubuntu:~$ sudo lshw -c network
[sudo] password for miroelo82: 
SCSI                      
  *-network        
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 90:2b:34:97:1a:3b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.2.100 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:fdcc0000-fdcfffff ioport:df00(size=128)
```lspci -nnk | grep -ia2 net
```
miroelo82@ubuntu:~$ lspci -nnk | grep -ia2 net
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Giga-byte Technology Device [1458:e000]
    Kernel driver in use: atl1c
```lsmod
```
miroelo82@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  4 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_codec_realtek   224066  1 
nouveau               774641  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
serio_raw              13211  0 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
k10temp                13166  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
snd_seq_midi           13324  0 
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
mac_hid                13253  0 
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47199  0 
hid                    99559  1 usbhid
pata_atiixp            13204  0 
usb_storage            49198  1 
atl1c                  41718  0 
```Help :)
Edit:
ifconfig
```
miroelo82@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:2b:34:97:1a:3b  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe97:1a3b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1578 errors:0 dropped:0 overruns:0 carrier:3988
          collisions:0 txqueuelen:1000 
          RX bytes:1393645 (1.3 MB)  TX bytes:214544 (214.5 KB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20114 (20.1 KB)  TX bytes:20114 (20.1 KB)
```tracepath -b 8.8.8.8
```
miroelo82@ubuntu:~$ tracepath -b 8.8.8.8
 1:  ubuntu.local (192.168.2.100)                          0.201ms pmtu 1500
 1:  192.168.2.1 (192.168.2.1)                             0.753ms 
 2:  no reply
 3:  89-75-10-65.infra.chello.pl (89.75.10.65)            11.488ms 
 4:  84.116.192.2 (84.116.192.2)                          41.040ms asymm 19 
 5:  84.116.252.66 (84.116.252.66)                        40.093ms asymm 18 
 6:  84.116.253.97 (84.116.253.97)                        42.137ms asymm 17 
 7:  84.116.252.229 (84.116.252.229)                      40.964ms asymm 16 
 8:  84.116.252.242 (84.116.252.242)                      49.862ms asymm 15 
 9:  pl-waw04a-rd1-ae12-2158.aorta.net (84.116.252.225)   51.165ms asymm 14 
10:  84.116.137.9 (84.116.137.9)                          38.340ms 
11:  84.116.132.146 (84.116.132.146)                      40.802ms 
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 

```

---

### Post by varunendra on 2012-11-13
Hi miro71, Welcome to the forums !

My initial guess from your outputs is that perhaps it is a bad physical connection problem -
> **miro71 said:**
> ```
miroelo82@ubuntu:~$ sudo lshw -c network
..
..
       configuration: autonegotiation=on ...... latency=0 [COLOR=Red]**link=no**[/COLOR] multicast=yes 
```
ifconfig
```
miroelo82@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:2b:34:97:1a:3b  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          [COLOR=Navy]**inet6**[/COLOR] addr: fe80::922b:34ff:fe97:1a3b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1578 errors:0 dropped:0 overruns:0 [COLOR=Red]**carrier:3988**[/COLOR]
          collisions:0 txqueuelen:1000 
          RX bytes:1393645 (1.3 MB)  TX bytes:214544 (214.5 KB)
          Interrupt:42 
```Accordingly, please check your physical connection. Replace the cable with a tested healthy one if possible, then recheck ifconfig to see if the number of "carrier" is increasing again. Ideally it should be '0', but a small number is okay.

As an additional measure, set IPv6 "Method" to "Ignore" in Network Manager, and disable it permanently by adding the following to your /etc/sysctl.conf file -
> # disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1 			 		
You can easily do so by just copy-pasting the following command in a terminal -
```
echo -e "\n# disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```

Once done, do the following -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
Then check the connection.

If the problem persists, post the outputs of the following -
```
ifconfig
sudo lshw -C network
nm-tool
```

---

### Post by miro71 on 2012-11-13
somehow the problem fixed itself(for now), thank you for your reply

---

### Post by varunendra on 2012-11-13
> **miro71 said:**
> somehow the problem fixed itself(for now)
Hmm... indeed it smells like a burnt cable/connector to me ;)

Anyway, glad it got fixed anyhow. Feel free to post back if needed.

---

### Post by dandroid7 on 2012-12-09
First post... brand new to this forum... 

Having the same issue, did as stated above, still slow internet, here is the output from running the command in command prompt (I have no idea what this stuff means... I just don't understand why the little circle keeps spinning and spinning in a fire-fox tab after loading a basic webpage):


root@dubuntu-Inspiron-660:~# ifconfig
eth0      Link encap:Ethernet  HWaddr d4:be:d9:d7:8b:26  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34988651 (34.9 MB)  TX bytes:6707485 (6.7 MB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92465 (92.4 KB)  TX bytes:92465 (92.4 KB)

wlan0     Link encap:Ethernet  HWaddr e0:06:e6:73:fd:97  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:421181 (421.1 KB)  TX bytes:11525 (11.5 KB)

root@dubuntu-Inspiron-660:~# sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: e0:06:e6:73:fd:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-34-generic firmware=N/A ip=192.168.1.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: d4:be:d9:d7:8b:26
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.18 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

Any suggestion would be greatly appreciated... Internet speed works great on windows (this is a dual boot computer/ windows 8/ubuntu 12.04)

Thanks for your help.

---

