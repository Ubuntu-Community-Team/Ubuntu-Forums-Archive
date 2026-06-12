---
title: "b43-phy0 ERROR: PHY transmission error"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by schizostatic on 2009-05-30
Okay I am having some odd issues with my wifi. If I put it under some strain. Like transferring files from one network pc to this one or vice versa. I get
May 30 01:07:23 joe-laptop kernel: [  933.412630] b43-phy0 ERROR: PHY transmission error
Filling my syslog and then the card just sorta dies. No traffic in or out. But the card pretends like it is working. Also a side note. I randomly can't get on WAP networks. My home network is fine but if I goto a friends It just keeps trying but never gets on.

Laptop: Lenovo 3000 N200

```
joe@joe-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


joe@joe-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


joe@joe-laptop:~$ lspci -nn | grep Bro
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:22:b4:e8  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe22:b4e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:529585 (529.5 KB)  TX bytes:211677 (211.6 KB)

joe@joe-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"StaticWifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:63:66:43   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=65/100  Signal level:-74 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


joe@joe-laptop:~$ lsmod
Module                  Size  Used by
xt_limit               10116  6 
xt_tcpudp              11008  27 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13220  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
rfkill_input           12800  0 
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
nfsd                  227756  13 
lockd                  74156  1 nfsd
nfs_acl                11136  1 nfsd
auth_rpcgss            42144  1 nfsd
sunrpc                195424  13 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs               12544  1 nfsd
joydev                 18368  0 
coretemp               13952  0 
sbp2                   30476  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
iptable_nat            13700  0 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  9 iptable_nat,nf_nat
nf_conntrack           72008  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_hda_intel         435636  2 
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
iptable_mangle         10880  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  2 snd_pcm_oss
iptable_filter         10752  1 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
b43                   131484  0 
snd_seq_dummy          10756  0 
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
x_tables               23044  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 b43
cfg80211               38032  1 mac80211
psmouse                61972  0 
led_class              12036  1 b43
snd                    62628  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  2 snd
pcspkr                 10496  0 
serio_raw              13316  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
input_polldev          11912  1 b43
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
video                  25360  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
tg3                   131204  0 
ssb                    41220  1 b43
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


joe@joe-laptop:~$ dmesg | grep b43
[    3.927534] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.927548] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[   13.972800] b43-phy0: Broadcom 4311 WLAN found
[   35.972169] input: b43-phy0 as /devices/virtual/input/input8
[   36.072059] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   36.422614] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   36.449349] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   36.490601] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   36.628048] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   36.708511] Registered led device: b43-phy0::tx
[   36.708530] Registered led device: b43-phy0::rx
[   36.708557] Registered led device: b43-phy0::radio
[   36.724030] b43-phy0: Radio turned on by software
joe@joe-laptop:~$ dmesg | grep wlan0
[   36.724678] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.260237] wlan0: authenticate with AP 00:18:f8:1b:1d:4d
[   38.264434] wlan0: authenticated
[   38.264439] wlan0: associate with AP 00:18:f8:1b:1d:4d
[   38.294853] wlan0: RX AssocResp from 00:18:f8:1b:1d:4d (capab=0x401 status=0 aid=1)
[   38.294856] wlan0: associated
[   38.295271] wlan0: disassociating by local choice (reason=3)
[   66.312304] wlan0: authenticate with AP 00:22:6b:63:66:43
[   66.321331] wlan0: authenticated
[   66.321335] wlan0: associate with AP 00:22:6b:63:66:43
[   66.323929] wlan0: RX AssocResp from 00:22:6b:63:66:43 (capab=0x411 status=0 aid=2)
[   66.323932] wlan0: associated
[   66.325360] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   76.580019] wlan0: no IPv6 routers present

joe@joe-laptop:~$ sudo lshw -C network
[sudo] password for joe: 
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

joe@joe-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

joe@joe-laptop:~$ lsb_release -d
Description:	Ubuntu 9.04

joe@joe-laptop:~$ uname -mr
2.6.28-11-generic i686

joe@joe-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... 
   Ignoring unknown interface wlan0=wlan0.[ OK ]

```

---

### Post by chili555 on 2009-05-30
I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263106](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263106)  and I was especially interested in this:> I had the same issue with my BCM4318 [AirForce One 54G - rev 02 ] card with the release of Intrepid. My connection would work for about 1 minute and then crap out. I was able to get it to work by using a different firmware that was already extracted.

I got the working firmware from [http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

So the easy was to remove the older firmware from /lib/firmware/b43 and copy the attached firmware into this directory.I suggest you try this and report back so the searchers will know what worked, or not.

---

### Post by reaktae on 2009-07-19
I confirm the above has worked for me, running Lenny with 'BCM4306 (rev 03)'. Fwcutter fetched and successfully installed the 'broadcom-wl-4.150.10.5' driver, which kept loggin the infamous 'ERROR: PHY transmission error' all over the place. However, my WPA2 g-connection has not been dropping and speeds were nominal.

After trying a few different driver versions, I came accross this thread, linked to 'https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263106' and that's where I downloaded the following driver: 'http://launchpadlibrarian.net/19141977/b43-all-fw.tar.gz'.

After copying the archive contents into /lib/firmware, replacing the original 'b43' and 'b43legacy' folders, and executing:

'modprobe -r b43'
'modprobe b43'
'/etc/init.d/networking restart',

I no longer receive any errors in my logs, however transfer speeds have halved, for some reason. If anyone's interested, PM me for more on further investigation, as I may not find the time to post here...

ALSO, anyone following this should probably run 'lsmod' FIRST and check which modules are currently loaded. If it lists both, 'bcm43xx' and 'ndiswrapper', there could be your problem, as those two conflict. Either way, try unload all of the following: 'b43', 'b43legacy', 'bcm43xx', ''ndiswrapper' and  'ssb' with 'modprobe -r' and THEN load your new one, AFTER replacing the driver files.

This has given me a headache for about a month now and it seems that the problem is not the driver as much as the firmware ('http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg540212.html'). Hope this helps...

---

