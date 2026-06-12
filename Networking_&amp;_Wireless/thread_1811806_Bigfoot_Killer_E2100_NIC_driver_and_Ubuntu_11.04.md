---
title: "Bigfoot Killer E2100 NIC driver and Ubuntu 11.04"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by jlcb03 on 2011-07-25
Does anybody know where to find Ubuntu drivers for Bigfoot Killer E2100 NIC?

---

### Post by wildmanne39 on 2011-07-25
Hi, run these commands in a terminal please
```
sudo lshw -C network
``` 
```
lspci -nn
```
```
ifconfig
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by jlcb03 on 2011-07-25
Thanks for your response. The output to the commands is the following:

```
sudo lshw -C network

PCI(sysfs)
```
```
lspci -nn

...
06:00.0 "Power PC" "Freescale Semiconductor Inc" "Device c006" -r10 "Bigfoot Networks, Inc." "Device 1201"

```
```
ifconfig

(only the loopback interface appears)
```
```
lsmod

Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  4 
usblp                  18233  0 
snd_usb_audio         112426  2 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_intel          33211  0 
binfmt_misc            17565  1 
snd_hda_codec         103804  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_ctxfi             105792  2 
nvidia              10709116  38 
snd_pcm                96625  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  20 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_hda_intel,snd_ctxfi,snd_pcm
i7core_edac            27903  0 
serio_raw              13166  0 
joydev                 17606  0 
xhci_hcd               77643  0 
edac_core              53845  1 i7core_edac
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  3 
libahci                26642  1 ahci

```

I just upgraded my computer from an Intel q9650 to a i7 970 with a Gigabyte G1.Sniper motherboard **without reinstalling** Ubuntu.

---

### Post by wildmanne39 on 2011-07-25
Hi, is that the only output of this command ```
lspci -nn
```
I was expecting to see more.

---

### Post by jlcb03 on 2011-07-26
> **wildmanne39 said:**
> Hi, is that the only output of this command ```
lspci -nn
```
I was expecting to see more.

Yes, you're right. The output of this command are several lines with info about devices in my system. I've summarized them with the line "**...**", because only the last line gives information about the network card. Do you need the info about other devices in my computer?

---

### Post by wildmanne39 on 2011-07-26
Hi, yes please I did not see the information I need to help you.

---

### Post by jlcb03 on 2011-07-26
> **wildmanne39 said:**
> Hi, yes please I did not see the information I need to help you.

Ok. The full output from the "lspci -nn" command is the following:

```
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
00:10.0 PIC [0800]: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13)
00:10.1 PIC [0800]: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13)
00:11.0 PIC [0800]: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 [8086:3427] (rev 13)
00:11.1 PIC [0800]: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 [8086:3428] (rev 13)
00:13.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller [8086:342d] (rev 13)
00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:15.0 PIC [0800]: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers [8086:342f] (rev 13)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
01:00.0 SATA controller [0106]: Marvell Technology Group Ltd. Device [1b4b:9182] (rev 10)
02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
03:00.0 VGA compatible controller [0300]: nVidia Corporation GF110 [Geforce GTX 580] [10de:1080] (rev a1)
03:00.1 Audio device [0403]: nVidia Corporation GF110 High Definition Audio Controller [10de:0e09] (rev a1)
05:00.0 Audio device [0403]: Creative Labs X-Fi Titanium series [EMU20k2] [1102:000b] (rev 03)
06:00.0 Power PC [0b20]: Freescale Semiconductor Inc Device [1957:c006] (rev 10)
```

I'm regretting for buying my new motherboard (Gigabyte G1.Sniper). The integrated NIC is very good for gaming under Windows but it's incredible that there's no support for it under Linux. The manufacturer (Bigfoot networks, [http://www.bigfootnetworks.com](http://www.bigfootnetworks.com)) should care more about his customers.

---

### Post by wildmanne39 on 2011-07-26
Deleted

---

### Post by wildmanne39 on 2011-07-26
Hi, I have been researching this and I had a friend help me that is the expert and he came up with nothing also because we can not find the driver you need. It will most likely have support in later versions of ubunbtu.

I am sorry we can not get this working for you.

---

### Post by jlcb03 on 2011-07-26
> **wildmanne39 said:**
> Hi, I have been researching this and I had a friend help me that is the expert and he came up with nothing also because we can not find the driver you need. It will most likely have support in later versions of ubunbtu.

I am sorry we can not get this working for you.

It's a modern hardware so I think it will take time to get it working in Ubuntu. 

Anyway, thanks for your help and time!.

---

### Post by wildmanne39 on 2011-07-26
Hi, your welcome!

---

