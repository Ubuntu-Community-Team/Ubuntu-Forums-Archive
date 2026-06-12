---
title: "Wired Netwrok and Sound gone after update"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by ishu161 on 2012-02-01
So I was having some trouble installing Chromium Browser yesterday, and the folks at #ubuntu helped me out. Turns out my security updates were disabled and someone was kind enough to provide me with a new *sources.list* file, which I replaced with the old one and updated. (I was able to install chromium, but it still didn't work.)

Everything was fine after that, but I wake up this morning and find out that my network and sound is completely gone. Meaning, Ubuntu won't even detect my router. The network connections menu is also not working. When I try to open network connections via the preferences menu, it appears for a few seconds on the panel, but then stops. (This was the same thing that happened with chromium after install.)

So what do I do? I'm running Ubuntu 11.04 64 bit, dual boot with Windows 7. I don't know much about network managing in Ubuntu, but here's the output of ifconfig -a, if that helps: 
```

eth0      Link encap:Ethernet  HWaddr 6c:62:6d:69:43:21  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 [/QUOTE]
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

Thanks. :)

---

### Post by praseodym on 2012-02-01
Hi,

please show the outputs of:

```
lsb_release -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/apt/sources.list
```

---

### Post by ishu161 on 2012-02-01
Hello. These are the outputs:

lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty
```lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7623]
    Kernel driver in use: atl1c
```lsmod
```
Module                  Size  Used by
binfmt_misc            17565  1 
snd_hda_codec         103804  0 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96145  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30435  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
radeon                982182  3 
snd_seq                61397  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29396  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
ppdev                  17113  0 
joydev                 17606  0 
ttm                    76664  1 radeon
drm_kms_helper         42394  1 radeon
drm                   227534  5 radeon,ttm,drm_kms_helper
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
serio_raw              13166  0 
snd                    67853  8 snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17078  1 videodev
edac_core              53845  0 
edac_mce_amd           23464  0 
k10temp                13119  0 
sp5100_tco             13744  0 
i2c_algo_bit           13400  1 radeon
parport_pc             36959  1 
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18484  1 snd_pcm
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  0 
pata_atiixp            13165  7 
libahci                26642  1 ahci
atl1c                  41171  0 
```cat /etc/network/interfaces```

auto lo
iface lo inet loopback
```
cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```
cat /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ natty main restricted

# Security
deb http://security.ubuntu.com/ubuntu natty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://in.archive.ubuntu.com/ubuntu/ natty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ natty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main


```


Thank you for the help. Also, I just noticed that a few panel applets are also gone. (The clock app, the status app). And it won't come back when I try to add it. :(

---

### Post by ishu161 on 2012-02-02
I've been able to get my network up and running by modifying the /etc/network/interfaces file from this: 

```
auto lo
iface lo inet loopback

```

to this: 
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Is there anything else I should be doing? Is this  fix permanent? 

Thanks.

---

### Post by praseodym on 2012-02-02
Yes, if you change "false" to "true" in the file **/etc(NetworkManager/NetworkManager.conf**, otherwise the networkmanager ignores these settings

---

### Post by ishu161 on 2012-02-03
Done. Thanks. :)

---

