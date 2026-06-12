---
title: "Unable to locate wireless network - HP Pavilion"
date: 2012-09-23
forum: Networking &amp; Wireless
---

### Post by winstont11 on 2012-09-23
Hi there, I recently installed Ubuntu 12.04 on my laptop and my wireless network is not being detected. Enable wireless is grayed out. I'm providing some information below. Please let me know if additional information is required. I'd appreciate some help : )

melissa@melissa-Pavilion-dv5000-ET818UA-ABA:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
melissa@melissa-Pavilion-dv5000-ET818UA-ABA:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:fc:47:88  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fefc:4788/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7319250 (7.3 MB)  TX bytes:670754 (670.7 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69427 (69.4 KB)  TX bytes:69427 (69.4 KB)

melissa@melissa-Pavilion-dv5000-ET818UA-ABA:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
melissa@melissa-Pavilion-dv5000-ET818UA-ABA:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
snd_atiixp             19337  2 
snd_atiixp_modem       18604  0 
snd_ac97_codec        106082  2 snd_atiixp,snd_atiixp_modem
joydev                 17393  0 
ac97_bus               12642  1 snd_ac97_codec
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_pcm                80845  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25424  1 snd_seq_midi
b43                   342643  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  1 b43
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39791  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              12937  0 
psmouse                87213  0 
serio_raw              13027  0 
cfg80211              178679  2 b43,mac80211
snd                    62064  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core              15040  1 tifm_7xx1
rfcomm                 38139  0 
parport_pc             32114  0 
soundcore              14635  1 snd
k8temp                 12905  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
bcma                   25651  1 b43
bluetooth             158438  7 rfcomm
ppdev                  12849  0 
snd_page_alloc         14115  3 snd_atiixp,snd_atiixp_modem,snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_piix4              13093  0 
binfmt_misc            17292  1 
shpchp                 32325  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
radeon                733718  3 
firewire_ohci          40180  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
8139too                23283  0 
drm                   197692  5 radeon,ttm,drm_kms_helper
sdhci_pci              18324  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci                  28241  1 sdhci_pci
i2c_algo_bit           13199  1 radeon
8139cp                 22633  0 
ssb                    50691  1 b43
pata_atiixp            12999  2 
video                  19068  0 
wmi                    18744  1 hp_wmi
ati_agp                13242  0 

melissa@melissa-Pavilion-dv5000-ET818UA-ABA:~$ sudo lshw -C network
[sudo] password for melissa: 
  *-network:0             [D^[[D
       description: Network controller
       product: BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:fc:47:88
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.108 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:4e:fd:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-30-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by chili555 on 2012-09-24
I suspect your Broadcom needs some firmware but let's do some diagnostics first. Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by winstont11 on 2012-09-24
> **chili555 said:**
> I suspect your Broadcom needs some firmware but let's do some diagnostics first. Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

Thank you for responding! : )

melissa@melissa-Pavilion-dv5000-ET818UA-ABA:~$ lspci -nn | grep 0280
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)
melissa@melissa-Pavilion-dv5000-ET818UA-ABA:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes

---

### Post by chili555 on 2012-09-24
> Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [[COLOR="Red"]14e4:4319[/COLOR]]You indeed need firmware. Hook up the ethernet, get a connection and do:```
sudo apt-get install linux-firmware-nonfree
```You also need to flip the wireless switch from OFF to ON:```
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]
```After you move the switch, reboot and your wireless should be working.

---

### Post by winstont11 on 2012-09-24
> **chili555 said:**
> You indeed need firmware. Hook up the ethernet, get a connection and do:```
sudo apt-get install linux-firmware-nonfree
```You also need to flip the wireless switch from OFF to ON:```
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]
```After you move the switch, reboot and your wireless should be working.

You are fantastic!  Thank you for helping me out.  I'm all set : )

---

### Post by chili555 on 2012-09-25
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

