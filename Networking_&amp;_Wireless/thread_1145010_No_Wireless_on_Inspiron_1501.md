---
title: "No Wireless on Inspiron 1501"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by justin23 on 2009-05-01
I have been using Ubuntu 9.4 64bit.  On the first install wireless worked just fine.  Had to uninstall and reinstall now wireless is not working.  Can someone help me with this?

**1 ) Machine Brand and Model (PC/Laptop)**

Dell inspiron 1501

**2 ) Wireless Brand, Model and Wireless Chipset:**

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

**3 ) check interface:**

justin@justin:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

pan0      no wireless extensions.

justin@justin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:6d:39:99  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe6d:3999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2684605 (2.6 MB)  TX bytes:163137 (163.1 KB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:b1:6c:24  
          inet6 addr: fe80::21a:92ff:feb1:6c24/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



**4 ) Check for modules:**

lsmod
Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
radeon                357792  2 
drm                   123232  3 radeon
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
joydev                 20864  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
dcdbas                 16944  0 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b44                    41616  0 
psmouse                64028  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
ssb                    46724  1 b44
serio_raw              14468  0 
pcspkr                 11136  0 
ricoh_mmc              12544  0 
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
i2c_piix4              20112  0 
k8temp                 13440  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
shpchp                 44572  0 
mii                    14464  1 b44
ieee80211_crypt_tkip    17920  0 
wl                   1496016  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
video                  29204  0 
output                 11648  1 video
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
[B]
5 ) Kernel boot messages[/B]

"/usr/sbin/tcpdump" name2="default" pid=1980
[   18.723258] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.723261] Bluetooth: BNEP filters: protocol multicast
[   18.758235] Bridge firewalling registered
[   20.735699] pci 0000:01:05.0: power state changed by ACPI to D0
[   20.735710] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.970356] [drm] Initialized drm 1.1.0 20060810
[   21.045545] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   21.184036] ppdev: user-space parallel port driver
[   21.502798] [drm] Setting GART location based on new memory map
[   21.503068] [drm] Loading R300 Microcode
[   21.503088] [drm] Num pipes: 4
[   21.503094] [drm] writeback test succeeded in 1 usecs
[   24.780087] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.816197] b44: eth0: Link is up at 100 Mbps, full duplex.
[   27.816201] b44: eth0: Flow control is off for TX and off for RX.
[   27.816788] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.172021] eth1: no IPv6 routers present
[   38.236027] eth0: no IPv6 routers present
[   83.060035] Clocksource tsc unstable (delta = -213471672 ns)
[  306.108098] APIC error on CPU0: 00(40)
[  590.864025] APIC error on CPU0: 40(40)
[  667.667118] APIC error on CPU0: 40(40)

**6 ) Network configuration**

justin@justin:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:b1:6c:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:6d:39:99
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.4 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:b4:89:e4:c8:a1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**7 ) Scan for networks:**

justin@justin:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

**8 ) Ubuntu Version: **

justin@justin:~$ lsb_release -d
Description:	Ubuntu 9.04
[B]
10 ) Restarting the network:
[/B]

justin@justin:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

---

