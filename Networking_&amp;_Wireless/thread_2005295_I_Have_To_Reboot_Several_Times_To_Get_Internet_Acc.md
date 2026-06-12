---
title: "I Have To Reboot Several Times To Get Internet Access"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by Precipitous on 2012-06-17
I am running a fresh install of Ubuntu 12.04 and am using an Arris cable modem and a Belkin router (I am plugging into it, not using wireless). When I have Internet access it works very well. Unfortunately, anytime I have to reboot my computer I end up having to do it several times before I am able to connect to again...  I have already ruled out any problems with my cable modem (I had it replaced), my router (I have tested with and without it) and my network card (I replaced it).

I need help desperately! 

Here are the results of some basic informational commands:

lspci:
```
$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1)
04:05.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone]
```lsub:
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 043d:00f2 Lexmark International, Inc. 
Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
```ifconfig:
```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:10:4b:68:86:8f  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::210:4bff:fe68:868f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30907420 (30.9 MB)  TX bytes:11961630 (11.9 MB)
          Interrupt:17 Base address:0x8f80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:661371 (661.3 KB)  TX bytes:661371 (661.3 KB)
```lsmod:
```
$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
nfnetlink_queue        17557  3 
nfnetlink              13983  4 nfnetlink_queue
nf_conntrack_ipv4      19084  3 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  3 
nf_conntrack           73847  2 nf_conntrack_ipv4,xt_state
xt_mark                12499  6 
xt_NFQUEUE             12630  3 
xt_iprange             12485  2 
xt_tcpudp              12531  11 
ipt_REJECT             12512  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
binfmt_misc            17292  1 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nvidia              10987747  40 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter         12706  1 
usbhid                 41906  0 
dcdbas                 14098  0 
hid                    77367  1 usbhid
ip_tables              18106  1 iptable_filter
x_tables               21974  8 xt_state,xt_mark,xt_NFQUEUE,xt_iprange,xt_tcpudp,ipt_REJECT,iptable_filter,ip_tables
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                72919  0 
serio_raw              13027  0 
lp                     17455  0 
mac_hid                13077  0 
parport                40930  3 parport_pc,ppdev,lp
3c59x                  37445  0 

```sudo lshw -C network:
```
$ sudo lshw -C network
[sudo] password for gslater: 
  *-network               
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: eth1
       version: 00
       serial: 00:10:4b:68:86:8f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.2 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:dc80(size=128) memory:dcdfff80-dcdfffff memory:dce00000-dce1ffff

```

---

### Post by Precipitous on 2012-06-19
This was resolved by wiping my hard drive and re-installing Ubuntu 12.04 from scratch...

---

