---
title: "Dell DW1501 Mini-PCI Load Issue - 12.04.02"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by ere109 on 2013-02-07
I have a Dell Inspiron N7010 laptop with the DW1501 mini-pci card - Broadcom 4313 chipset.  I've got a strange driver loading issue.  If I power the machine down completely, then do a cold boot into Ubuntu 12.04.02 LTS (3.2.0-37-generic x86_64), it detects my wireless, connects, and internet works properly.  If I restart the machine (hot boot), when it comes back up I get no wireless detection. 
    I've uninstalled ALL BCM drivers and devices other than the STA driver - which now allows me to access the internet but not my network attached storage drive. 
    I've read dozens of help articles and stickies, but haven't found any post that specifically solves this issue for my hardware. I followed the advice of ([http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)) and posted output for both cold and warm start info below. 
 
 
**COLD START RESULT: **
 
lspci -vvnn | grep 14e4 
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 
 
```

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:46:42:f8   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:44
 
eth1      Link encap:Ethernet  HWaddr 1c:65:9d:06:78:97   
          inet addr:192.168.109.103  Bcast:192.168.109.255  Mask:255.255.255.0 
          inet6 addr: fe80::1e65:9dff:fe06:7897/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:6207 errors:1 dropped:0 overruns:0 frame:15023 
          TX packets:5534 errors:11 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:5546162 (5.5 MB)  TX bytes:945409 (945.4 KB) 
          Interrupt:17  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:813 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:813 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:72650 (72.6 KB)  TX bytes:72650 (72.6 KB) 
 

```

iwconfig 
```
lo        no wireless extensions. 
 
eth1      IEEE 802.11abg  ESSID:"*MYWIRELESS*"   
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:66:47:56:1F    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
eth0      no wireless extensions. 

```

lsmod | grep "wlan_module_name" 
(Returns nothing) 
 
lsmod 
```
Module                  Size  Used by 
nls_utf8               12557  0  
cifs                  287317  0  
pci_stub               12622  1  
vboxpci                23237  0  
vboxnetadp             13382  0  
vboxnetflt             23478  0  
joydev                 17693  0  
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt 
lib80211_crypt_tkip    17390  0  
wl                   3074895  0  
snd_hda_codec_hdmi     32474  1  
snd_hda_codec_realtek   224173  1  
bnep                   18281  2  
rfcomm                 47604  0  
bluetooth             180153  10 bnep,rfcomm 
parport_pc             32866  0  
ppdev                  17113  0  
nfsd                  277884  2  
nfs                   356470  0  
lockd                  90326  2 nfsd,nfs 
binfmt_misc            17540  1  
fscache                61529  1 nfs 
auth_rpcgss            53380  2 nfsd,nfs 
nfs_acl                12883  2 nfsd,nfs 
sunrpc                245863  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl 
dell_wmi               12681  0  
sparse_keymap          13890  1 dell_wmi 
uvcvideo               72627  0  
videodev               98259  1 uvcvideo 
v4l2_compat_ioctl32    17128  1 videodev 
snd_hda_intel          33773  3  
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              17764  1 snd_hda_codec 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0  
snd_rawmidi            30748  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
dell_laptop            18119  0  
dcdbas                 14490  1 dell_laptop 
cfg80211              205774  1 wl 
lib80211               14381  2 lib80211_crypt_tkip,wl 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
psmouse                97485  0  
serio_raw              13211  0  
wmi                    19256  1 dell_wmi 
snd_timer              29990  2 snd_pcm,snd_seq 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
intel_ips              18174  0  
mac_hid                13253  0  
i915                  477602  8  
soundcore              15091  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
drm_kms_helper         46978  1 i915 
drm                   241971  4 i915,drm_kms_helper 
mei                    41616  0  
i2c_algo_bit           13423  1 i915 
video                  19596  1 i915 
lp                     17799  0  
parport                46562  3 parport_pc,ppdev,lp 
ums_realtek            18248  0  
usb_storage            49198  1 ums_realtek 
uas                    18180  0  
atl1c                  41718  0  
 

```

lsmod | grep "wl" 
```
wl                   3074895  0  
cfg80211              205774  1 wl 
lib80211               14381  2 lib80211_crypt_tkip,wl 
 
```

dmesg 
```
[   26.541737] wl: module license 'MIXED/Proprietary' taints kernel. 
[   30.287325] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264) 
[   43.671137] eth1: no IPv6 routers present 
[ 1260.022987] ERROR @wl_cfg80211_get_station : Could not get rate (-1) 
[ 1260.022995] ERROR @wl_cfg80211_get_station : Could not get rssi (-1) 
[ 1260.023006] ERROR @wl_cfg80211_get_station : Could not get rate (-1) 
[ 1260.023010] ERROR @wl_cfg80211_get_station : Could not get rssi (-1) 
[ 1260.023019] ERROR @wl_dev_intvar_get : error (-1) 
[ 1260.023023] ERROR @wl_cfg80211_get_tx_power : error (-1) 
 

```

dmesg | grep "wl" 
```
[   26.541737] wl: module license 'MIXED/Proprietary' taints kernel. 
[   26.548575] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   26.548588] wl 0000:03:00.0: setting latency timer to 64 
[   26.588788] INFO @wl_cfg80211_attach : Registered CFG80211 phy 
[ 1260.022987] ERROR @wl_cfg80211_get_station : Could not get rate (-1) 
[ 1260.022995] ERROR @wl_cfg80211_get_station : Could not get rssi (-1) 
[ 1260.023006] ERROR @wl_cfg80211_get_station : Could not get rate (-1) 
[ 1260.023010] ERROR @wl_cfg80211_get_station : Could not get rssi (-1) 
[ 1260.023019] ERROR @wl_dev_intvar_get : error (-1) 
[ 1260.023023] ERROR @wl_cfg80211_get_tx_power : error (-1) 
 
```

dmesg | grep "eth1" 
```
[   30.287325] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264) 
[   43.671137] eth1: no IPv6 routers present 
 

```

sudo lshw -C network 
  ```
*-network                
       description: Wireless interface 
       product: BCM4313 802.11b/g/n Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth1 
       version: 01 
       serial: 1c:65:9d:06:78:97 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.109.103 latency=0 multicast=yes wireless=IEEE 802.11abg 
       resources: irq:17 memory:f0500000-f0503fff 
  *-network 
       description: Ethernet interface 
       product: AR8152 v1.1 Fast Ethernet 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: c1 
       serial: f0:4d:a2:46:42:f8 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:44 memory:f0400000-f043ffff ioport:2000(size=128) 
 

```

iwlist scan 
```
lo        Interface doesn't support scanning. 
 
eth1      Scan completed : 
          Cell 01 - Address: 00:0F:66:47:56:1F 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=67/70  Signal level=-43 dBm   
                    Encryption key:on 
                    ESSID:"DoubleE" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000000000000000 
                    Extra: Last beacon: 97388ms ago 
                    IE: Unknown: 0007446F75626C6545 
                    IE: Unknown: 010882848B9624B0486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32048C129860 
                    IE: Unknown: DD090010180204F0000000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
 
eth0      Interface doesn't support scanning. 
 

```

sudo /etc/init.d/networking restart 
 ```
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces 
 * Reconfiguring network interfaces... 
 
```
 
**WARM START RESULT: **
 
lspci -vvnn | grep 14e4 
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 

```

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:46:42:f8   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:43  
 
eth1      Link encap:Ethernet  HWaddr 1c:65:9d:06:78:97   
          inet6 addr: fe80::1e65:9dff:fe06:7897/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:294 
          TX packets:0 errors:35 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1156 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1156 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:90784 (90.7 KB)  TX bytes:90784 (90.7 KB) 

```

iwconfig 
```
lo        no wireless extensions. 
 
eth1      IEEE 802.11abg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
eth0      no wireless extensions. 

```

iwconfig wlan0 
```
wlan0     No such device 
```

lsmod 
```
Module                  Size  Used by 
nls_utf8               12557  0  
cifs                  287317  0  
pci_stub               12622  1  
vboxpci                23237  0  
vboxnetadp             13382  0  
vboxnetflt             23478  0  
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt 
joydev                 17693  0  
snd_hda_codec_hdmi     32474  1  
snd_hda_codec_realtek   224173  1  
parport_pc             32866  0  
ppdev                  17113  0  
rfcomm                 47604  0  
bnep                   18281  2  
lib80211_crypt_tkip    17390  0  
bluetooth             180153  10 rfcomm,bnep 
wl                   3074895  0  
dell_wmi               12681  0  
sparse_keymap          13890  1 dell_wmi 
uvcvideo               72627  0  
videodev               98259  1 uvcvideo 
v4l2_compat_ioctl32    17128  1 videodev 
snd_hda_intel          33773  3  
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              17764  1 snd_hda_codec 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0  
snd_rawmidi            30748  1 snd_seq_midi 
nfsd                  277884  2  
snd_seq_midi_event     14899  1 snd_seq_midi 
nfs                   356470  0  
binfmt_misc            17540  1  
lockd                  90326  2 nfsd,nfs 
fscache                61529  1 nfs 
auth_rpcgss            53380  2 nfsd,nfs 
nfs_acl                12883  2 nfsd,nfs 
sunrpc                245863  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl 
dell_laptop            18119  0  
dcdbas                 14490  1 dell_laptop 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              29990  2 snd_pcm,snd_seq 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              205774  1 wl 
lib80211               14381  2 lib80211_crypt_tkip,wl 
intel_ips              18174  0  
psmouse                97485  0  
serio_raw              13211  0  
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15091  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
i915                  477602  8  
drm_kms_helper         46978  1 i915 
drm                   241971  4 i915,drm_kms_helper 
i2c_algo_bit           13423  1 i915 
wmi                    19256  1 dell_wmi 
video                  19596  1 i915 
mac_hid                13253  0  
mei                    41616  0  
lp                     17799  0  
parport                46562  3 parport_pc,ppdev,lp 
atl1c                  41718  0  

```

dmesg | grep "wl" 
```
[   25.566786] wl: module license 'MIXED/Proprietary' taints kernel. 
[   25.571311] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   25.571320] wl 0000:03:00.0: setting latency timer to 64 
[   25.606351] INFO @wl_cfg80211_attach : Registered CFG80211 phy 
[   37.416872] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[   58.238741] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[   88.228976] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  128.207873] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  178.174818] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  238.143001] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  298.114269] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  358.076260] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  418.043676] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  477.564429] ERROR @wl_dev_intvar_get : error (-1) 
[  477.564434] ERROR @wl_cfg80211_get_tx_power : error (-1) 
[  478.013910] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  537.977337] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  597.944285] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 

```

sudo lshw -C network 
  ```
*-network                
       description: Wireless interface 
       product: BCM4313 802.11b/g/n Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth1 
       version: 01 
       serial: 1c:65:9d:06:78:97 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg 
       resources: irq:17 memory:f0500000-f0503fff 
  *-network 
       description: Ethernet interface 
       product: AR8152 v1.1 Fast Ethernet 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: c1 
       serial: f0:4d:a2:46:42:f8 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128) 

```

iwlist scan 
```
lo        Interface doesn't support scanning. 
 
eth1      No scan results 
 
eth0      Interface doesn't support scanning. 

```

sudo /etc/init.d/networking restart 
 ```
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces 
 * Reconfiguring network interfaces...                                   [ OK ]  
 
```
 
Note: the network restart command had no effect on bringing wifi back, but a shutdown and restart did.  BIOS issue?  Hardware switch not being activated? 
 
Thanks

---

### Post by Hadaka on 2013-02-07
Hi try this, on the next warm boot and the wifi driver does not load..
do,
```
sudo modprobe wl
```

*IF that loads the driver for you then
do.
```
sudo su
echo wl >> /etc/modules
exit
```

this will then load your driver module on a warm or cold boot.

---

### Post by ere109 on 2013-02-07
Thanks.  I just did two warm reboots and wireless came back both times.   I've now got: 
bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source
installed.

Strangely, other wireless devices in the house are having trouble connecting, now.  My next step will be a router reboot, but I fear it's something that got clicked or unclicked while I was trying to solve this wireless mystery.

---

### Post by ere109 on 2013-02-12
Update: I was away from the computer for the weekend, so shut it off.  When I cold booted tonight, Ubuntu didn't load wireless.  I tried two warm reboots without any effect, so I fear the problem persists.  "Modprobe WL" didn't do anything for me.  I'm searching threads now.  If someone has a suggestion, please share.  If I find anything, I'll report back.

---

### Post by ere109 on 2013-02-12
Wierdest thing of the day, I seem to have fixed the issue.  The report below is basically my attempt to figure out what was wrong, which resulted in a final reboot that brought back wifi - will figure out which driver it's operating on and repost.
After spending several hours, reading dozens of pages, I feel/felt a little more comfortable with my system and the potential to make something work.  So I compiled a list of commands (and even read what they actually do) to try.  The results are pasted below: 
 
lsmod 
```
 wl                   3074895  0  
```
 
modprobe -r wl 
```
FATAL: Error removing wl (/lib/modules/3.2.0-37-generic/updates/dkms/wl.ko): Operation not permitted 
 
```
sudo modprobe -r wl 
```
Network Disconnected 
 
```
sudo modprobe wl 
 
ping 8.8.8.8 
```
connect: Network is unreachable 
 
```
lsmod | grep wl 
```
wl                   3074895  0  
cfg80211              205774  1 wl 
lib80211               14381  2 #wl,lib80211_crypt_tkip 
 
```
sudo lshw -C network 
```
*-network                
       description: Wireless interface 
       product: BCM4313 802.11b/g/n Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth1 
       version: 01 
       serial: 1c:65:9d:06:78:97 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg 
       resources: irq:17 memory:f0500000-f0503fff 
  *-network 
       description: Ethernet interface 
       product: AR8152 v1.1 Fast Ethernet 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: c1 
       serial: f0:4d:a2:46:42:f8 
       capacity: 100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128) 
 
```
dmesg | grep -i 'wl\|wlan' 
```
[   18.235183] wl: module license 'MIXED/Proprietary' taints kernel. 
[   18.273112] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   18.273125] wl 0000:03:00.0: setting latency timer to 64 
[   18.340342] INFO @wl_cfg80211_attach : Registered CFG80211 phy 
[   29.509044] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[   50.236910] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[   80.220297] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  120.204432] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  170.176088] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  230.135633] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  290.107455] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  339.036130] wlc_lcnphy_rx_gain_tbl_free_entry = 5 
[  339.036211] wl 0000:03:00.0: PCI INT A disabled 
[  383.855860] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[  383.855874] wl 0000:03:00.0: setting latency timer to 64 
[  383.892547] INFO @wl_cfg80211_attach : Registered CFG80211 phy 
[  385.022212] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  405.039019] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  435.026820] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  475.004285] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  524.972262] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  584.939974] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  644.907298] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  704.873340] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  764.840038] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  824.807568] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  884.773904] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[  944.740761] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[ 1004.708580] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[ 1064.679318] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
[ 1124.641513] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
 
```
cat /var/log/kern.log | grep -i 'wl\|wlan' 
```
Feb 12 01:16:18 ubuntu kernel: [  764.840038] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:17:18 ubuntu kernel: [  824.807568] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:18:18 ubuntu kernel: [  884.773904] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:19:18 ubuntu kernel: [  944.740761] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:20:18 ubuntu kernel: [ 1004.708580] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:21:18 ubuntu kernel: [ 1064.679318] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:22:18 ubuntu kernel: [ 1124.641513] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:23:18 ubuntu kernel: [ 1184.608088] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
Feb 12 01:24:18 ubuntu kernel: [ 1244.575026] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22) 
 
```
iwconfig 
```
lo        no wireless extensions. 
 
eth1      IEEE 802.11abg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
 
```
lspci 
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01) 
04:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1) 
ff:00.0 Host bridge: Intel Corporation Core  
 
```
grep blacklist /etc/modprobe.d/blacklist.conf 
```
blacklist evbug 
blacklist usbmouse 
blacklist usbkbd 
blacklist eepro100 
blacklist de4x5 
blacklist eth1394 
blacklist snd_intel8x0m 
blacklist snd_aw2 
blacklist i2c_i801 
blacklist prism54 
blacklist bcm43xx 
blacklist garmin_gps 
blacklist asus_acpi 
blacklist snd_pcsp 
blacklist pcspkr 
blacklist amd76x_edac 
 
```
grep wlan0 /etc/udev/rules.d/70-persistent-net.rules 
```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:65:9d:06:78:97", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0" 
 
```
grep eth1 /etc/udev/rules.d/70-persistent-net.rules 
```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:65:9d:06:78:97", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1" 
 
```
nm-tool 
 ```
NetworkManager Tool 
 
State: disconnected 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            atl1c 
  State:             unavailable 
  Default:           no 
  HW Address:        F0:4D:A2:46:42:F8 
 
  Capabilities: 
    Carrier Detect:  yes 
 
  Wired Properties 
    Carrier:         off 
 
```
modprobe --list 
```
kernel/net/wireless/cfg80211.ko 
kernel/net/wireless/lib80211.ko 
kernel/net/wireless/lib80211_crypt_wep.ko 
kernel/net/wireless/lib80211_crypt_ccmp.ko 
kernel/net/wireless/lib80211_crypt_tkip.ko 
 
*-pci:1 
             description: PCI bridge 
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2 
             vendor: Intel Corporation 
             physical id: 1c.1 
             bus info: pci@0000:00:1c.1 
             version: 06 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:17 ioport:3000(size=4096) memory:f0500000-f05fffff ioport:c0200000(size=2097152) 
           *-network UNCLAIMED 
                description: Network controller 
                product: BCM4313 802.11b/g/n Wireless LAN Controller 
                vendor: Broadcom Corporation 
                physical id: 0 
                bus info: pci@0000:03:00.0 
                version: 01 
                width: 64 bits 
                clock: 33MHz 
                capabilities: cap_list 
                configuration: latency=0 
                resources: memory:f0500000-f0503fff 
        *-pci:2 
             description: PCI bridge 
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6 
             vendor: Intel Corporation 
             physical id: 1c.5 
             bus info: pci@0000:00:1c.5 
             version: 06 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:17 ioport:2000(size=4096) memory:f0400000-f04fffff ioport:c0000000(size=2097152) 
           *-network 
                description: Ethernet interface 
                product: AR8152 v1.1 Fast Ethernet 
                vendor: Atheros Communications Inc. 
                physical id: 0 
                bus info: pci@0000:04:00.0 
                logical name: eth0 
                version: c1 
                serial: f0:4d:a2:46:42:f8 
                capacity: 100Mbit/s 
                width: 64 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair 
                resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128) 
 
```
_____________________________________________ 
    What I learned from this is that both wlan0 and eth1 have the same mac address, and that the card is loading wl0 driver version=6.20.155.1.  The return I got from dmesg is interesting, but I'm not entirely sure how to read it. 
[   18.235183] wl: module license 'MIXED/Proprietary' taints kernel.  Why "taints?"  That doesn't sound good. 
    I also searched the /etc/modprobe.d/ directory and found a file called "broadcom-sta-common.conf" that blacklists other common 4313 drivers, including brcmsmac, and a redundant file "blacklist-bcm43.conf" that does the same: 
```

# wl module from Broadcom conflicts with ssb 
# We must blacklist the following modules: 
blacklist b44 
blacklist b43legacy 
blacklist b43 
blacklist brcm80211 
blacklist brcmsmac 
blacklist ssb 
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS 
```
 
    Next, I decided to start eliminating the STA drivers, to see if I'd have better luck with something else.  In the beginning, I had "bcmwl-kernel-source" , "broadcom-sta-common" , and "broadcom-sta-source."  I uninstalled all three through software center, then ran sudo apt-get remove bcmwl-kernel-source just to be sure.  Then I restarted. 
    When the machine loaded, as expected, there was no wifi.  I checked some things out.  The b43 blacklist was gone, but broadcom-sta-common.conf still existed.  I ignored the lines ```

#blacklist brcmsmac 
#install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS 
```
 
sudo lshw -C network 
```
*-network                
       description: Network controller 
       product: BCM4313 802.11b/g/n Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=bcma-pci-bridge latency=0 
       resources: irq:17 memory:f0500000-f0503fff 
 
```
Then I did a full purge of bcmwl... 
sudo apt-get remove --purge bcmwl-kernel-source 
```
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages will be REMOVED: 
  bcmwl-kernel-source* 
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded. 
After this operation, 0 B of additional disk space will be used. 
Do you want to continue [Y/n]? Y 
(Reading database ... 506903 files and directories currently installed.) 
Removing bcmwl-kernel-source ... 
Purging configuration files for bcmwl-kernel-source ... 
update-initramfs: deferring update (trigger activated) 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic 
Warning: No support for locale: en_US.utf8 
 
```
Reboot

---

### Post by ere109 on 2013-02-12
And the survey says:
lsmod | grep brc
```
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

``` 

My wireless hardware also now shows up as wlan0, instant of eth1.  I'll give this a few days to settle and test, but I absolutely believe the STA drivers caused my issue, and removing them completely has now solved my problem (tentatively).

---

