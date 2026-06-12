---
title: "PRO/Wireless 3945 ABG (Golan) ,Acer Aspire 5610z  wireless problem"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by lorithai on 2012-12-31
Alright, I have recently installed ubuntu 12.04.1 LTS and my wireless connection doesn't seem to work (only wired). Going to follow ([http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)) so you have all the information you need.

**Machine Brand and Model (PC/Laptop)**:
Acer Aspire 5610Z laptop.

[B]Wireless Brand, Model and Wireless Chipset:
[/B]i believe it to be PRO/Wireless 3945 ABG (Golan) from intel.

[B]check interface:
[/B]     $ ifconfig $ iwconfig
Yielded
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:1f:39:c5  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe1f:39c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78562301 (78.5 MB)  TX bytes:2407859 (2.4 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37348 (37.3 KB)  TX bytes:37348 (37.3 KB)

```and 
 ```
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```respectively

**Check for modules:**
lsmod yielded
```
Module                  Size  Used by
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
usblp                  17885  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174222  1 
arc4                   12473  2 
snd_hda_intel          32765  2 
iwl3945                73152  0 
iwl_legacy             71134  1 iwl3945
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
snd_seq_midi           13132  0 
mac80211              436455  2 iwl3945,iwl_legacy
snd_rawmidi            25424  1 snd_seq_midi
videodev               86588  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nouveau               712356  3 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
snd_timer              28931  2 snd_pcm,snd_seq
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
joydev                 17393  0 
snd                    62064  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mxm_wmi                12859  1 nouveau
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
psmouse                72919  0 
mac_hid                13077  0 
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
wmi                    18744  2 mxm_wmi,acer_wmi
video                  19068  1 nouveau
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
b44                    31364  0 
ssb                    50691  1 b44

```**Kernel boot messages**
dmesg just game me a huge list of the following repeating with just the number in [ ] changing ever so slightly.

[ 2600.735436] iwl3945 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003CC

**Network configuration**
sudo lshw -C network gave

```
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:36:41:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-29-generic-pae firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:d2100000-d2100fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:1f:39:c5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.110 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:d2000000-d2001fff

```[B]Scan for networks
[/B]iwlist scan
gave

```
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.


```[B]Ubuntu version
[/B]12.04.1 LTS

[B]Kernel/architecture (including 32 vs. 64 bit): 
[/B]3.2.0-29-generic-pae i686

**Restarting the network:**
$ sudo /etc/init.d/networking restart
gave

```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```wow, thats a lot of info. I read around some before posting here and i think that what might be the problem is that this laptop has a button which disables wifi. it is switched on now, but someone wrote that it might not be possible to switch it on again in ubuntu, but that i would need to go back into windows to do so which i don't have anymore (deleted it as it was broken).

will be glad for all the help i can get ^^

---

