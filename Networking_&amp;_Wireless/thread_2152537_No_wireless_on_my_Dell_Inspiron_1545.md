---
title: "No wireless on my Dell Inspiron 1545"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by karan093 on 2013-06-08
I have installed ubuntu 12.10 on my Dell inpiron 1545. My wireless does not seem to be working. Here's the snapshot 


[ATTACH=CONFIG]243646[/ATTACH]

I dont see any wireless option on there. I have googled enough and this seems to be my last resort. Since not much familiar with the command line tool of ubuntu, kindly take me through it step by step. I'll keep updating.

Also, I tried[COLOR=#000000] > [/COLOR][COLOR=#000000]sudo lshw -C network[/COLOR][COLOR=#000000] and the output is

[/COLOR]sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:34:46:d2
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f69fc000-f69fffff ioport:de00(size=256)


Kindly help.

---

### Post by benzarti on 2013-06-08
for knowing the wifi card do:
lspci | grep -i network
it must be Broadcom BCM4312, then look for the driver and install it

---

### Post by karan093 on 2013-06-08
[COLOR=#000000]lspci | grep -i network

It does not output anything.[/COLOR]

---

### Post by benzarti on 2013-06-08
Check in the bios for a hardware switch like "Wireless enabled".

---

### Post by karan093 on 2013-06-08
How do I do that?

---

### Post by karan093 on 2013-06-08
So i restarted and wireless enable was already checked in BIOS.

---

### Post by benzarti on 2013-06-08
Restart the computer. At the very beginning you must see press  "F2 to enter setup" and then change the option CAREFULLY.

---

### Post by benzarti on 2013-06-08
Other hardware switch is with fn key. Check the manual of your laptop on how to enable/disable Wifi with the fn key.

---

### Post by praseodym on 2013-06-08
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
pccardctl info
lsmod
iwconfig
rfkill list
```

---

### Post by tyar on 2013-06-08
check uncheck enable networking.. usually Broadcom need u to install d driver manually [http://packages.debian.org/squeeze/all/broadcom-sta-common/download](http://packages.debian.org/squeeze/all/broadcom-sta-common/download)

---

### Post by ahallubuntu on 2013-06-08
~

---

### Post by karan093 on 2013-06-08
karan@karan-Inspiron-1545:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: sky2
karan@karan-Inspiron-1545:~$ lsusb
Bus 001 Device 004: ID 0c45:63ee Microdia 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 003: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 003 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
karan@karan-Inspiron-1545:~$ pccardctl info
karan@karan-Inspiron-1545:~$ lsmod
Module                  Size  Used by
ppp_deflate            12807  0 
zlib_deflate           26446  1 ppp_deflate
bsd_comp               12786  0 
ppp_async              17206  1 
crc_ccitt              12628  1 ppp_async
option                 25745  3 
usb_wwan               19467  1 option
usbserial              36712  9 option,usb_wwan
pci_stub               12551  1 
vboxpci                22897  0 
vboxnetadp             25637  0 
vboxnetflt             27262  0 
vboxdrv               252271  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             31969  0 
rfcomm                 37277  12 
ppdev                  12818  0 
bnep                   17708  2 
ext2                   67205  1 
joydev                 17162  0 
btusb                  17987  0 
coretemp               13169  0 
bluetooth             183270  22 rfcomm,bnep,btusb
snd_hda_codec_idt      59762  1 
dell_wmi               12602  0 
sparse_keymap          13659  1 dell_wmi
gpio_ich               13160  0 
dell_laptop            17162  0 
dcdbas                 14055  1 dell_laptop
microcode              18210  0 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
psmouse                89552  0 
serio_raw              13032  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13038  0 
wmi                    18591  1 dell_wmi
snd                    62146  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  461452  3 
lpc_ich                16926  0 
soundcore              14600  1 snd
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
ums_realtek            17670  0 
usb_storage            39351  1 ums_realtek
ahci                   25497  2 
libahci                25938  1 ahci
sky2                   52927  0 
karan@karan-Inspiron-1545:~$ iwconfig
ppp0      no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.


karan@karan-Inspiron-1545:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
karan@karan-Inspiron-1545:~$

---

### Post by praseodym on 2013-06-08
Did you mean "wireless" or "UMTS"? There is no wireless card visible. Try a BIOS reset to default settings.

The USB-UMTS-stick is currently in modem-mode.

---

