---
title: "Dell 5150 Connection dropping on update / Can't connect to wifi"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by Velenos on 2013-06-22
Installed Xubuntu 13.04 on a Dell Inspiron 5150 yesterday. Installation would freeze up every time I tried checking "Download updates while installing"(or that other download option). Ethernet connection worked fine, after installing it with those unchecked, until I tried to run updates or download anything from the Software Manager, at which point it would disconnect until I restarted. It also happens when I try to download files from the terminal. I could browse Firefox fine, but when I tried to download addons it crashed as well. It didn't crashed when I downloaded normal files though.
I haven't downloaded any drivers or updates because I haven't really been able to yet. I'm also not that familiar with anything besides Windows -_-.
 Would appreciate any help I can get. Feel free to let me know any information you need posted.

---

### Post by praseodym on 2013-06-22
Hi,

please open a terminal window and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lspci -nnk | grep -iA2 VGA
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Velenos on 2013-06-22
lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Dell Device [1028:015f]
    Kernel driver in use: b44
02:02.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge

lspci -nnk | grep -iA2 VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV34M [GeForce FX Go5200 64M] [10de:0324] (rev a1)
    Subsystem: Dell Device [1028:015f]
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)


lsusb
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsmod
Module                  Size  Used by
bnep                   17669  2 
rfcomm                 37420  4 
parport_pc             27504  0 
ppdev                  12817  0 
bluetooth             202069  10 bnep,rfcomm
vesafb                 13500  1 
nouveau               834513  0 
snd_intel8x0           33096  2 
snd_ac97_codec        105692  1 snd_intel8x0
b43                   351918  0 
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
mxm_wmi                12893  1 nouveau
snd_seq_midi           13132  0 
wmi                    18590  2 mxm_wmi,nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    71289  1 nouveau
snd_rawmidi            25114  1 snd_seq_midi
drm_kms_helper         47545  1 nouveau
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm                   228750  3 ttm,drm_kms_helper,nouveau
joydev                 17097  0 
bcma                   39645  1 b43
mac80211              526519  1 b43
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
i2c_algo_bit           13197  1 nouveau
snd                    56485  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
cfg80211              436177  2 b43,mac80211
soundcore              12600  1 snd
pcmcia                 39544  0 
psmouse                81038  0 
dell_laptop            17161  0 
dcdbas                 14021  1 dell_laptop
serio_raw              13031  0 
microcode              18286  0 
yenta_socket           27095  0 
lpc_ich                16925  0 
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
video                  18894  1 nouveau
mac_hid                13037  0 
shpchp                 32129  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
b44                    31137  0 
ssb                    50628  2 b43,b44
firewire_ohci          35292  0 
firewire_core          61718  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Nothing happened when I did rfkill list

---

### Post by praseodym on 2013-06-22
First: Go to "Additional drivers" and install the proprietary recommended NVIDIA driver. Reboot. The freezes should have stopped.

Second: Download this package, save it in "Downloads" and install it via terminal:

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by Velenos on 2013-06-22
Thanks a lot man, seems like you fixed in a few minutes what I was trying to do for the last 8 hours, lol. Appreciate it. Wireless is working and my internet hasn't went out, just dl'd two things.

---

