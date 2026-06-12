---
title: "WEP failure with 11.4 - Intel 2200BG"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by nbxmike on 2011-09-24
I am trying to get a WEP link working on a Dell Inspiron 9300.  Following the advice of several posts/threads, I have tried network manager, manual config and most recently wicd.  I have confirmed that network-manager was actually removed.  At least Wicd finally reported "BAD PASSWORD" which is more than network-manager ever reported, and yes the key is correct.  As way of diagnostic, here are the outputs of a couple of tools.

sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:12:3f:d6:71:b5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.44 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:dfcfe000-dfcfffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth0
       version: 05
       serial: 00:12:f0:75:1f:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfcfd000-dfcfdfff

iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

The link worked under Fedora before I installed Ubuntu.  I use the same USB drive to pass the key between machines, and it works on other systems.  I installed from an i386 alternate install CD.

Any help would be appreciated.

---

### Post by nbxmike on 2011-09-25
Additional diag info if anyone could help

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:12:f0:75:1f:b6  
          inet6 addr: fe80::212:f0ff:fe75:1fb6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3464 (3.4 KB)
          Interrupt:17 Base address:0x2000 Memory:dfcfd000-dfcfdfff 


 sudo lsmod
[sudo] password for mike: 
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
radeon                900494  3 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ipw2200               145664  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
libipw                 46641  1 ipw2200
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
cfg80211              156212  2 ipw2200,libipw
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lib80211               14570  2 ipw2200,libipw
pcmcia                 39671  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
joydev                 17322  0 
i2c_algo_bit           13184  1 radeon
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
serio_raw              12990  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
dell_laptop            13515  0 
video                  18951  0 
dcdbas                 14054  1 dell_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
b44                    35301  0 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
ssb                    45942  1 b44
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core


 dmesg | grep "ipw2200"
[   16.176817] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.176821] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.176932] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.176997] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.514822] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


I'd be glad to collect anything else if anyone has an idea . . .

---

### Post by nbxmike on 2011-09-26
New information -
 
Added Ubuntu 11.04 AMD64 to an Acer with BCM4612 - works fine with WEP on the same router, same key.
 
Inspiron 9300 w/ Intel 2200BG on WPA2-Enterprise with PEAP and WPA2-Personal works fine (two other locations I visit.)
 
So to me it seems that the fault lies in the ipw2200 / encryption level; can someone point me to what needs to be diagnosed?

---

### Post by nbxmike on 2011-11-07
After trying all the suggestions, I bought an Atheros card off E-Bay.  It works with every operating system including Ubuntu!

Thanks

---

