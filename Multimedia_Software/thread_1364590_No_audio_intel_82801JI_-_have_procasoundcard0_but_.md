---
title: "No audio intel 82801JI - have /proc/asound/card0 but alsautils can't find hardware"
date: 2009-12-26
forum: Multimedia Software
---

### Post by adante on 2009-12-26
Hello. I somewhat foolishly decided to upgrade to 9.10 yesterday in the hopes that after 2 months in the wild it should be reasonably error free.

Anyway. It was - mostly. I can't boot I have to boot off've a 2.6.28-17-generic kernel because the 2.6.31-16-generic immediatelly throws some random kernel panic not syncing out of memory error*. I figured I could live with this.

Unfortunately I can't because it turns out audio doesn't work. Also unfortunately I no longer am in the position where I have the requisite 20 hours spare to fix this so I thought I would just post the basic information here in the hopes that someone might know of a quick fix.

lspci -v:
```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Giga-byte Technology Device a102
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e1700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```lsmod:
```

adante@veer:/home/zmc$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1
i915                   67844  0
drm                    96424  1 i915
dm_crypt               20996  0
nfsd                  228012  17
auth_rpcgss            42144  1 nfsd
exportfs               12416  1 nfsd
nfs                   266600  0
lockd                  74284  2 nfsd,nfs
nfs_acl                11136  2 nfsd,nfs
iptable_filter         10752  0
ip_tables              19600  1 iptable_filter
x_tables               23044  1 ip_tables
snd_hda_intel         436148  0
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
sunrpc                195552  15 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dvb_usb_af9015         28196  0
dvb_usb                24332  1 dvb_usb_af9015
dvb_core               92032  1 dvb_usb
snd                    62756  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  15620  0
soundcore              15200  1 snd
psmouse                61972  0
serio_raw              13444  0
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
parport_pc             40100  1
sbp2                   30476  0
lp                     17156  0
parport                42220  3 ppdev,parport_pc,lp
hid_logitech           16256  0
ff_memless             13320  1 hid_logitech
usbhid                 42336  1 hid_logitech
ohci1394               38576  0
pata_it8213            12548  0
ieee1394               94660  2 sbp2,ohci1394
r8169                  40836  0
mii                    13312  1 r8169
floppy                 64324  0
intel_agp              34108  1
agpgart                42696  3 drm,intel_agp

```attempting to run various alsa tools shows there are no devices :

```

adante@veer:~$ aplay -l
aplay: device_list:223: no soundcards found...
adante@veer:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```yet strangely there seem to be alsa devices in /proc/asound/:
```

adante@veer:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe1700000 irq 22

adante@veer:~$ ls /proc/asound/card0 -al
total 0
dr-xr-xr-x 7 root root 0 2009-12-26 18:22 .
dr-xr-xr-x 5 root root 0 2009-12-26 18:22 ..
-r--r--r-- 1 root root 0 2009-12-26 18:22 codec#2
-r--r--r-- 1 root root 0 2009-12-26 18:22 id
-rw-r--r-- 1 root root 0 2009-12-26 18:22 oss_mixer
dr-xr-xr-x 3 root root 0 2009-12-26 18:22 pcm0c
dr-xr-xr-x 3 root root 0 2009-12-26 18:22 pcm0p
dr-xr-xr-x 3 root root 0 2009-12-26 18:22 pcm1c
dr-xr-xr-x 3 root root 0 2009-12-26 18:22 pcm1p
dr-xr-xr-x 3 root root 0 2009-12-26 18:22 pcm2c


```

A copy of dmesg is [here](http://pastebin.com/m7bcd7ba8)
Full lspci -v is [here](http://pastebin.com/m29fb5635)

A friend suggested I install linux-backports-modules-2.6.28-17-generic so I did. After a reboot it was much the same. 

I would appreciate it if someone could advise me as to the most painless manner in which I can get audio working again. If one such exists.


[SIZE=1] * incidentally I was going to report this but you can't do this on the web anymore, and 'ubuntu-bug linux' claims this is not a genuinge ubuntu package, and 'ubuntu-bug linux-image-2.6.31-16-generic' wants to upload a 350 meg bug report.[/SIZE]

---

