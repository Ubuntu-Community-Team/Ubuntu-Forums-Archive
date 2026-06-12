---
title: "Wireless will not work after install"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by dabast1 on 2012-06-28
Hi all

I'm new to using UBUNTU, I just did a fresh install on a Dell Latitude D630 and can not get the wireless to work properly

when I do  lshw -c network, this is what I get

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:34:5a:e1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5755m-v3.29 ip=192.168.0.109 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fe7f0000-fe7fffff

Any help would be appreciated.

---

### Post by josephmills on 2012-06-28
can we see a 
```
lspci -nn | grep 14e4 
```
and also 
```
lsmod
```
and 
```
rfkill list all 
```

---

### Post by dabast1 on 2012-06-28
~$ lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

~$ lsmod
Module                  Size  Used by
iwlwifi               292030  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac80211
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
i915                  414663  3 
joydev                 17393  0 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
drm_kms_helper         45466  1 i915
psmouse                72919  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
drm                   197692  4 i915,drm_kms_helper
snd_seq_midi           13132  0 
dell_laptop            17767  0 
pcmcia                 39791  0 
dell_wmi               12601  0 
serio_raw              13027  0 
sparse_keymap          13658  1 dell_wmi
snd_rawmidi            25424  1 snd_seq_midi
mac_hid                13077  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 i915
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
wl                   2646601  0 
lib80211               14040  1 wl
wmi                    18744  1 dell_wmi
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   141369

~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by josephmills on 2012-06-28
you have the wrong driver loaded 
do this 
```
sudo rmmod wl
```
then 
```
sudo apt-get --purge remove broadcom-sta-common broadcom-sta-dkms  broadcom-sta-source 
```

then 
```
sudo apt-get install b43-fwcutter 
```
```

 sudo apt-get install firmware-b43-installer

```
then 

```
sudo modprobe b43
```

Do you have wireless ? if not post 
```
rfkill list all 
```
and 
```
dmesg | grep b43
```
thanks

---

### Post by dabast1 on 2012-06-28
It worked! Thank you very much!

---

### Post by kumars on 2012-06-28
Hi,

I am new to ubuntu, I tried the same thing but it didnt work, in my case it says its connect..

Ping 4.2.2.2 -c 4 says Destination Net Unreachable..

Any help would be highly appreciated.

Thanks in advance

---

### Post by josephmills on 2012-06-28
> **dabast1 said:**
> It worked! Thank you very much!

np can you mark the thread as solved please and Thanks.

---

### Post by Elfy on 2012-06-28
> **kumars said:**
> Hi,

I am new to ubuntu, I tried the same thing but it didnt work, in my case it says its connect..

Ping 4.2.2.2 -c 4 says Destination Net Unreachable..

Any help would be highly appreciated.

Thanks in advance

Please start your own thread please, thank you.

---

