---
title: "Ubuntu 11.10 RTL8185 Wifi Issues"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by hybridhavoc on 2011-10-23
Last night I installed Kubuntu 11.10 on my Gateway ML3109.  This is using the Realtek 8185 wireless card.  It is not detecting any wireless networks whatsoever.  I have been able to find online many references to people having trouble with this wireless card in the past, but nothing that is similar to the issue I am having with 11.10.

Any assistance would be greatly appreciated.

> 
**lspci**
```

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

> 
**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:03:25:47:5f:d4  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe47:5fd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26680072 (26.6 MB)  TX bytes:1644112 (1.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:f3:9a:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

> 
**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

> 
**lsmod**
```

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rtl8180                35880  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              272785  1 rtl8180
eeprom_93cx6           12653  1 rtl8180
psmouse                73673  0 
cfg80211              172392  2 rtl8180,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
radeon                925020  2 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  4 radeon,ttm,drm_kms_helper
pata_atiixp            12967  2 
i2c_algo_bit           13199  1 radeon
sky2                   49317  0 
ati_agp                13242  0 
```

> 
**dmesg | grep "rtl8180"**
```

[   18.892092] rtl8180 0000:08:09.0: using bridge 0000:00:14.4 INT B to get IRQ 16
[   18.892098] rtl8180 0000:08:09.0: PCI->APIC IRQ transform: INT B -> IRQ 16
```


> 
**lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:47:5f:d4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.2.10 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:d0100000-d0103fff ioport:a000(size=256)
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:f3:9a:bb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=3.0.0-12-generic firmware=N/A latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 ioport:b000(size=256) memory:d0200000-d02001ff
```

> 
**iwlist scan**
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```

> 
**lsb_release -d**
```

Description:    Ubuntu 11.10
```

> 
**uname -mr**
```

3.0.0-12-generic i686
```

> 
**/etc/init.d/networking restart**
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```

---

### Post by hybridhavoc on 2011-10-23
Updated first post with pertinent information.

---

### Post by hero1900 on 2011-10-24
me have same problem and also a friend of mine
from 100 time of trying to connect 1 time will work and it will disconnect after a while 
its a nightmare.

---

### Post by imnotrich on 2011-10-28
The last version of Ubuntu that supported the RTL-8185 was 9.04. 

Debian Lenny supports this card but Squeeze does not. 

The last several versions of Mint and PCLinux OS did not either. 

Meanwhile Puppy has happily supported the RTL-8185 since version 3, so I don't know what the malfunction is with these "major" distros. 

I have an ML-3109 also and typically have it set up as dual boot windows vista (later upgraded to 7) and some version of Linux. 

At one time there was a PPA for Ubuntu but I don't know if there is one for 11.10, that's the version of Ubuntu I am currently struggling with (since it doesn't support the ML-3109's ati video card either, I have to nomodeset acpi=off VGA=792 just to get it to boot. 

"Just works" is a myth. I will be tracking this thread to see if anyone figures out this wireless card.

---

### Post by hybridhavoc on 2011-10-29
As far as I can tell, Realtek just doesn't have a driver that supports this linux kernel.  I had read several instances of people getting it to work with 9.04 but I had no luck with that.  I was also having some USB issues so I ultimately gave up on it for now.  A friend of mine did suggest trying Xubuntu, but I don't see how that would make any particular difference if it's still based on Ubuntu.

By default, it uses the 8180 driver that doesn't work.  I compiled the 8185 driver available on the Realtek site and got it trying to use that but to no avail.  I also tried going the route of using Windows driver through ndiswrapper.  When I was running 7.04 on the same machine several years ago, it was with ndiswrapper.  Still no good though.

I will periodically check on this, since Kubuntu ran significantly better than Windows XP with the exception of the wireless and USB issues.

---

