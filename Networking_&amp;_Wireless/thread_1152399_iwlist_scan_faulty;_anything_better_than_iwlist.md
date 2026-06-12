---
title: "iwlist scan faulty; anything better than iwlist?"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by wgw on 2009-05-07
My home access point was not showing up on net-manager, so after many reboots and fiddling, I installed wicid. No joy there either. I tried using iwlist to see the access point: nada.

The problem resolved itself when I completely shut down the computer and left it for about 15 min. 

My question: what could interfere with iwlist? Is there a more low-level way to list the access points?

I know my home access point was working -- my partner detected it on her machine running Suse. I know my network card was working: I could see all my neighbors' points and connected to one. I just couldn't see my own, until I shut down the machine. 

The only thing I can imagine is that somehow the card buffer was corrupt in some way that was specific to my router. That sounds weird! But I can't imagine how a single access point could be blocked.

Any ideas?

One thing that was strange, was that the net-manager connections editor was behaving strangely. What file does it affect? 

Thanks for any help with this ufo. (unidentified freaking :O ?)

---

### Post by coffeeaddict22 on 2009-05-07
Have a look at iwspy (sudo iwspy scan is the nicest tool).  Also, for network manager ```
nm-tool
``` is a useful terminal command.

---

### Post by kevdog on 2009-05-08
If you run iwlist as a regular user the results are cached.  I don't remember the caching interval, however to avoid the cache run the command as root

sudo iwlist scan

This should give you the most accurate result.

---

### Post by wgw on 2009-05-08
Thanks for the suggestions.

When I run iwspy, I get:
```

bill@bill-laptop:~$ sudo iwspy scan
scan      Interface doesn't support wireless statistic collection
```

sudo or not, iwlist does not give a complete list. In fact, now that I have connected with wcid, I only see my home router and not my neighbors'. 

I'm collecting hypotheses: could be an artifact of hibernate; could be a faulty network card. Mystery! (But I am able to connect....) Probably the only solution is to find software that interacts directly with the card. Perhaps iwlist does that -- I will see if there is some doc on how it is programmed. 

Thanks again for your replies.

---

### Post by coffeeaddict22 on 2009-05-08
What's the output of ```
lshw -C network
``` and ```
iwconfig
``` Have you just upgraded from 8.10 to 9.04?

---

### Post by wgw on 2009-05-09
I just upgraded to 8.04 (Hardy). With the connection to my home address: 

```
bill@bill-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"wirelessRus"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:0D:88:AE:1E:3E   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=94/100  Signal level=-35 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

And: 

```
bill@bill-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:82:d9:4f
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:c0:5b:d9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.184 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

So my connection is:

```
bill@bill-laptop:~/$ sudo iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0D:88:AE:1E:3E
                    ESSID:"wirelessRus"
                    Mode:Master
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=96/100  Signal level=-30 dBm  Noise level=-88 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000245c7ea8fd

eth0      Interface doesn't support scanning.

```

But there are a ton of other access points in the neighborhood. So not sure why I'm getting sometimes only my own, sometimes only NOT my own!

---

### Post by coffeeaddict22 on 2009-05-09
You've got a driver problem.  wmaster0 is coming up as the logical name for your wireless, and its got the Intel wireless driver.  At a guess, you were running ndiswrapper with 7.10, and are enjoying the freedom of the Linux driver.  
wmaster0 is a 'dummy' connection the kernel uses for managing the internet connection.  It is allowed to show up in wlist, but shouldn't be the logical name for a connection; if it is, there's a problem with the interface drivers.
What I suspect happens is ndiswrapper is keeping its settings over a system upgrade; that's great unless it gets superseded.  I haven't used ndiswrapper for a while, but my guess is there's a .directory in your home folder that's got info in it which messes up the new settings.  If that's the case, uninstalling ndiswrapper with modprobe should fix it.
Have a look at ```
lsmod
```, Post the results back if you need more help.

---

### Post by wgw on 2009-05-09
Yes CoffeeAddict, you are right. 

I was on a Compaq with a Broadcom wireless. That crashed, and I transferred everything to a thinkpad. I have ndiswrapper files still on my hard drive, but I don't see anything loaded (and there is no /etc/ndiswrapper/): 

```
bill@bill-laptop:~$ lsmod
Module                  Size  Used by
e1000                 126016  0 
iwl3945                89840  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
af_packet              23812  4 
ipv6                  267908  10 
wacom                  18048  0 
snd_rtctimer            4640  1 
binfmt_misc            12808  1 
uinput                 10240  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
bay                     6912  0 
dock                   11280  1 bay
container               5632  0 
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
coretemp                8448  0 
visor                  18572  0 
usbserial              35688  1 visor
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
pcmcia                 40876  0 
irtty_sir               9728  0 
sir_dev                17412  1 irtty_sir
nsc_ircc               24208  0 
thinkpad_acpi          51836  0 
irda                  203068  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               3072  1 irda
nvram                   9992  1 thinkpad_acpi
evdev                  13056  8 
psmouse                40336  0 
serio_raw               7940  0 
pcspkr                  4224  0 
ac                      6916  0 
battery                14212  0 
snd_hda_intel         346136  5 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
button                  9232  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  0 
snd                    56996  21 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  1 intel_agp
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
iptable_nat             8324  0 
nf_nat                 20396  1 iptable_nat
nf_conntrack_ipv4      19080  2 iptable_nat
nf_conntrack           66752  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  0 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  2 iptable_nat,ip_tables
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sg                     36880  0 
ata_piix               19588  0 
pata_acpi               8320  0 
sd_mod                 30720  6 
usbhid                 32128  0 
hid                    38784  1 usbhid
ata_generic             8324  0 
ahci                   28548  5 
libata                159600  4 ata_piix,pata_acpi,ata_generic,ahci
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  7 wacom,visor,usbserial,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

But I do think that is the problem. I need to look at my interface files: 

```
bill@bill-laptop:~/django/mysite$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

```


Here are some pertinent bits from dmesg: 

```
[   33.809148] swsusp: Basic memory bitmaps freed
[   34.068661] usb 3-1: new low speed USB device using uhci_hcd and address 6
[   34.241667] usb 3-1: configuration #1 chosen from 1 choice
[   34.263824] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input15
[   34.284316] input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.2-1
[   34.284392] usb 4-2: USB disconnect, address 6
[   34.523867] usb 4-2: new full speed USB device using uhci_hcd and address 7
[   34.695891] usb 4-2: configuration #1 chosen from 1 choice
[   48.998871] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   48.998880] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   48.999033] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   48.999060] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   48.999084] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   49.621415] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   49.623191] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   49.627737] udev: renamed network interface wlan0 to eth1
[   49.922907] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   49.922915] Copyright (c) 1999-2006 Intel Corporation.
[   49.923078] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[   49.923089] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   49.923113] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   49.985003] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:15:58:82:d9:4f
[   50.042748] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   52.183935] Uhhuh. NMI received for unknown reason a1 on CPU 0.
[   52.183944] You have some hardware problem, likely on the PCI bus.
[   52.183948] Dazed and confused, but trying to continue
[   55.940712] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.276935] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   66.429569] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   66.827346] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   70.455905] eth1: Initial auth_alg=0
[   70.455913] eth1: authenticate with AP 00:0d:88:ae:1e:3e
[   70.456611] eth1: Initial auth_alg=0
[   70.456616] eth1: authenticate with AP 00:0d:88:ae:1e:3e
[   70.457512] eth1: Initial auth_alg=0
[   70.457518] eth1: authenticate with AP 00:0d:88:ae:1e:3e
[   70.458078] eth1: RX authentication from 00:0d:88:ae:1e:3e (alg=0 transaction=2 status=0)
[   70.458084] eth1: authenticated
[   70.458088] eth1: associate with AP 00:0d:88:ae:1e:3e
[   70.459254] eth1: authentication frame received from 00:0d:88:ae:1e:3e, but not in authenticate state - ignored
[   70.460067] eth1: RX AssocResp from 00:0d:88:ae:1e:3e (capab=0x471 status=0 aid=1)
[   70.460073] eth1: associated
[   70.463774] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   80.571361] eth1: no IPv6 routers present

```

There is a problem here! I think the first thing I should fix is to allow wan0 to be the wireless connection. Right now it is eth1.

---

### Post by coffeeaddict22 on 2009-05-10
Nope.  The name doesn't matter as a rule.  The problem is you've got two drivers.  I suspect there was more to the output of lshw -C network; in there will be something that has eth1 as its logical name, and whatever is listed as the driver of that needs to be removed.

---

### Post by wgw on 2009-05-10
When I run lshw -C network, I don't get anything for eth1, only eth0, as indicated above. (I'm assuming eth0 is the hardwire interface.) 

I do remember at one point (on the old system years ago!) reassigning wlan0 to eth in a configuration file, but can't see anything about that in the files I have checked. 

there is no .ndiswrapper directory or file in my home directory,and nothing for .ndiswrapper indicated in synaptic. So I don't know where to look, if not dmesg, for a double loading of a driver. 

dmesg does have that ```
[   52.183935] Uhhuh. NMI received for unknown reason a1 on CPU 0.
[   52.183944] You have some hardware problem, likely on the PCI bus.
[   52.183948] Dazed and confused, but trying to continue
[
```

But I don't think it is relevant.

---

### Post by coffeeaddict22 on 2009-05-10
That'll be your problem.  Try typing in ```
lspci -v 
``` and looking for the problem in the output.  The -v is only a switch to make it verbose, so you could try without it to start, but you'll probably need the info to figure out the problem.

---

### Post by wgw on 2009-05-10
I am not competent enough to see anything wrong here, though I am surprised by the duplicate IRQs.That must not be a problem in itself, or I would be having more problems than I do. Anyway, the network card's IRQ is not duplicated.

I'm surprised too that there is a IDE interface, since it is a SATA drive. Maybe I should check the Bios configuration....Much to learn in all this!

```
bill@bill-laptop:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Lenovo ThinkPad T60
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: ee100000-ee1fffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
	Capabilities: [88] Subsystem: Lenovo Unknown device 2014
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at ee400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: ee000000-ee0fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Lenovo Unknown device 2011
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00005fff
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: 00000000e4000000-00000000e40fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Lenovo Unknown device 2011
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
	I/O behind bridge: 00006000-00007fff
	Memory behind bridge: e8000000-e9ffffff
	Prefetchable memory behind bridge: 00000000e4100000-00000000e41fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Lenovo Unknown device 2011
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=13, sec-latency=0
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: ea000000-ebffffff
	Prefetchable memory behind bridge: 00000000e4200000-00000000e42fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Lenovo Unknown device 2011
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ee404000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 0000a000-0000dfff
	Memory behind bridge: e4300000-e7ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e3ffffff
	Capabilities: [50] Subsystem: Lenovo Unknown device 2013

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1880 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 218
	I/O ports at 18c8 [size=8]
	I/O ports at 18ac [size=4]
	I/O ports at 18c0 [size=8]
	I/O ports at 18a8 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at ee404400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: medium devsel, IRQ 11
	I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300] (prog-if 00 [VGA controller])
	Subsystem: Lenovo Unknown device 2005
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at ee100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at ee120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
	Subsystem: Lenovo ThinkPad T60
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint IRQ 0

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1010
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at edf00000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Lenovo ThinkPad T60/R60 series
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at e4300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: e0000000-e3fff000 (prefetchable)
	Memory window 1: 50000000-53fff000
	I/O window 0: 0000a000-0000a0ff
	I/O window 1: 0000a400-0000a4ff
	16-bit legacy interface ports at 0001

```

---

### Post by wgw on 2009-05-10
This appears to show some kind of driver duplication. What do the -5k drivers do?

```
bill@bill-laptop:~$ modprobe -l | grep iwlwifi
/lib/modules/2.6.24-24-generic/ubuntu/wireless/[COLOR="Red"]iwlwifi-5k[/COLOR]/net/wireless/iwlwifi5k-cfg80211.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi-5k/net/mac80211/iwlwif5k-mac80211.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi-5k/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi-5k/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko

```

the configuration given at thinkwiki is simpler: 

```
$ modprobe -l | grep iwlwifi
 /lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
 /lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
 /lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
 /lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko

``` 

( [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T60#Open_Source_Intel_Wifi_Driver](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T60#Open_Source_Intel_Wifi_Driver) )

---

### Post by wgw on 2009-05-10
More complicated than I thought! That bcm43xx is definitely not necessary... I don't have that  card anymore...

```
bill@bill-laptop:~$ sudo modprobe -l | grep wireless
/lib/modules/2.6.24-24-generic/ubuntu/wireless/hso.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/fsam7400.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/rtl8187-usb/rtl8187/r8187.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/rtl8187-usb/ieee80211/ieee80211_crypt_wep-rtl.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/rtl8187-usb/ieee80211/ieee80211_crypt_tkip-rtl.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/rtl8187-usb/ieee80211/ieee80211_crypt_ccmp-rtl.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/rtl8187-usb/ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/rtl8187-usb/ieee80211/ieee80211_crypt-rtl.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/acx/acx.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi-5k/net/wireless/iwlwifi5k-cfg80211.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi-5k/net/mac80211/iwlwif5k-mac80211.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi-5k/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi-5k/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/prism2_usb/prism2_usb.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/p80211/p80211.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/wimax-i2400m/drivers/net/wimax/i2400m/i2400m.ko
/lib/modules/2.6.24-24-generic/ubuntu/wireless/wimax-i2400m/drivers/net/wimax/wimax.ko
/lib/modules/2.6.24-24-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/zd1201.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/wl3501_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/wavelan_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/wavelan.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/strip.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/spectrum_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/ray_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/prism54/prism54.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/p54usb.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/p54pci.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/p54common.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/orinoco.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/orinoco_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/libertas/usb8xxx.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/libertas/libertas_sdio.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/libertas/libertas.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/netwave_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/hostap/hostap_plx.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/hostap/hostap_pci.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/hostap/hostap.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/hermes.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/atmel_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/atmel.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/arlan.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/airo_cs.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/airo.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/atmel_pci.ko

```

---

### Post by coffeeaddict22 on 2009-05-11
Don't worry about the modprobe.  The big downside of a "just works" kernel is it needs to have all the drivers for all the gear it might need...

The easy answer is an upgrade.  Sounds like there's at least two drivers on the system.  I'd clean install 8.10- if you go to 9.04 you'd have to put up with loss of some graphics ability as the proprietary driver dropped support for your video card.  The benefit is that in the last 12 months wireless support in the kernel has increased significantly, so your wireless should work out of the box with 9.04, and probably with 8.10 ( I can't be certain with your card which kernel included it).

However, if you're going to do it, make sure you explicitly select the packages you want out of the /home folder; in particular, ndiswrapper seems to keep some data in there it can transfer over during upgrades.

---

### Post by wgw on 2009-05-11
Many thanks! I think I will go to 8.10, somewhat cautiously -- everything mostly works in 8.04 for the moment, in spite of this flaky network access point. But an upgrade is, as you suggest, the most logical solution.

Thanks so much for your help. It has been a learning experience!

---

