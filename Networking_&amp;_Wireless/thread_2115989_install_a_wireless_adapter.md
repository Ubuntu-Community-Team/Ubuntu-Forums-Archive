---
title: "install a wireless adapter"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by seneca2535 on 2013-02-14
Hello to everybody,
I'm very new in this forum and also in using ubuntu.
I'm trying to install a netway 579 wireless adapter to my computer. It's got a ralink 3070 which I can't install.
I very much appreciate your help. Thanks

---

### Post by praseodym on 2013-02-14
Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands:
```

lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by seneca2535 on 2013-02-18
Hi, thanks for your reply.
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ lsusb
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 004: ID 03f0:6c11 Hewlett-Packard 
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ lsmod
Module                  Size  Used by
usblp                  17752  0 
bnep                   17708  2 
bluetooth             183270  7 bnep
radeon                820764  3 
wl                   3032350  1 
snd_atiixp             19280  2 
snd_atiixp_modem       18556  5 
snd_ac97_codec        105652  2 snd_atiixp,snd_atiixp_modem
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
ac97_bus               12671  1 snd_ac97_codec
drm                   238811  5 radeon,ttm,drm_kms_helper
snd_pcm                80235  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
joydev                 17162  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              12899  0 
i2c_algo_bit           13198  1 radeon
snd_timer              24412  2 snd_pcm,snd_seq
pcmcia                 39545  0 
psmouse                84878  0 
tifm_core              15069  1 tifm_7xx1
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27096  0 
i2c_piix4              12984  0 
cfg80211              175574  1 wl
pcmcia_rsrc            18192  1 yenta_socket
ati_agp                13178  0 
hp_wmi                 13617  0 
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32190  0 
snd                    62146  20 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13032  0 
sparse_keymap          13659  1 hp_wmi
lib80211               14041  1 wl
soundcore              14600  1 snd
video                  18848  0 
ppdev                  12818  0 
k8temp                 12843  0 
snd_page_alloc         14037  3 snd_atiixp,snd_atiixp_modem,snd_pcm
mac_hid                13038  0 
wmi                    18591  1 hp_wmi
parport_pc             31969  1 
binfmt_misc            17261  1 
lp                     13300  0 
parport                40754  3 ppdev,parport_pc,lp
sdhci_pci              18156  0 
firewire_ohci          35522  0 
sdhci                  27831  1 sdhci_pci
firewire_core          57493  1 firewire_ohci
usb_storage            39351  0 
tg3                   130449  0 
crc_itu_t              12628  1 firewire_core
pata_atiixp            13000  2 
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ sudo iwlist scan
[sudo] password for manuel: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$

---

### Post by praseodym on 2013-02-18
Do you also have a wireless PCI-card (Broadcom)? There is the wrong driver loaded (module **wl**, Broadcom). Load the right one:
```

sudo modprobe -rfv wl
sudo modprobe -v rt2800usb
```
and replug the stick. Maybe
```

sudo rfkill unblock all
rfkill list
```
is needed. Any button/switch/key/key combination?
```

lspci -nnk | grep -iA2 net
```
shows the PCI cards.

---

### Post by seneca2535 on 2013-02-19
Thanks again, It takes too long for the first sudo and I had to kill terminal.
The rest looks like that:manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ sudo modprobe -v rt2800usb
[sudo] password for manuel: 
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ sudo rfkill unblock all
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
    Subsystem: Hewlett-Packard Company MX6125 [103c:308b]
    Kernel driver in use: tg3
--
02:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1356]
    Kernel driver in use: wl
manuel@manuel-HP-Compaq-nx6125-PY418ET-ABE:~$

---

### Post by seneca2535 on 2013-02-19
Thank you very much, I've been fiddling around and following your instructions and I think the problem is SOLVED

---

