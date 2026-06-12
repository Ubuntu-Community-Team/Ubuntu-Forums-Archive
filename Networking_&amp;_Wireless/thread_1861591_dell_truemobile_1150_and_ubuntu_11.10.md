---
title: "dell truemobile 1150 and ubuntu 11.10"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by Henk506 on 2011-10-15
here is the scoop, i have a dell inspiron 1100 running ubuntu 11.10 with no wireless, i have a dell truemobile 1150 pccard.  i need to get the truemobile card to work with the laptop.  how can i do this.  thanks in advance

---

### Post by Henk506 on 2011-10-15
Does anyone have an answer!!! please

---

### Post by wildmanne39 on 2011-10-15
Hi, please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Henk506 on 2011-10-16
here you are
also i need it to work with an open school network
it reads the existance but will not connect. it keeps trying but never seems to make it
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
	Subsystem: Dell Device [1028:0149]
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
	Subsystem: Intel Corporation Device [8086:24c0]
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
	Subsystem: Intel Corporation Device [8086:24c0]
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
	Subsystem: Intel Corporation Device [8086:24c0]
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
	Subsystem: Intel Corporation Device [8086:24c0]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
	Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
	Subsystem: Intel Corporation Device [8086:24c0]
	Kernel driver in use: ata_piix
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
	Subsystem: Dell Device [1028:0149]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
	Subsystem: Broadcom Corporation Device [14e4:4d64]
	Kernel modules: snd-intel8x0m
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
	Subsystem: Device [0149:1028]
	Kernel driver in use: b44
	Kernel modules: b44
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
	Subsystem: Dell Device [1028:0149]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
	Subsystem: Device [0149:1028]
	Kernel driver in use: b44

---

### Post by praseodym on 2011-10-16
Please show additionally:

```
lsusb
lsmod
pccardctl info
```

---

### Post by Henk506 on 2011-10-16
connor@OmegaThief:~$ netdev
netdev: command not found
connor@OmegaThief:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
connor@OmegaThief:~$ lsmod
Module                  Size  Used by
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                70112  1 orinoco_cs
cfg80211              172392  1 orinoco
nls_utf8               12493  1 
udf                    83826  1 
crc_itu_t              12627  1 udf
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
joydev                 17393  0 
8139too                23283  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
pcmcia                 39822  1 orinoco_cs
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
psmouse                73673  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
i915                  505108  0 
drm_kms_helper         32889  1 i915
drm                   192226  2 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
binfmt_misc            17292  1 
b44                    31443  0 
ssb                    50682  1 b44
connor@OmegaThief:~$ pccardctl info
PRODID_1="Dell"
PRODID_2="TrueMobile 1150 Series PC Card"
PRODID_3="Version 01.01"
PRODID_4=""
MANFID=0156,0002
FUNCID=6
connor@OmegaThief:~$ AA
here you are

---

### Post by praseodym on 2011-10-16
Ok, its an Orinoco chipset it only works with WEP or WPA, not with WPA2. Check additionally:

```
dmesg | egrep 'ori|wlan'
```

---

### Post by Henk506 on 2011-10-16
connor@OmegaThief:~$ dmesg | egrep 'ori|wlan'
[    0.124738] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[   16.009071] Adding 514044k swap on /dev/sda5.  Priority:-1 extents:1 across:514044k 
[  803.113687] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[  803.196187] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[  803.196297] orinoco_cs 0.0: Station identity  001f:0001:0006:000a
[  803.196304] orinoco_cs 0.0: Firmware determined as Lucent/Agere 6.10
[  803.560098] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[  803.560233] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[  803.560239] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[  803.560244] orinoco_cs 0.0: Ad-hoc demo mode supported
[  803.560247] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[  803.560251] orinoco_cs 0.0: WEP supported, 104-bit key
[  803.560255] orinoco_cs 0.0: WPA-PSK supported
connor@OmegaThief:~$ 
here you go
by the way are there any drivers i need to download to get this fully working

---

### Post by Henk506 on 2011-10-17
by the way the card tries to connect to a unprotected network with no wireless security ant thinks that there is a code how do i fix this and what drivers do i need

---

### Post by praseodym on 2011-10-17
The orinoco driver is loaded. Try a shorter key without cryptic letters in it:

```
[ 803.560251] orinoco_cs 0.0: WEP supported, 104-bit key
[ 803.560255] orinoco_cs 0.0: WPA-PSK supported
```

---

### Post by Henk506 on 2011-10-17
> **praseodym said:**
> The orinoco driver is loaded. Try a shorter key without cryptic letters in it:

```
[ 803.560251] orinoco_cs 0.0: WEP supported, 104-bit key
[ 803.560255] orinoco_cs 0.0: WPA-PSK supported
```

ok then why can it never seem to finish connecting to a open network and hangs.  any ideas there.

---

