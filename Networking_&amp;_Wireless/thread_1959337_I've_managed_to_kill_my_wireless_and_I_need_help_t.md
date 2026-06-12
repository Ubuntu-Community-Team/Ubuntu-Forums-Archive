---
title: "I've managed to kill my wireless and I need help to reestablish it"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by Stretchkev1 on 2012-04-15
So, I have an  ASUS laptop with an Intel Centrino Wireless-n 6150 chip with the problem connecting to networks.  While attempting the solutions from this thread: [http://ubuntuforums.org/showthread.php?t=1862484&page=8](http://ubuntuforums.org/showthread.php?t=1862484&page=8) I've managed to kill the wlan0 by accident and I don't know how to reestablish the driver.

```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

```

```
rfkill list all

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wimax: WiMAX
    Soft blocked: no
    Hard blocked: no

```

```
lsmod

Module                  Size  Used by
nls_utf8               12557  0 
isofs                  40253  0 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73882  0 
i915                  566711  4 
mac80211              310872  0 
uvcvideo               72711  0 
mei                    41480  0 
drm_kms_helper         42558  1 i915
videodev               93004  1 uvcvideo
drm                   236330  5 i915,drm_kms_helper
cfg80211              199587  1 mac80211
asus_nb_wmi            12517  0 
v4l2_compat_ioctl32    17083  1 videodev
asus_wmi               20035  1 asus_nb_wmi
i2c_algo_bit           13423  1 i915
usb_storage            57901  0 
sparse_keymap          13890  1 asus_wmi
serio_raw              13166  0 
wmi                    19256  1 asus_wmi
uas                    18027  0 
lp                     17799  0 
video                  19412  1 i915
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               78641  0 

```

```
lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 67
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: c8:60:00:2c:fc:47
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.69 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

Any help would be much appreciated.

---

