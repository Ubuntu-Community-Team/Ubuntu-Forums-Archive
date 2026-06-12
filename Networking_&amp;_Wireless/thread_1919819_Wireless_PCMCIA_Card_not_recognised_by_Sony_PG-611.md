---
title: "Wireless PCMCIA Card not recognised by Sony PG-6116 with 11.10"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by dckidd on 2012-02-03
Can someone please help, my PCMCIA card (EDIMAX EW-7108PCg) which worked perfectly with Ubuntu 9.x in my laptop (SONY PG-6116) no longer works since I wiped 9 and installed 11.10.

It doesn't seem to recognise the card at all, though when I stick it in another laptop (A Dell with a currently broken inbuilt Broadcom wireless) it lights up just fine. 

I have provided the information from the howto, though I have no idea what much of it means, I only hope someone out there does and can spot something simple.

lspci
-----

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0056 Sony Corp. MG Memory Stick Reader/Writer


lsusb
-----

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0056 Sony Corp. MG Memory Stick Reader/Writer

lspci -nn (I put the whole lot here as I didn't want to miss anything)
---------
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 11)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82815 Chipset Graphics Controller (CGC) [8086:1132] (rev 11)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BAM ISA Bridge (LPC) [8086:244c] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BAM IDE U100 Controller [8086:244a] (rev 03)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 03)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801BA/BAM AC'97 Modem Controller [8086:2446] (rev 03)
01:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) [104c:8021] (rev 02)
01:02.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c475 [1180:0475] (rev 80) 
01:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)


ifconfig -- only shows wired network eth0 and lo

iwconfig 
--------
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod
-----

Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
i810                   22857  3 
i915                  509487  0 
drm_kms_helper         32889  1 i915
drm                   192194  6 i810,i915,drm_kms_helper
joydev                 17393  0 
i2c_algo_bit           13199  1 i915
ppdev                  12849  0 
snd_intel8x0           33318  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
snd                    55902  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
pcmcia                 39822  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
intel_rng              12700  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
firewire_sbp2          18414  0 
sony_laptop            39681  0 
parport_pc             32114  1 
shpchp                 32356  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  0 
firewire_ohci          35854  0 
e100                   36289  0 
firewire_core          56937  2 firewire_sbp2,firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60310  0 

dmesg 
-----

nothing wireless related except...

[ 1794.712082] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0

when I plug the card in

sudo lshw -C network 
--------------------

only reports about wired network

iwlist scan
-----------
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

lsb_release
-----------
Description:	Ubuntu 11.10

uname -mr
---------

3.0.0-15-generic i686

sudo /etc/init.d/networking restart
-----------------------------------
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

---

### Post by praseodym on 2012-02-03
Hi,

please show

```
pccardctl info
iwconfig
rfkill list
```

---

### Post by dckidd on 2012-02-03
Hi, wow that was quick...

pccardctl info

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.


rfkill list

<returns nothing>


I appreciate the help.

---

### Post by praseodym on 2012-02-03
IMHO the (normally needed) driver rt2500pci is no longer part of the kernel (and also part of "linux-wireless", respectively)?! Try ndiswrapper with the windows XP driver. Ndiswrapper 1.56 makes some trouble, so you better compile the latest stable 1.57 on your own:

[http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113](http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113)

---

