---
title: "no wireless on desktop with realtek 8190"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by le_vainqueur on 2011-03-12
I have a new desktop with 10.10 installed.  I have a realtek 8190 PCI wireless card. The manufacturer and model number are: Filemate 3FMPCIMWN-R.  Everything seems to work well in Windows 7, so I know the hardware is fine, but there is no wireless in Ubuntu 10.10.

According to some posts I found in the forum, I tried to install the driver using ndisgtk, but it didn't seem to have an effect.  Nothing else I could find in my searches seemed to be relevant.

After playing around for a bit, I reinstalled 10.10 to have a clean slate while trying to fix the problem.  I would appreciate any help or guidance
======================

Using the command
> lspci -v | lessI get the following relevant info:

> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 51
        I/O ports at c800 [size=256]
        Memory at f3fff000 (64-bit, prefetchable) [size=4K]
        Memory at f3ff8000 (64-bit, prefetchable) [size=16K]
        Expansion ROM at f7ee0000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

07:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190
        Subsystem: Realtek Semiconductor Co., Ltd. Device 8190
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at e800 [size=256]
        Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>


From > lspci
> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
07:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190


From > ifconfig
> eth0      Link encap:Ethernet  HWaddr 20:cf:30:cc:8f:91  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fecc:8f91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4766240 (4.7 MB)  TX bytes:389096 (389.0 KB)
          Interrupt:51 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


From > iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.


from > lsmod
> odule                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22299  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
nouveau               518076  2 
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56825  1 nouveau
drm_kms_helper         30200  1 nouveau
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                59033  0 
drm                   168732  4 nouveau,ttm,drm_kms_helper
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7342  0 
soundcore                880  1 snd
agpgart                32075  2 ttm,drm
serio_raw               4022  0 
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  1 nouveau
asus_atk0110           11423  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21554  0 
r8169                  36777  0 
firewire_core          46675  1 firewire_ohci
usbhid                 36978  0 
hid                    67742  1 usbhid
crc_itu_t               1383  1 firewire_core
mii                     4425  1 r8169
pata_jmicron            1855  0 


Nothing was returned from > dmesg | grep "wlan_module_name"

from > sudo lshw -C network

>  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 20:cf:30:cc:8f:91
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:51 ioport:c800(size=256) memory:f3fff000-f3ffffff memory:f3ff8000-f3ffbfff memory:f7ee0000-f7eeffff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:07:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:f7ffe000-f7ffefff


from > iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


from > sudo /etc/init.d/networking restart

>  * Reconfiguring network interfaces...                                                                                                                                                    Ignoring unknown interface eth0=eth0.
                                                                                                                                                                                   [ OK ]

---

### Post by bkratz on 2011-03-12
Well from what I see in this thread you may have to use ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=1606676](http://ubuntuforums.org/showthread.php?t=1606676)

Hopefully, your card came with inf and sys files compatible with XP, windows 7 drivers will usually not work with ndiswrapper.

---

