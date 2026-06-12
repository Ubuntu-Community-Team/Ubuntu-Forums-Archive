---
title: "eth0 is missing"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by johnno56 on 2013-03-31
I have recently install 12.10 and have come across a networking problem - I think.

To start with, I have been running with Ubuntu since 8.04 until 10.04 without any networking problems.

I have a suspicion that 12.10 does not have my onboard ethernet drivers installed. I dropped in a Realtek PCI ethernet card and it connected without any problems. Removed the card and reconnected to the onboard ethernet connection and I have no internet connection... no surprises there...

I used the "sudo lshw -class network" command and it came back with the following:

john@baldwin-johna:~$ sudo lshw -class network
[sudo] password for john: 
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 00
       serial: 00:20:18:2a:82:95
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.10.10 latency=0 multicast=yes
       resources: irq:17 ioport:d000(size=32)
  *-network UNCLAIMED
       description: Ethernet controller
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d3ffff ioport:c000(size=128)
john@baldwin-johna:~$ 

The onboard ethernet connection shows as "Unclaimed" with no "Product" or "Vendor" details.

My MB is a Gigabyte H77-D3H and according to the files on the DVD, the ethernet drivers are either Atheros 813x or 815x

Any advice would be appreciated.

Thanking you in advance.

J

---

### Post by praseodym on 2013-04-01
Pleas show:
```

lspci -nnk | grep -iA2 net
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by johnno56 on 2013-04-01
Praseodym,

Thank you for replying. I hope the information below will be helpful.

Regards

J

ps: At the moment, I am using the Realtek PCI card, as the motherboard connection does not work.

```
--------------------------------------------

john@baldwin-johna:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8029(AS) [10ec:8029]
	Kernel driver in use: ne2k-pci
	Kernel modules: ne2k-pci
05:00.0 Ethernet controller [0200]: Device [3f6b:1083] (rev c0)
	Subsystem: Device [5c79:eb30]
06:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
john@baldwin-johna:~$

----------------------------------------

john@baldwin-johna:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12649  1 
parport_pc             31969  0 
ppdev                  12818  0 
bnep                   17708  2 
rfcomm                 37277  0 
bluetooth             183270  10 bnep,rfcomm
binfmt_misc            17261  1 
vesafb                 13478  1 
snd_hda_codec_hdmi     31457  2 
snd_hda_codec_via      45644  1 
snd_usb_audio         105029  1 
snd_usbmidi_lib        24211  1 snd_usb_audio
coretemp               13169  0 
kvm                   357807  0 
aesni_intel            17939  0 
cryptd                 15615  1 aesni_intel
aes_i586               16996  1 aesni_intel
microcode              18210  0 
snd_hda_intel          32516  5 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13273  2 snd_usb_audio,snd_hda_codec
snd_pcm                80235  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  3 snd_seq_midi,snd_seq_midi_event
gspca_sonixj           32257  0 
gspca_main             27627  1 gspca_sonixj
videodev               95842  1 gspca_main
video                  18895  0 
snd_timer              24412  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13038  0 
psmouse                84878  0 
serio_raw              13032  0 
fglrx                2917043  123 
mei                    35797  0 
snd                    62146  25 snd_hda_codec_hdmi,snd_hda_codec_via,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16926  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
ahci                   25497  2 
libahci                25938  1 ahci
ne2k_pci               13390  0 
8390                   18337  1 ne2k_pci
john@baldwin-johna:~$

---------------------------------

john@baldwin-johna:~$ cat /etc/udev/rules.d/70-persistent-net.rules

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.6/0000:05:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:ce:e3:0a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/0000:04:00.0 (ne2k-pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:20:18:2a:82:95", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
john@baldwin-johna:~$
```

---

### Post by praseodym on 2013-04-01
eth0 is the name of the Realtek-device, the driver of the Atheros device is not loaded:
```

sudo modprobe -v atl1c
ifconfig -a
```

---

### Post by johnno56 on 2013-04-01
Praseodym,

Results of commands. Will attempt connection and get back to you.

Regards

J

```
john@baldwin-johna:~$ sudo modprobe -v atl1c
[sudo] password for john: 
insmod /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko 
john@baldwin-johna:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:20:18:2a:82:95  
          inet addr:192.168.10.10  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::220:18ff:fe2a:8295/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:554 errors:169 dropped:0 overruns:0 carrier:336
          collisions:2913 txqueuelen:1000 
          RX bytes:456154 (456.1 KB)  TX bytes:121450 (121.4 KB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15833 (15.8 KB)  TX bytes:15833 (15.8 KB)

john@baldwin-johna:~$
```

---

### Post by johnno56 on 2013-04-01
Praseodym,

MB connection does not work yet. Did I do anything wrong?

J

---

### Post by utkjamie on 2013-06-25
Was this ever resolved? I have the same problem, similar card.

---

