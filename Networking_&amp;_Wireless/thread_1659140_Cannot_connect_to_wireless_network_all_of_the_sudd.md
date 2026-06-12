---
title: "Cannot connect to wireless network all of the sudden."
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by FastTiger on 2011-01-03
Im new to Ubuntu and been enjoying this OS.But I have a problem. At first I was connecting to the internet via WiFi on my home network, and all of the sudden I couldn't connect to my wireless network anymore. The strange part was that I couldn't see my wireless network connection. But when I go to hidden wireless network its there, yet I still cannot connect.
Im using the Ethernet core for now and it works fine.

```
fasttiger@Beast:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-64 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:539  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3023   Missed beacon:0

```
Thanks for help in advance.

---

### Post by PatchesTheCaveman on 2011-01-03
You must run iwconfig as superuser for it to return useful information:
```
sudo iwconfig
```

Also, run these commands so we can see what might be going on with your hardware:
```
lspci -v
sudo lshw -C network
```

---

### Post by FastTiger on 2011-01-03
```
fasttiger@Beast:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=37/70  Signal level=-63 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:1504  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5128   Missed beacon:0
```

```
fasttiger@Beast:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at d4000000 (32-bit, prefetchable) [size=64M]
	Memory at d0009000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-ati
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0300000-d03fffff
	Prefetchable memory behind bridge: d8000000-dfffffff
	Kernel modules: shpchp

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 1000 [size=256]
	Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ALI 5451
	Kernel modules: snd-ali5451

00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
	Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: alim7101_wdt, alim1535_wdt

00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: medium devsel, IRQ 10
	Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1400 [size=256]
	Capabilities: <access denied>

00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0200
	Flags: medium devsel, IRQ 10
	Memory at d000a000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: hostap_pci
	Kernel modules: hostap_pci

00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
	Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 2c000000-2ffff000 (prefetchable)
	Memory window 1: 30000000-33fff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at 2000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at 2020 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at d0003000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at d0003800 (32-bit, non-prefetchable) [size=2K]
	Memory at d0004000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at 2040 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_ali
	Kernel modules: pata_ali

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: medium devsel
	Kernel driver in use: ali1535_smbus
	Kernel modules: alim7101_wdt, i2c-ali15x3, i2c-ali1535

00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
	Subsystem: Hewlett-Packard Company Device 0850
	Flags: bus master, medium devsel, latency 90, IRQ 10
	I/O ports at 2400 [size=256]
	Memory at d0008000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 34000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: natsemi
	Kernel modules: natsemi

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Radeon IGP 345M
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at d0300000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0320000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb

```

```
fasttiger@Beast:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wifi0
       version: 01
       serial: 00:02:8a:7a:f2:ec
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: irq:10 memory:d000a000-d000afff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:8a:28:da
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.68 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:10 ioport:2400(size=256) memory:d0008000-d0008fff memory:34000000-3400ffff
fasttiger@Beast:~$ 

```
Thanks.

---

### Post by PatchesTheCaveman on 2011-01-03
Strangely you have two wireless network interfaces, even though you only have one wireless network adapter.

At any rate, it appears NetworkManager is the culprit here.  That is the software that drives the network icon.  You can replace it with wicd, a program that does the same thing, but many people think works better.

To do so, make sure you are plugged into a working wired Ethernet connection, and run these commands on the terminal:
```
sudo apt-get update
sudo apt-get purge network-manager
sudo apt-get install wicd
```

You might need to reboot to fully remove NetworkManager and let wicd take over.

---

### Post by FastTiger on 2011-01-03
On wicd I can see my wireless network, but I get this message when trying to connect. Connection Failed: Unable to Get IP Address.

edit: I'd put my IP address manually, and got this. Connection failed: Could not contact the wireless access point.?

edit: I've restarted my laptop, and having trouble finding my wireless network on the wicd network manager, I have to click on the refresh button a few times till it finally shows my wireless network.??

---

### Post by FastTiger on 2011-01-03
It looks that I still have the same problem using wicd then I had with the network manager.

---

### Post by PatchesTheCaveman on 2011-01-03
Did you have Windows on this computer previously?  Did it work better?

The reason I ask is that you have a 802.11b wireless adapter.  Most devices are now 802.11g and new devices are now 802.11n.  If you have even one 802.11b device on a wireless network, all devices on that network must communicate using the slower 802.11b speeds.  

To take advantage of the increased speed and reliability of 802.11g networking, you might consider purchasing a new USB wireless dongle.  You don't have your location listed, but in the United States they can be bought for as little as $25-$30 in some discount stores.  The kernel wireless team maintains a list of USB wireless adapter fully supported by Linux:  [http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)

If it was working better before on Windows, there might be some more things we can try.  But I'll need you to copy/paste the output of another command for me:
```
lsmod
```

---

### Post by FastTiger on 2011-01-04
> **PatchesTheCaveman said:**
> Did you have Windows on this computer previously?  Did it work better?

Yes I had Windows XP. I don't know if it was better, but everything work.
```
fasttiger@Beast:~$ lsmod
Module                  Size  Used by
ses                     6077  0 
enclosure               6724  1 ses
usb_storage            40172  1 
binfmt_misc             6599  1 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
radeon                827837  2 
snd_ali5451            15875  2 
snd_ac97_codec         99227  1 snd_ali5451
ip6table_filter         1275  1 
ac97_bus                1014  1 snd_ac97_codec
ip6_tables             11764  1 ip6table_filter
snd_pcm                71475  2 snd_ali5451,snd_ac97_codec
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
snd_seq_midi            4588  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd_rawmidi            17783  1 snd_seq_midi
ttm                    56633  1 radeon
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5361  1 nf_nat_ftp
drm_kms_helper         30168  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
joydev                  8735  0 
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
ppdev                   5556  0 
snd_timer              19067  2 snd_pcm,snd_seq
iptable_filter          1302  1 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 radeon,ttm,drm_kms_helper
ip_tables              10460  1 iptable_filter
pcmcia                 35973  0 
parport_pc             26058  1 
hostap_pci             44661  1 
video                  18712  0 
psmouse                59033  0 
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
ati_agp                 5202  1 
snd                    49006  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
hostap                100441  1 hostap_pci
output                  1883  1 video
i2c_algo_bit            5168  1 radeon
yenta_socket           21518  0 
i2c_ali15x3             5190  0 
pcmcia_rsrc            10566  1 yenta_socket
soundcore                880  1 snd
i2c_ali1535             4865  0 
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,ati_agp
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc          7120  1 snd_pcm
lib80211                5058  2 hostap_pci,hostap
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
firewire_ohci          21106  0 
hid                    67742  1 usbhid
firewire_core          46643  1 firewire_ohci
pata_ali                7976  2 
natsemi                24030  0 
crc_itu_t               1383  1 firewire_core
floppy                 54311  0 

```

---

### Post by PatchesTheCaveman on 2011-01-04
Run this command to see if your wireless card driver is reporting any errors:
```
dmesg | grep -i hostap
```

Copy/paste the output in a reply to this message.

---

### Post by FastTiger on 2011-01-04
```
fasttiger@Beast:~$ dmesg | grep -i hostap
[   26.782234] hostap_pci 0000:00:09.0: enabling device (0010 -> 0012)
[   26.782262] hostap_pci 0000:00:09.0: PCI INT A -> Link[LNK3] -> GSI 10 (level, low) -> IRQ 10
[   26.783846] hostap_pci: Registered netdevice wifi0
```

---

### Post by darkhelmetchris on 2011-01-04
I will offer my two cents.  I have also run in to some trouble with wireless not working "all of a sudden".  I forget where I found this little tip, but what worked well for me was to delete the network adapter assignments and restart.  This has fixed my wireless a couple of times.  I still can't figure out what circumstances cause it to go wonky, but this seems to do the trick and get mine back online:

```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

PLEASE NOTE, as far as I know this file is recreated when it is not present after you restart Ubuntu.  Removing this file should not damage your installation; it has not damaged my install.  However, a word of caution makes me say:  I would back-up the file first (to some other folder in your profile - as I understand that this entire folder is searched and ran as part of startup?)

After deleting it and restarting, I found my wireless redetected and worked fine.  Your mileage may vary.

---

### Post by FastTiger on 2011-01-04
Im still getting the Unable To Get IP Address message.???

---

### Post by darkhelmetchris on 2011-01-04
> **FastTiger said:**
> Im still getting the Unable To Get IP Address message.???

Can you confirm that when you deleted that file (renaming in the same folder will not work) that the file was no longer present in the folder?

After that, and restarting your machine, what was the output of
```
iwconfig
```

---

### Post by darkhelmetchris on 2011-01-04
Also, right-click on your wireless connection, Edit Connections, go to your Wireless list of SSID's your machine knows, and run down the list, and remove the known config for your own wireless.  Then reconnect.  See if removing the profile for your wireless helps any.

---

### Post by FastTiger on 2011-01-04
> **darkhelmetchris said:**
> Can you confirm that when you deleted that file (renaming in the same folder will not work) that the file was no longer present in the folder?

After that, and restarting your machine, what was the output of
```
iwconfig
```

Yes the file was deleted.
```
fasttiger@Beast:~$ sudo iwconfig 
[sudo] password for fasttiger: 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"test"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"test"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:19  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:117   Missed beacon:0

```

---

### Post by FastTiger on 2011-01-04
> **darkhelmetchris said:**
> Also, right-click on your wireless connection, Edit Connections, go to your Wireless list of SSID's your machine knows, and run down the list, and remove the known config for your own wireless.  Then reconnect.  See if removing the profile for your wireless helps any.

Where and how exactly do I do this?

---

### Post by darkhelmetchris on 2011-01-04
I agree with PatchesTheCaveman.  It still seems that you have 2 wireless adapters listed.  If removing that "70-persistent-net.rules" file didn't refresh your configuration during the next boot, then I'm at a bit of a loss as to how to refresh it.  Hopefully another user will enlighten us both.

---

### Post by darkhelmetchris on 2011-01-04
> **FastTiger said:**
> Where and how exactly do I do this?

Sorry, that was for NetworkManager, and not for wicd.  I don't currently use wicd, but I'll sure be trying it out shortly.

---

### Post by FastTiger on 2011-01-05
> **darkhelmetchris said:**
> I agree with PatchesTheCaveman.  It still seems that you have 2 wireless adapters listed.  If removing that "70-persistent-net.rules" file didn't refresh your configuration during the next boot, then I'm at a bit of a loss as to how to refresh it.  Hopefully another user will enlighten us both.
Thanks for the help.

I still need a solution.

---

### Post by buntu_hugenewbie11 on 2011-08-29
Did you ever get a solution?
I have the same problem.

---

