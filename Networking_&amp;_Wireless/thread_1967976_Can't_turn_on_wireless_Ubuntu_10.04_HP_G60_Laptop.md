---
title: "Can't turn on wireless Ubuntu 10.04 HP G60 Laptop"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by shawnicullen on 2012-04-28
I've been using Ubuntu 10.04 on my HP laptop for a while now with no problems.  In the last week, the wireless has stopped working.  I checked the wireless network with other devices, that is not the problem.  I can connect via wired network fine.  The wireless icon shows up greyed out with a red exclamation point.  It will let me edit connection settings for my wireless.  I've tried removing all wireless networks but my home network, that didn't help.  I've tried restarting, no help. I tried getting the latest updates in update manager while wired (all updates).  It returned a few errors, not sure if that's related.

For what it's worth, the wireless enable button on the laptop is illuminated blue, and doesn't seem to change anything when I press it.

Please help!

Thanks,

Shawn

---

### Post by shawnicullen on 2012-04-28
results of lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

results of lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a102 Suyin Corp. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

results of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1f:16:dd:72:f4  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fedd:72f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:231234297 (231.2 MB)  TX bytes:12223128 (12.2 MB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100844 (100.8 KB)  TX bytes:100844 (100.8 KB)

results of iwconfig  

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

reults of lsmod

Module                  Size  Used by
nfs                   265599  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_conexant    22705  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
nfsd                  238775  11 
lockd                  64881  2 nfs,nfsd
nfs_acl                 2245  2 nfs,nfsd
auth_rpcgss            33767  2 nfs,nfsd
sunrpc                193609  12 nfs,nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3437  1 nfsd
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74297  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
i915                  289683  3 
drm_kms_helper         29329  1 i915
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121632  0 
mac80211              205434  1 ath5k
ath                     7611  1 ath5k
uvcvideo               57438  0 
drm                   163779  4 i915,drm_kms_helper
psmouse                63677  0 
serio_raw               3978  0 
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            40033  0 
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32680  2 

results of sudo lshw -c network

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:dd:72:f4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:56:50:33:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d2600000-d260ffff


results of uname -mr
2.6.32-40-generic i686

restarting the network did not seem to have an effect

---

### Post by chili555 on 2012-04-28
Please let us see:```
rfkill list all
```Thanks.

---

### Post by shawnicullen on 2012-04-29
Soft Blocked: no
Hard Blocked: yes

Also note - when I right-click on the wireless icon, the "enable wireless" selection is greyed out.

Appreciate the help.

Shawn

---

### Post by chili555 on 2012-04-29
> Soft Blocked: no
Hard Blocked: yesThere is more to it than that. Doesn't it say something like:> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yesOr maybe something like:```
0: phy0: [COLOR="Red"]hp-wireless[/COLOR] LAN
	Soft blocked: no
	Hard blocked: yes
```Those trivial details tell us some things we need to know. Please show me:```
lsmod | grep hp
```

Obviously, if the wireless system is hard-blocked, it won't work at all.

---

### Post by shawnicullen on 2012-04-29
Sorry - missed that line before.  Here's the results below:

rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

lsmod | grep hp
That doesn't seem to do anything.  It just returns a command line.

---

### Post by chili555 on 2012-04-29
I'm fairly confident that this:> For what it's worth, the wireless enable button on the laptop is illuminated blue, and doesn't seem to change anything when I press it....means the same as this:> 0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]May I see:```
lsmod
```Is there any improvement with:```
sudo modprobe -r ath5k
sudo rfkill unblock all
sudo modprobe ath5k
rfkill list all
```Thanks.

---

### Post by shawnicullen on 2012-04-29
Module                  Size  Used by
nfs                   265599  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_conexant    22705  1 
fbcon                  35102  72 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
nfsd                  238775  11 
lockd                  64881  2 nfs,nfsd
nfs_acl                 2245  2 nfs,nfsd
auth_rpcgss            33767  2 nfs,nfsd
sunrpc                193609  12 nfs,nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3437  1 nfsd
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74297  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
i915                  289683  3 
drm_kms_helper         29329  1 i915
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121632  0 
mac80211              205434  1 ath5k
ath                     7611  1 ath5k
uvcvideo               57438  0 
drm                   163779  4 i915,drm_kms_helper
psmouse                63677  0 
serio_raw               3978  0 
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            40033  0 
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32680  2

---

### Post by shawnicullen on 2012-04-29
That seems to have worked thank you very much!

Shawn

So, what should I do to prevent it from getting blocked again?

---

### Post by chili555 on 2012-04-29
> **shawnicullen said:**
> That seems to have worked thank you very much!

Shawn

So, what should I do to prevent it from getting blocked again?I assume this is what did it:```
sudo modprobe -r ath5k
sudo rfkill unblock all
sudo modprobe ath5k
```If so, please do:```
sudo gedit /etc/rc.local
```Right above exit 0 add this:```
modprobe -r ath5k
rfkill unblock all
modprobe ath5k
```Proofread carefully, save and close gedit. If you don't have gedit, use any other text editor such as nano, leafpad, kate or vim.

On reboot, is it working?

---

