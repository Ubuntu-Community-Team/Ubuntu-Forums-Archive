---
title: "new install, no wi-fi"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by alex_oakland on 2012-01-08
I just installed 11.0.4 onto my HP Compaq nx 7300. I upgraded to 11.10. I can get Internet via ethernet, but nothing on wi-fi.

I saw these instructions on a similar post: [paste these commands into terminal, and repost the results here]

cat /etc/lsb-release; uname -a lspci -nnk | grep -iA2 net iwconfig rfkill list all lsmod

here are the results:

cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux delilah-HP-Compaq-nx7300-RM205UT-ABA 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net 
02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Hewlett-Packard Company NX7300 laptop [103c:30a2]
    Kernel driver in use: b44
--
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN [103c:1360]
    Kernel driver in use: b43-pci-bridge


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.




rfkill list all

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[FONT=Verdana]


lsmod

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
bnep                   17923  2 
snd_hda_codec_analog    75090  1 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
b44                    31443  0 
pcmcia                 39822  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ssb                    50682  1 b44
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
wl                   2646601  0 
i915                  505159  3 
psmouse                73673  0 
snd_seq_midi           13132  0 
serio_raw              12990  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_rawmidi            25241  1 snd_seq_midi
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211               14570  1 wl
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 i915
snd                    55902  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core



Thanks for your help.
[/FONT]

---

### Post by lincoln32 on 2012-01-09
try commands lspci and lsusb this will tell us what kind of wifi chip you have and repost the results;)

---

### Post by alex_oakland on 2012-01-09
> **lincoln32 said:**
> try commands lspci and lsusb this will tell us what kind of wifi chip you have and repost the results;)

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by alex_oakland on 2012-01-09
bump

---

### Post by TBABill on 2012-01-09
Looks like you just need to plug into your router via ethernet so you can download drivers. Run the following command: ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Once it runs, just ```
sudo modprobe b43
```Wait a few minutes and then try to connect.

---

### Post by TBABill on 2012-01-09
Just for future reference, your wireless device is a Broadcom BCM4311. From your output: > 10:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

---

### Post by alex_oakland on 2012-01-09
> **TBABill said:**
> Looks like you just need to plug into your router via ethernet so you can download drivers. Run the following command: ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Once it runs, just ```
sudo modprobe b43
```Wait a few minutes and then try to connect.


Thank you. I had the firmware command, but not the 
sudo modprobe b43

Once I ran that, it worked right away.

---

### Post by hjartberg on 2012-10-28
I installed Ubuntu 12.10 on a HP Compaq nx 7300.  I used the code in this thread to get access to wifi. The problem is that every time I restart the computer the wifi disappears and I have to once again write:
```
sudo modprobe b43
```Is there a way to save the settings so I don't have to write code every time I restart the computer?

---

### Post by westie457 on 2012-10-28
Running these commands one line at a time should make the changes permanent

```
sudo su 
 echo b43 >> /etc/modules 
 exit
```

Any problems post back here.

Thank you

---

### Post by hjartberg on 2012-10-28
> **westie457 said:**
> Running these commands one line at a time should make the changes permanent

```
sudo su 
 echo b43 >> /etc/modules 
 exit
```Any problems post back here.

Thank you

It works very well. Thank you.

---

