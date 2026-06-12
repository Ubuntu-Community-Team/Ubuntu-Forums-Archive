---
title: "Intel 5300 on Dell m6400 (10.10)"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by wprecht on 2010-11-21
Hello,

I swapped the wireless card in my m6400 from a Dell 1510 (Broadcom) to an Intel 5300 and I am trying to get it working. Right now it's not coming up at all.  This is a running install of Ubuntu, not a new install, prior to the HW swap the Broadcom worked OK. I've searched all over, but nothing seems to address the specific problem of getting this started.

The laptop is a Dell m6400 with T9800 CPU and 4GB of RAM running 10.10 (2.6.35-22-generic x86_64).

**lspci:**
```
wprecht@LWP-laptop:$ lspci
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
[COLOR=DarkRed]**0c:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300**[/COLOR]

```**ifconfig and iwconfig**
```

wprecht@LWP-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:8a:7b:e4  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe8a:7be4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:580494 (580.4 KB)  TX bytes:155362 (155.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14848 (14.8 KB)  TX bytes:14848 (14.8 KB)

wprecht@LWP-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wprecht@LWP-laptop:~$ 

```[B]Not sure which module is appropriate, so here are all of them:
[/B]```

wprecht@LWP-laptop:~$ lsmod
Module                  Size  Used by
wl                   1965231  0 
lib80211                6175  1 wl
usb_storage            50372  1 
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792856  2 vboxnetadp,vboxnetflt
kvm_intel              49247  0 
kvm                   298550  1 kvm_intel
snd_hda_codec_idt      64667  1 
joydev                 11363  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
iwlagn                202721  0 
iwlcore               146875  1 iwlagn
nvidia              10221046  44 
pcmcia                 40944  0 
mac80211              266657  2 iwlagn,iwlcore
uvcvideo               62379  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
yenta_socket           24279  0 
pcmcia_rsrc            10357  1 yenta_socket
dell_laptop             6722  0 
r852                   11348  0 
sm_common               4441  1 r852
nand                   38430  2 r852,sm_common
nand_ids                4443  1 nand
nand_ecc                4406  1 nand
v4l2_compat_ioctl32    12486  1 videodev
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
mtd                    21479  2 sm_common,nand
dell_wmi                3372  0 
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  6910  1 dell_laptop
video                  22176  0 
intel_agp              32080  0 
psmouse                62080  0 
cfg80211              170293  3 iwlagn,iwlcore,mac80211
serio_raw               4910  0 
output                  2527  1 video
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  1 usbhid
tg3                   135768  0 
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
ahci                   21857  0 
libahci                26167  3 ahci
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci

```[B]This seems to be the relevant portion of the boot messages:
[/B]```

[   16.765523] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   16.942533] ACPI Error (psparse-0537): Method parse/execution failed [\SXX6] (Node ffff88011fc149e0), AE_AML_INFINITE_LOOP
[   16.942557] ACPI Error (psparse-0537): Method parse/execution failed [\SXX5] (Node ffff88011fc14a00), AE_AML_INFINITE_LOOP
[   16.942574] ACPI Error (psparse-0537): Method parse/execution failed [\SXX4] (Node ffff88011fc14a20), AE_AML_INFINITE_LOOP
[   16.942590] ACPI Error (psparse-0537): Method parse/execution failed [\SX11] (Node ffff88011fc14a80), AE_AML_INFINITE_LOOP
[   16.942605] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.AGP_.VID_.LCD_._BCM] (Node ffff88011b63b2a0), AE_AML_INFINITE_LOOP
[   16.942624] ACPI Error: Evaluating _BCM failed (20100428/video-532)
[   16.960535] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.960537] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   16.960594] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.960602] iwlagn 0000:0c:00.0: setting latency timer to 64
[   16.960686] iwlagn 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   16.984824] iwlagn 0000:0c:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x1 < 0x4
[   17.015269] iwlagn 0000:0c:00.0: PCI INT A disabled
[   17.015275] iwlagn: probe of 0000:0c:00.0 failed with error -22

```[B]

lshw -C network:[/B]
```

  *-network UNCLAIMED     
       description: Network controller
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f1ffe000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761e Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:8a:7b:e4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5761e-v3.60 ip=192.168.1.5 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:49 memory:f1be0000-f1beffff memory:f1bf0000-f1bfffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```[B]iwlist scan
[/B]```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

``````

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                              Ignoring unknown interface eth0=eth0.
                                                                                                                             [ OK ]

```Thanks in advance for any help

---

### Post by chili555 on 2010-11-21
> iwlagn 0000:0c:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x1 < 0x4Please see this: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8844035](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8844035)> To explain this a bit; if you get this error, it normally means that you are using an experimental version of the card which was somehow leaked to the public. These cards normally originate from dubious sources like eBay.

I have the same card and the same issue. I contacted an Intel employee to make sure if there is anything that can be done to fix the issue, since the card works perfectly fine under Windows. If there's nothing I can do though, I am planning on sending the person I purchased the laptop from an angry message and demanding a replacement ASAP.I have seen this issue reported a few times; I have not yet seen a solution.

---

### Post by wprecht on 2010-11-22
Crap, I was afraid of that.  I did, in fact, buy it from eBay.  I guess I will drop a line to the vendor.

---

