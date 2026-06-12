---
title: "Network-manager automatically disabling Wired Connections"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by Sharang.d on 2013-07-08
OS: Ubuntu 12.04 64-bit

As the title suggests I'm having problems with the network-manager.

First a little bit of info:
I have an ADSL modem(in which you cannot save the ID/pass which is why a dialer/DSL connection has to be made) with it's output connected to a computer.
Also, the modem is ISP/factory locked wherein there are no "settings" on the config page but just information. 

Now,
I have made two connections in Network Manager: 
1 Wired (eth0) [With IP, Netmask and default gateway] and another under the DSL tab which has my id, password.
DSL connection is set to connect automatically.

When I swtich on my PC the connection is made automatically without my intervention. 
After inactivity(or sometimes even while I'm working on the PC) my wired network goes down.
I don't see the wired connections under nm-applet any more!
Screenshot of this:
[ATTACH=CONFIG]244504[/ATTACH]

Then i have to manually enter 
sudo service network-manager restart
which generally solves my problem.


Screenshot during normal operation:
[ATTACH=CONFIG]244505[/ATTACH]


When connected:
==========
lspci -nnk | grep -iA2 net
```
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:850d]
    Kernel driver in use: ath9k

```

lsmod
```

Module                  Size  Used by
pppoe                  17876  2 
pppox                  13343  1 pppoe
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
parport_pc             32867  0 
ppdev                  17114  0 
vesafb                 13846  1 
snd_hda_codec_hdmi     32476  1 
arc4                   12530  2 
ath9k                 133095  0 
mac80211              555272  1 ath9k
snd_hda_codec_realtek    79855  1 
fglrx                4715455  190 
ath9k_common           14054  1 ath9k
coretemp               13642  0 
ath9k_hw              399752  2 ath9k,ath9k_common
snd_hda_intel          34063  5 
kvm                   422160  0 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mei                    41410  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
psmouse               102506  0 
eeepc_wmi              13110  0 
ghash_clmulni_intel    13221  0 
serio_raw              13216  0 
amd_iommu_v2           19228  1 fglrx
asus_wmi               24457  1 eeepc_wmi
aesni_intel            51134  0 
sparse_keymap          13891  1 asus_wmi
mxm_wmi                13022  0 
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
joydev                 17694  0 
mac_hid                13254  0 
lp                     17800  0 
wmi                    19257  2 asus_wmi,mxm_wmi
lpc_ich                17145  0 
video                  19653  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
aes_x86_64             17256  1 aesni_intel
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
cfg80211              208382  3 ath9k,mac80211,ath
parport                46563  3 parport_pc,ppdev,lp
microcode              23030  0 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
ahci                   25869  4 
libahci                27338  1 ahci
e1000e                198734  0 

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 10:bf:48:7c:d0:8d  
          inet6 addr: fe80::12bf:48ff:fe7c:d08d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2946221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2914176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:888570423 (888.5 MB)  TX bytes:1731709068 (1.7 GB)
          Interrupt:20 Memory:f7f00000-f7f20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2128411 (2.1 MB)  TX bytes:2128411 (2.1 MB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:175.100.137.8  P-t-P:10.12.13.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:514379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:313885829 (313.8 MB)  TX bytes:69324771 (69.3 MB)


wlan0     Link encap:Ethernet  HWaddr 94:db:c9:4b:57:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1036 (1.0 KB)  TX bytes:11094 (11.0 KB)

```


sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 10:bf:48:7c:d0:8d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:f7f00000-f7f1ffff memory:f7f39000-f7f39fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 94:db:c9:4b:57:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-36-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff

```

WHEN DISCONNECTED AUTOMATICALLY
======

lspci -nnk | grep -iA2 net

```

00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:850d]
    Kernel driver in use: ath9k

```

lsmod
```
Module                  Size  Used by
pppoe                  17876  0 
pppox                  13343  1 pppoe
bnep                   18240  2 
rfcomm                 47562  0 
bluetooth             211812  10 bnep,rfcomm
parport_pc             32867  0 
ppdev                  17114  0 
vesafb                 13846  1 
snd_hda_codec_hdmi     32476  1 
coretemp               13642  0 
arc4                   12530  2 
ath9k                 133095  0 
mac80211              555272  1 ath9k
kvm                   422160  0 
ath9k_common           14054  1 ath9k
ghash_clmulni_intel    13221  0 
ath9k_hw              399752  2 ath9k,ath9k_common
snd_hda_codec_realtek    79855  1 
aesni_intel            51134  0 
fglrx                4715455  160 
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
cfg80211              208382  3 ath9k,mac80211,ath
eeepc_wmi              13110  0 
aes_x86_64             17256  1 aesni_intel
asus_wmi               24457  1 eeepc_wmi
mxm_wmi                13022  0 
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
sparse_keymap          13891  1 asus_wmi
wmi                    19257  2 asus_wmi,mxm_wmi
lpc_ich                17145  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse               102506  0 
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     17800  0 
mei                    41410  0 
amd_iommu_v2           19228  1 fglrx
soundcore              15092  1 snd
serio_raw              13216  0 
joydev                 17694  0 
video                  19653  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
microcode              23030  0 
mac_hid                13254  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
ahci                   25869  4 
libahci                27338  1 ahci
e1000e                198734  0 

```

ifconfig
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:828929 (828.9 KB)  TX bytes:828929 (828.9 KB)


wlan0     Link encap:Ethernet  HWaddr 94:db:c9:4b:57:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

sudo lshw -C network
```
  *-network DISABLED      
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 10:bf:48:7c:d0:8d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:f7f00000-f7f1ffff memory:f7f39000-f7f39fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 94:db:c9:4b:57:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-36-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff

```

I would like to have an always-on connection from the time I swtich on my PC to the time i switch it off(whenever).
I don't want to use any commands to connect/disconnect.. I don't want to use pppoeconf (I already did and it wasn't satisfying)
What I want is to have network-manager and any other config files managing the process automatically.
I will be happy to show you the output of any other commands.
Waiting for the replies!

---

### Post by praseodym on 2013-07-08
Please check:
```

cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by Sharang.d on 2013-07-08
> **praseodym said:**
> Please check:
```

cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
cat /etc/resolv.conf
```

cat /var/lib/NetworkManager/NetworkManager.state
```


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```
cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false

```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

```

---

### Post by praseodym on 2013-07-08
Change "false" to "true" in the .conf file and add the line
[B]
auto eth0[/B]
to the "interfaces". Reboot

---

### Post by Sharang.d on 2013-07-08
^Okay done. Will report back if network-manager goes bad again.

---

### Post by Sharang.d on 2013-07-08
After the changes my DSL connection doesn't connect automatically at startup!
I have to restart service network-manager and manually connect to the DSL connection.

---

### Post by praseodym on 2013-07-08
Then remove "auto eth0" again.

---

### Post by Sharang.d on 2013-07-08
> **praseodym said:**
> Then remove "auto eth0" again.
Sorry that was a problem from my ISP's side.
I have kept the settings you mentioned and I will let you know if I face the problem again.

---

### Post by Sharang.d on 2013-07-08
Yeah I'm still having problems. Just happened again(Lost all conenctions on eth0 as shown in screenshot 1). Had to restart service network-manager and got connected to the DSL immediately

---

### Post by praseodym on 2013-07-08
Did you tick "connect automatically" and "available to all users"?

---

### Post by Sharang.d on 2013-07-09
Yes, I have "Available to all users" ticked in both the DSL and Wired connections 
whereas "Connect Automatically" ticked in only the DSL connection.

I think something bigger is going on here though. Since the wired connections just disappear from nm-applet. Is there some kind of log that i can paste?

---

### Post by rpa.adak on 2013-07-09
I have a Tosiba Dual core satalite C850 laptop free Dos. I am trying to install ubuntu 12.04 LTS 32 bit on it. Everything are ok, but the network manager is not operating. When I connect it to a LAN, I donot get any connection information, ifconfig gives 
   lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:512 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:512 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:41552 (41.5 KB)  TX bytes:41552 (41.5 KB)  
 
   
sudo service network-manager restart   this gives :


   
network-manager stop/waiting  
 network-manager start/running, process 2652  
 debarati@debarati-Satellite-C850:~$  
 also wifi is not connected.
Any answer or suggestions ? Thanks in advanced

---

### Post by Sharang.d on 2013-07-09
> **rpa.adak said:**
> I have a Tosiba Dual core satalite C850 laptop free Dos. I am trying to install ubuntu 12.04 LTS 32 bit on it. Everything are ok, but the network manager is not operating. When I connect it to a LAN, I donot get any connection information, ifconfig gives 
   lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:512 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:512 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:41552 (41.5 KB)  TX bytes:41552 (41.5 KB)  
 
   
sudo service network-manager restart   this gives :


   
network-manager stop/waiting  
 network-manager start/running, process 2652  
 debarati@debarati-Satellite-C850:~$  
 also wifi is not connected.
Any answer or suggestions ? Thanks in advanced
You could get better help if you start a thread of your own :)
Our problems are not exactly same.

---

### Post by Sharang.d on 2013-07-10
Bought a new router.
Will still keep an eye out for network-manager messing up though.

If it does I'm gonna uninstall it and just use /etc/network/interfaces :)

---

### Post by Sharang.d on 2013-07-14
UPDATE: It didn't happen again. I guess it messes up when there's a DSL connection. Idk.

Thread can be closed.
{..but note that the problem isn't solved}

---

### Post by amith2 on 2013-08-06
i am having the same problem and tried doing the modification to conf.file and the interfaces.

Can you please suggest me how to resolve it

---

### Post by praseodym on 2013-08-06
Hi,

please show these terminal outputs:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
```

---

