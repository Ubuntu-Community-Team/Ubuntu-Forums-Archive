---
title: "Broadcom BCM57785"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by ksjenka on 2013-08-02
I'm new to linux, so don't be really hard on me. I bought a new laptop - Acer Aspire v3-571g intel-corei3-3110M. I tried to install different linux distros: pear os, elementary os luna and ubuntu finally. In all cases it says "Connected" to my wired internet, but actually the internet isn't working. I really don't know what to. On my old Acer laptop installed Ubuntu and the internet works like a charm. Maybe I have to install ethernet drivers? Please, help me.
I set up outputs that I saw in other threads is most requested for help, but I'm not sure what those commands mean:

```

ifconfig
eth0      Link encap:Ethernet  HWaddr b8:88:e3:a3:f6:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18634 (18.6 KB)  TX bytes:18634 (18.6 KB)


wlan0     Link encap:Ethernet  HWaddr 68:94:23:1e:e2:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


sudo lshw -C network
[sudo] password for ksenia: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:88:e3:a3:f6:25
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:b3450000-b34507ff
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 68:94:23:1e:e2:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:b3500000-b357ffff memory:9fc00000-9fc0ffff




sudo lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)


lspci -nn | grep 0200
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)









```

Thanks to all who are helping people here:)

---

### Post by praseodym on 2013-08-03
Hi,

is the driver loaded?
```

lsmod
```
please also check:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```
Is wireless working? If yes, install this package and show additionally:
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by ksjenka on 2013-08-03
OK, that's the info I got:

```

lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
acer_wmi               32467  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
uvcvideo               80847  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
snd_timer              29425  2 snd_pcm,snd_seq
videodev              129260  2 uvcvideo,videobuf2_core
nouveau               939088  0 
arc4                   12615  2 
mac_hid                13205  0 
i915                  600351  3 
microcode              22881  0 
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mxm_wmi                13021  1 nouveau
ttm                    83187  1 nouveau
mac80211              606457  1 ath9k
wmi                    19070  3 acer_wmi,mxm_wmi,nouveau
video                  19390  3 i915,acer_wmi,nouveau
drm_kms_helper         49394  2 i915,nouveau
drm                   286313  6 ttm,i915,drm_kms_helper,nouveau
cfg80211              510937  3 ath,ath9k,mac80211
psmouse                95870  0 
serio_raw              13215  0 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           13413  2 i915,nouveau
mei                    41158  0 
soundcore              12680  1 snd
lpc_ich                17061  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
tg3                   153796  0 
ahci                   25731  4 
libahci                31364  1 ahci
ptp                    18621  1 tg3
pps_core               14080  1 ptp




cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.31.253   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.16.16.0     0.0.0.0         255.255.240.0   U     1      0        0 eth0




sudo apt-get install ethtool
[sudo] password for ksenia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ethtool is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'ethtool' has no installation candidate



```

I don't have a wireless connection, I only can see the users in list that are connected to wi-fi network. But to be sure I did the last command.

---

### Post by praseodym on 2013-08-03
Which Ubuntu version is it? Please show
```

uname -a
lsb_release -a
```

---

### Post by ksjenka on 2013-08-03
Here:

```

uname -a
Linux ksenia-Aspire-V3-571G 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


ksenia@ksenia-Aspire-V3-571G:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring



```

---

### Post by praseodym on 2013-08-03
Download this package to "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.4.2-1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.4.2-1_amd64.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
sudo ethtool eth0
```

---

### Post by ksjenka on 2013-08-03
I assume I had to connect my cable to the new laptop in order to check the last command, which I did (sorry I'm saying those stupid things):

```

 sudo ethtool eth0
[sudo] password for ksenia: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: yes



```

---

### Post by ksjenka on 2013-08-03
For additional information: I'm currently typing all of my posts on my old laptop, where this wired connection is working; I'm also downloading from there, then I'm putting info on my flash usb; and also all of the output from my new laptop I put on this flash drive in .txt,  go back to this old laptop in order to write here.

---

### Post by praseodym on 2013-08-03
Try to deactivate the auto-negotiation of the card:
```

sudo ethtool -s eth0 speed 100 autoneg off
```

---

### Post by ksjenka on 2013-08-03
Nope, nothing's changed:(

---

### Post by praseodym on 2013-08-03
```
nameserver 127.0.1.1
```
This should read:```

nameserver 127.0.0.1
``````

gksudo gedit /etc/resolv.conf
```
Change the file, save, close the editor and restart the network (or reboot):
```

sudo /etc/init.d/networking restart
```

---

### Post by ksjenka on 2013-08-03
It says:

```

gksudo gedit /etc/resolv.conf
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu

```
I tried to use sudo:

```

ksenia@ksenia-Aspire-V3-571G:~$ sudo gedit /etc/resolv.conf
[sudo] password for ksenia: 


(gedit:2518): IBUS-WARNING **: The owner of /home/ksenia/.config/ibus/bus is not root!

```

But after I changed the file, reboot and opened it again it's still:

```


[COLOR=#000000][FONT=Ubuntu Mono]nameserver 127.0.1.1[/FONT][/COLOR]

```

and of course the internet doesn't work still...
How do I install **gksudo**?

---

### Post by ksjenka on 2013-08-03
Even though I downloaded the .deb package of gksu([http://packages.ubuntu.com/raring/amd64/gksu/download](http://packages.ubuntu.com/raring/amd64/gksu/download)), installed and I had also to download and install this - [http://packages.ubuntu.com/raring/amd64/libgksu2-0/download](http://packages.ubuntu.com/raring/amd64/libgksu2-0/download), because there was a message in terminal about this lib - I didn't get the positive result - I changed the resolv.conf file, rebooted and again nothing - and the changes in that file didn't take place - it is:

[COLOR=#000000][FONT=Ubuntu Mono]nameserver 127.0.1.1
[/FONT][/COLOR]
instead of: [B]nameserver 127.0.0.1
[/B]
**@praseodym**, please help me

---

### Post by praseodym on 2013-08-03
Uninstall this one:
```

sudo apt-get remove --purge resolvconf
```
and reboot. If there is nothing inside afterwards, then:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
```

---

### Post by ksjenka on 2013-08-03
After I executed first command - I couldn't reboot normally, it froze, so I pushed the power off button to force its turning off. When I was booting there was a message (I didn't quite remembered all numbers) somewhat like this : 
```


[8.833423] usb 1-1.1  script descritor 0 read error [-22]
unable to detect USB 1 port


```

When I did this:
```


sudo gedit /etc/resolv.conf


```

it took to that file, where was this:

```


# Generated by NetworkManager
nameserver 127.0.1.1



```

So, do I need to execute your last commands?

---

### Post by chili555 on 2013-08-03
I would love to see:```
dmesg | grep -e tg3 -e eth0 > ksj.txt
```Find the file ksj.txt in your user directory and transfer and post it as before.

---

### Post by ksjenka on 2013-08-03
Sorry for my stupidity: I executed the command and nothing's happened:

```


ksenia@ksenia-Aspire-V3-571G:~$ dmesg | grep -e tg3 -e eth0 > ksj.txt
ksenia@ksenia-Aspire-V3-571G:~$ 




```

Then in **home** directory I found ksj.txt file (the cable to internet was plugged in to my new laptop):

```

[    1.269249] tg3.c:v3.128 (December 03, 2012)
[    1.296018] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM57785) rev 57785100] (PCI Express) MAC address b8:88:e3:a3:f6:25
[    1.296023] tg3 0000:02:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    1.296026] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.296029] tg3 0000:02:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    8.126735] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.199686] tg3 0000:02:00.0: irq 46 for MSI/MSI-X
[   11.199692] tg3 0000:02:00.0: irq 47 for MSI/MSI-X
[   11.199695] tg3 0000:02:00.0: irq 48 for MSI/MSI-X
[   11.199698] tg3 0000:02:00.0: irq 49 for MSI/MSI-X
[   11.199701] tg3 0000:02:00.0: irq 50 for MSI/MSI-X
[   11.389997] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.390288] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.147946] tg3 0000:02:00.0 eth0: Link is up at 100 Mbps, full duplex
[   13.147951] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
[   13.147954] tg3 0000:02:00.0 eth0: EEE is disabled
[   13.147972] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  128.772020] tg3 0000:02:00.0 eth0: Link is down
[  132.822240] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3021.199871] tg3 0000:02:00.0 eth0: Link is up at 100 Mbps, full duplex
[ 3021.199877] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
[ 3021.199881] tg3 0000:02:00.0 eth0: EEE is disabled
[ 3021.199901] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


```

Hope it'll help to help me, lol:)

---

### Post by ksjenka on 2013-08-03
I read this article - [http://havingnoclue.wordpress.com/2012/03/25/lan-working-on-acer-aspire-5750-6872-laptop-with-ubuntu-10-04/](http://havingnoclue.wordpress.com/2012/03/25/lan-working-on-acer-aspire-5750-6872-laptop-with-ubuntu-10-04/)
and tried to install the driver, but there was issues:
[COLOR=#141414][FONT=Georgia]1. In HOME I created "Ethernet" directory where I extracted linux-3.129d.zip[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]2. I extracted tg3-3.129d.tar.gz in Ethernet/Sever/Linux/Driver folder and there appeared "tg3-3.129d" folder[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]3. Opened a terminal and did the following:
[/FONT][/COLOR]
```

ksenia@ksenia-Aspire-V3-571G:~$ cd Ethernet/Server/Linux/Driver/
ksenia@ksenia-Aspire-V3-571G:~/Ethernet/Server/Linux/Driver$ cd tg3-3.129d
ksenia@ksenia-Aspire-V3-571G:~/Ethernet/Server/Linux/Driver/tg3-3.129d$ make
sh makeflags.sh /lib/modules/3.8.0-19-generic/build  > tg3_flags.h
make -C /lib/modules/3.8.0-19-generic/build SUBDIRS=/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.o
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:288:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__devinitdata’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:11377:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_timer_init’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:14766:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_eeprom_size’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:14800:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_nvram_size’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:14833:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:14884:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_nvram_get_pagesize’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:14911:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_5752_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:14952:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_5755_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15008:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_5787_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15046:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_5761_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15121:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_5906_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15128:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_57780_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15201:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_5717_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15279:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_5720_nvram_info’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15421:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_nvram_init’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15492:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__devinitdata’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15556:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_lookup_by_subsys’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15570:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_eeprom_hw_cfg’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15783:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_ape_otp_read’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15816:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_issue_otp_command’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15839:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_otp_phycfg’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15865:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_phy_init_link_config’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:15892:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_phy_probe’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16011:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_vpd’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16132:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_fw_img_is_valid’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16145:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_bc_ver’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16197:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_hwsb_ver’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16213:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_sb_ver’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16268:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_mgmtfw_ver’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16320:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_probe_ncsi’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16336:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_dash_ver’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16361:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_otp_ver’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16386:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_read_fw_ver’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16442:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_find_peer’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16470:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_detect_asic_rev’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16579:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_invariants’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:17436:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_get_device_address’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:17517:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_calc_dma_bndry’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:17658:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_do_test_dma’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:17747:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_test_dma’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:17943:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_init_bufmgr_config’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:17999:25: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_phy_string’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:18038:25: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_bus_string’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:18074:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_init_coal’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:18105:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_init_one’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:18625:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tg3_remove_one’
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:18939:12: error: ‘tg3_init_one’ undeclared here (not in a function)
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:18940:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:18940:25: error: ‘tg3_remove_one’ undeclared here (not in a function)
In file included from /home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.h:13:0,
                 from /home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:118:
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3_compat.h:969:14: warning: ‘print_mac’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:548:12: warning: ‘tg3_read32’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:579:12: warning: ‘tg3_read_indirect_reg32’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:621:12: warning: ‘tg3_read_indirect_mbox’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:674:12: warning: ‘tg3_read32_mbox_5906’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:679:13: warning: ‘tg3_write32_mbox_5906’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:747:13: warning: ‘tg3_ape_lock_init’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:1623:12: warning: ‘tg3_mdio_init’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:1739:13: warning: ‘tg3_mdio_fini’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:11246:13: warning: ‘tg3_timer’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:11436:13: warning: ‘tg3_reset_task’ defined but not used [-Wunused-function]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:14524:27: warning: ‘tg3_ethtool_ops’ defined but not used [-Wunused-variable]
/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.c:16558:13: warning: ‘tg3_10_100_only_device’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[2]: *** [/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d/tg3.o] Error 1
make[1]: *** [_module_/home/ksenia/Ethernet/Server/Linux/Driver/tg3-3.129d] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [default] Error 2




```
I didn't execute commands: 
```

insmod tg3.ko

```
and
```

make install

```
because of those errors above.
What did I do wrong?? I don't know how to install it, the README.TXT file instructions apparently aren't enough for me, I'm a total noob.:(

---

### Post by chili555 on 2013-08-04
> **ksjenka said:**
> 
because of those errors above.
What did I do wrong?? I don't know how to install it, the README.TXT file instructions apparently aren't enough for me, I'm a total noob.:(The article was written for Ubuntu 10.04. The package was written for kernel 2.6.xx. You have Ubuntu 13.04 and kernel 3.8. The package has too many dis-similarities from your sleek modern kernel. 

Let's try to dig even deeper. Please hook up the ethernet cable. Shut down completely (not reboot). Start the computer and let it try to connect. After a few minutes, run and post:```
cat /var/log/syslog | grep -e tg3 -e etwork -e eth0 > ksj2.txt
```The file is likely to be quite long so paste it here and give us the link: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by ksjenka on 2013-08-04
OK, I did it, the file is here - [http://paste.ubuntu.com/5947511/](http://paste.ubuntu.com/5947511/)

---

### Post by chili555 on 2013-08-04
>  Joining mDNS multicast group on interface eth0.IPv4 with address 172.16.26.226.
Aug  4 19:12:58 ksenia-Aspire-V3-571G avahi-daemon[766]: New relevant interface eth0.IPv4 for mDNS.
Aug  4 19:12:58 ksenia-Aspire-V3-571G avahi-daemon[766]: Registering new address record for 172.16.26.226 on eth0.IPv4.So it connected just fine??```
ping -c3 8.8.8.8
ifconfig
```It looks like you have a dnsmasq issue, but, nonetheless, eth0 connects! Yes? No?

--------

More information: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1048430](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1048430)

> Peter: the issue here is that this "error" is expected: on the very first update after boot, dnsmasq will get spawned during the update phase, but is likely not going to be ready yet -- the update will "fail" and fallback to writing the dns names directly to resolv.conf, instead of writing 127.0.1.1 and using dnsmasq. Then when dnsmasq appears on the bus the update is re-tried, and should succeed.

---

### Post by ksjenka on 2013-08-04
Yes it connects immediately after I hook up the cable: message "Connected" appears, but browsers won't work and Software Center too - it says "Server not found" - that's the whole deal  - the internet connection exists but there is no actual internet in the same time. I can't figure what's the problem.

---

### Post by praseodym on 2013-08-04
Check now:
```

cat /etc/resolv.conf
route -n
ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.11 
```

---

### Post by ksjenka on 2013-08-04
This is what I got:

```


 cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.1.1
ksenia@ksenia-Aspire-V3-571G:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.31.253   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.16.16.0     0.0.0.0         255.255.240.0   U     1      0        0 eth0
ksenia@ksenia-Aspire-V3-571G:~$ ping -c 2 $(route -n | grep UG | awk {'print $2'})
PING 172.16.31.253 (172.16.31.253) 56(84) bytes of data.


--- 172.16.31.253 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1007ms


ksenia@ksenia-Aspire-V3-571G:~$ ping -c 2 www.ubuntuusers.de
ping: unknown host www.ubuntuusers.de
ksenia@ksenia-Aspire-V3-571G:~$ ping -c 2 213.95.41.11
PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.


--- 213.95.41.11 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms



```

---

### Post by praseodym on 2013-08-04
Go to the network-manager profile and change "Automatic (DHCP)" to "Automatic (DHCP), addresses only" and add
```

8.8.8.8, 8.8.4.4
```
in the DNS field. restart your network
```

sudo service network-manager restart
```

---

### Post by ksjenka on 2013-08-04
I did all of the above - the message is "Disconnected". Though, maybe I should point out that it wasn't "[COLOR=#000000]Automatic (DHCP)[/COLOR]" it was "Manual", because I manually added all the ip, gateway,dns - see the screenshot - [http://imgur.com/c1CO4Ka](http://imgur.com/c1CO4Ka)

---

### Post by ksjenka on 2013-08-04
Please, take a look at this output, maybe it'll help:

```


[COLOR=#000000][FONT=dejavu sans mono]lshw -C network ; ip a ; tracepath ya.ru[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]WARNING: you should run this program as super-user.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  *-network               [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       product: NetLink BCM57785 Gigabit Ethernet PCIe[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       vendor: Broadcom Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       bus info: pci@0000:02:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       logical name: eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       version: 10[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       serial: b8:88:e3:a3:f6:25[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       size: 100Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       capacity: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=sb ip=172.16.26.226 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:b3450000-b34507ff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  *-network[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       product: AR9462 Wireless Network Adapter[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       vendor: Atheros Communications Inc.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       logical name: wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       version: 01[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       serial: 68:94:23:1e:e2:51[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       capabilities: bus_master cap_list rom ethernet physical wireless[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       resources: irq:17 memory:b3500000-b357ffff memory:9fc00000-9fc0ffff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]WARNING: output may be incomplete or inaccurate, you should run this program as super-user.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet 127.0.0.1/8 scope host lo[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet6 ::1/128 scope host [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       valid_lft forever preferred_lft forever[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    link/ether b8:88:e3:a3:f6:25 brd ff:ff:ff:ff:ff:ff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet 172.16.26.226/20 brd 172.16.31.255 scope global eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet6 fe80::ba88:e3ff:fea3:f625/64 scope link [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       valid_lft forever preferred_lft forever[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    link/ether 68:94:23:1e:e2:51 brd ff:ff:ff:ff:ff:ff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]gethostbyname2: Resolver internal error[/FONT][/COLOR]



[COLOR=#000000][FONT=dejavu sans mono]ksenia@ksenia-Aspire-V3-571G:~$ sudo lshw -C network ; ip a ; tracepath ya.ru[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][sudo] password for ksenia: [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  *-network               [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       product: NetLink BCM57785 Gigabit Ethernet PCIe[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       vendor: Broadcom Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       bus info: pci@0000:02:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       logical name: eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       version: 10[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       serial: b8:88:e3:a3:f6:25[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       size: 100Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       capacity: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=sb ip=172.16.26.226 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:b3450000-b34507ff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  *-network[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       product: AR9462 Wireless Network Adapter[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       vendor: Atheros Communications Inc.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       logical name: wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       version: 01[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       serial: 68:94:23:1e:e2:51[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       resources: irq:17 memory:b3500000-b357ffff memory:9fc00000-9fc0ffff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet 127.0.0.1/8 scope host lo[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet6 ::1/128 scope host [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       valid_lft forever preferred_lft forever[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    link/ether b8:88:e3:a3:f6:25 brd ff:ff:ff:ff:ff:ff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet 172.16.26.226/20 brd 172.16.31.255 scope global eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    inet6 fe80::ba88:e3ff:fea3:f625/64 scope link [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]       valid_lft forever preferred_lft forever[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    link/ether 68:94:23:1e:e2:51 brd ff:ff:ff:ff:ff:ff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]gethostbyname2: Resolver internal error[/FONT][/COLOR]

```

---

### Post by ksjenka on 2013-08-04
I solved the problem, I just had to change my MAC-address on new laptop:)))))

---

### Post by ksjenka on 2013-08-04
I really wanna say thank you really much **@praseodym** and **@chili555**, you rock!:))))

---

### Post by chili555 on 2013-08-04
Glad it's working! Have fun!

---

