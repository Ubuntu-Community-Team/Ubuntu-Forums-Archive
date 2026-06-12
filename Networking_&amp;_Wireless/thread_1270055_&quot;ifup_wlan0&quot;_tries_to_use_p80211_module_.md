---
title: "&quot;ifup wlan0&quot; tries to use p80211 module on broadcom card"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by hailtothethief on 2009-09-19
So, I'm using a (sort of) custom kernel:

```
bryan@bryan-laptop:~$ uname -r
2.6.30-02063003-generic
```

Here's my lsmod:
```

bryan@bryan-laptop:~$ lsmod
Module                  Size  Used by
rfkill_input            5868  0 
b43                   127144  0 
ssb                    36692  1 b43
mac80211              214544  1 b43
cfg80211               65836  2 b43,mac80211
led_class               4112  1 b43
input_polldev           3892  1 b43
arc4                    1612  2 
ecb                     2508  2 
i915                  174664  2 
drm                   157152  3 i915
i2c_algo_bit            5776  1 i915
binfmt_misc             8084  1 
ppdev                   7280  0 
bridge                 47904  0 
stp                     2224  1 bridge
bnep                   12140  2 
vboxnetflt             82632  0 
vboxdrv               109160  1 vboxnetflt
joydev                 10464  0 
lp                      8900  0 
parport                35020  2 ppdev,lp
snd_hda_codec_conexant    20204  1 
snd_hda_intel          27304  2 
snd_hda_codec          74092  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7024  1 snd_hda_codec
snd_pcm_oss            40224  0 
snd_mixer_oss          16684  1 snd_pcm_oss
snd_pcm                76272  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2672  0 
snd_seq_oss            28448  0 
snd_seq_midi            6304  0 
snd_rawmidi            21536  1 snd_seq_midi
snd_seq_midi_event      6860  2 snd_seq_oss,snd_seq_midi
snd_seq                48560  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                56676  0 
iTCO_wdt               10864  0 
iTCO_vendor_support     3728  1 iTCO_wdt
snd_timer              21908  2 snd_pcm,snd_seq
snd_seq_device          7000  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               5392  0 
pcspkr                  2284  0 
intel_agp              26300  1 
agpgart                35884  3 drm,intel_agp
snd                    58276  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7168  1 snd
snd_page_alloc          8980  2 snd_hda_intel,snd_pcm
video                  19744  1 i915
output                  2764  1 video
usbhid                 37632  0 
8139too                24044  0 
8139cp                 20012  0 
mii                     4972  2 8139too,8139cp
```

When I run `ifup wlan0` I get the following output:
```

bryan@bryan-laptop:~$ sudo ifup wlan0
FATAL: Module p80211 not found.
Failed to load p80211.ko.
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
```

From what I can tell, p80211 is for cards with Prism chipsets. Why on earth is it trying to use that module when I have a Broadcom card and the correct module (b43) installed and modprobe'd up?

Here's my (relevant) lshw:

```
bryan@bryan-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:a6:86:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:22:e4:39:51:ac
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:0f:58:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.1 multicast=yes wireless=IEEE 802.11bg
```

One last thing, I can boot into another kernel version (2.6.28-15-generic) and the card works just fine. I have to use this new kernel version for the improved Intel GMA graphics drivers. 

Sorry for the length of this post, I just wanted to be thorough.

Any insight would be greatly appreciated.

---

### Post by hailtothethief on 2009-09-19
Good news!

The problem was that the ssb module (rather than the b43 module) was taking over my wireless card.

You test to see if you have this same problem by running:

```
lshw | grep ssb
```

If you get a line like:

```
configuration: driver=b43-pci-bridge latency=0 module=ssb
```

then you might have this problem. To verify, run this:
```

bryan@bryan-laptop:~$ sudo -i
root@bryan-laptop:~# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
root@bryan-laptop:~# modprobe -r b43
root@bryan-laptop:~# modprobe -r ssb
root@bryan-laptop:~# modprobe -b b43
```

And you your wireless should work. If it works, **you'll need to make this fix permanent via:**

```
root@bryan-laptop:~# echo "install b43 /sbin/modprobe -r ssb; /sbin/modprobe -b -i b43" >> /etc/modprobe.d/blacklist.conf
```

After a reboot the wireless **should** work. Feel free to contact me with any questions.

---

