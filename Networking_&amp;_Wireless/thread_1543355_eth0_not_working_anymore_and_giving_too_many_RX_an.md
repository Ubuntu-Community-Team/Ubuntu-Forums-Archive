---
title: "eth0 not working anymore and giving too many RX and TX"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by chosenperfect on 2010-07-31
hi, i just got my wireless network working, after compiling AR81WLAN driver from Atheros website..
and now my wired network not working and giving too many RX and TX everytime i use ifconfig commands here's the output from 

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:af:78:22  
          inet addr:192.168.10.31  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4199266833732810 errors:25195626772200630 dropped:8398542257400210 overruns:4199271128700105 frame:20996355643500525
          TX packets:4199271128700105 errors:16797084514800420 dropped:0 overruns:4199271128700105 carrier:8398542257400210
          collisions:20996355643500525 txqueuelen:1000 
          RX bytes:4199271128700105 (4.1 PB)  TX bytes:4199271128700105 (4.1 PB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:356208 (356.2 KB)  TX bytes:356208 (356.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.24.14.128  P-t-P:192.168.11.32  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:591621 errors:5 dropped:0 overruns:0 frame:0
          TX packets:573322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:487441822 (487.4 MB)  TX bytes:144867059 (144.8 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:38:29:2a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


ifconfig -a # again
```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:af:78:22  
          inet addr:192.168.10.31  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4205241133240155 errors:25231472569244700 dropped:8410490856414900 overruns:4205245428207450 frame:21026227141037250
          TX packets:4205245428207450 errors:16820981712829800 dropped:0 overruns:4205245428207450 carrier:8410490856414900
          collisions:21026227141037250 txqueuelen:1000 
          RX bytes:4205245428207450 (4.2 PB)  TX bytes:4205245428207450 (4.2 PB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:356694 (356.6 KB)  TX bytes:356694 (356.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.24.14.128  P-t-P:192.168.11.32  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:593168 errors:5 dropped:0 overruns:0 frame:0
          TX packets:574846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:488834348 (488.8 MB)  TX bytes:145230135 (145.2 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:38:29:2a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lspci -v
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 3110 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, fast devsel, latency 0
        Memory at e2400000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 30e0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 30c0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at e4505c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e4500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e3500000-e44fffff
        Prefetchable memory behind bridge: 00000000e0400000-00000000e13fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: e2500000-e34fffff
        Prefetchable memory behind bridge: 00000000e1400000-00000000e23fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 30a0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 3080 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 3060 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 3040 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at e4505800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
        I/O ports at 3108 [size=8]
        I/O ports at 311c [size=4]
        I/O ports at 3100 [size=8]
        I/O ports at 3118 [size=4]
        I/O ports at 3020 [size=32]
        Memory at e4505000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: medium devsel, IRQ 11
        Memory at e4506000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 3000 [size=32]
        Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: fast devsel, IRQ 11
        Memory at e4504000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
        Subsystem: Intel Corporation Device 1301
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at e3500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
        Subsystem: Acer Incorporated [ALI] Device 0229
        Flags: fast devsel, IRQ 28
        Memory at e2500000 (64-bit, non-prefetchable) [disabled] [size=256K]
        I/O ports at 1000 [disabled] [size=128]
        Capabilities: <access denied>
        Kernel driver in use: atheros_eth
        Kernel modules: atl1c, atl1e

```

dmesg | grep eth # after few /etc/init.d/networking restart
```

[   12.960106] atheros_eth 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.960118] atheros_eth 0000:02:00.0: setting latency timer to 64
[   14.051120] atheros_eth 0000:02:00.0: irq 28 for MSI/MSI-X
[   14.141171] ADDRCONF(NETDEV_UP): eth0: link is not ready
[40719.011563] atheros_eth 0000:02:00.0: MAC state machine cann't be idle since disabled for 10ms second
[40721.667431] atheros_eth 0000:02:00.0: irq 28 for MSI/MSI-X
[40722.060057] atheros_eth 0000:02:00.0: stop mac failed
[40722.130232] atheros_eth 0000:02:00.0: Error enable PHY linkChange Interrupt
[40722.130307] atheros_eth 0000:02:00.0: Error get phy ID
[40722.131814] ADDRCONF(NETDEV_UP): eth0: link is not ready
[40738.680079] atheros_eth 0000:02:00.0: MAC state machine cann't be idle since disabled for 10ms second
[40739.235274] atheros_eth 0000:02:00.0: irq 28 for MSI/MSI-X
[40739.630250] atheros_eth 0000:02:00.0: stop mac failed
[40739.700442] atheros_eth 0000:02:00.0: Error enable PHY linkChange Interrupt
[40739.700512] atheros_eth 0000:02:00.0: Error get phy ID
[40739.702018] ADDRCONF(NETDEV_UP): eth0: link is not ready
[41147.750177] atheros_eth 0000:02:00.0: MAC state machine cann't be idle since disabled for 10ms second
[41274.734655] atheros_eth 0000:02:00.0: irq 28 for MSI/MSI-X
[41275.130075] atheros_eth 0000:02:00.0: stop mac failed
[41275.200253] atheros_eth 0000:02:00.0: Error enable PHY linkChange Interrupt
[41275.200322] atheros_eth 0000:02:00.0: Error get phy ID
[41275.201979] ADDRCONF(NETDEV_UP): eth0: link is not ready
[41616.730259] atheros_eth 0000:02:00.0: MAC state machine cann't be idle since disabled for 10ms second
[41618.864544] atheros_eth 0000:02:00.0: irq 28 for MSI/MSI-X
[41619.260261] atheros_eth 0000:02:00.0: stop mac failed
[41619.330429] atheros_eth 0000:02:00.0: Error enable PHY linkChange Interrupt
[41619.330498] atheros_eth 0000:02:00.0: Error get phy ID
[41619.332009] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

lsmod
```

Module                  Size  Used by
ppp_deflate             4426  0 
zlib_deflate           21834  1 ppp_deflate
bsd_comp                5283  0 
ppp_async               8174  1 
crc_ccitt               1675  1 ppp_async
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
xt_tcpudp               2667  2 
ipt_MASQUERADE          1863  1 
iptable_mangle          3315  0 
iptable_nat             5219  1 
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_conntrack           73966  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_filter          2791  0 
ip_tables              18390  3 iptable_mangle,iptable_nat,iptable_filter
x_tables               22461  4 xt_tcpudp,ipt_MASQUERADE,iptable_nat,ip_tables
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279040  1 
btusb                  12969  0 
bluetooth              58685  1 btusb
i915                  321160  3 
snd_hda_intel          25677  4 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
joydev                 11072  0 
snd_pcm                87882  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
drm_kms_helper         30742  1 i915
snd_seq_dummy           1782  0 
arc4                    1473  2 
drm                   199204  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
snd_seq_oss            31219  0 
option                 19050  1 
snd_seq_midi            5829  0 
uvcvideo               62467  0 
acer_wmi               15829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
psmouse                64576  0 
serio_raw               4918  0 
usbserial              39131  4 option
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
iwlagn                121641  0 
iwlcore               124955  1 iwlagn
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  20623  1 i915
atl1c                  32975  0 
intel_agp              29095  2 i915
snd                    71106  20 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              238448  2 iwlagn,iwlcore
atl1e                  69846  0 
soundcore               8052  1 snd
led_class               3764  2 acer_wmi,iwlcore
cfg80211              148546  3 iwlagn,iwlcore,mac80211
output                  2503  1 video
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
jfs                   184920  11 
usbhid                 41084  0 
hid                    83440  1 usbhid
ahci                   37870  14 

```

cat /etc/network/interfaces 
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.10.31
        broadcast 192.168.10.255
        network 192.168.10.0
        netmask 255.255.255.0

```


sudo /etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                                                                                                                                                          RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 17759

```

i have tried to bring down and up the eth0 using sudo ifconfig eth0 down (and up) but it seems not working at all..

could anyone kind enough to help me ^^ thanks for reading this thread..

---

### Post by chosenperfect on 2010-07-31
it's working now, after 2x restart T_T thanks all

---

### Post by chosenperfect on 2010-08-02
still, it's send and receive 1.3GB/s after few hours.. >_< i don't know what's wrong with my eth0 T____T

---

### Post by marc.verwerft on 2010-08-02
> hi, i just got my wireless network working, after compiling AR81WLAN driver from Atheros website..
Strange, your lspci says that it uses the iwlagn driver - maybe there is a conflict somewhere?

Regards,

Marc

---

### Post by Iowan on 2010-08-02
Although you shouldn't argue with success...
Have you tried configuring a static address via Network Manager?

---

