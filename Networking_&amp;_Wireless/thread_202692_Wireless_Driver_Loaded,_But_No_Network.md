---
title: "Wireless Driver Loaded, But No Network"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by sdbradley86 on 2006-06-23
I've been using Ubuntu 5.10 for the past six months or so. I never had any issues with my wireless connectivity. Irecently was out of town, and when 6.06 was released, I installed it on a wired ethernet connection that I had available. My wireless card was installed at the time of installation (linksys WMP54G), but I was using the wired connection to access the web. 

Now I'm back home, and I disabled my wired ethernet port. When I went to connect my wireless internet up, and I had no access. I couldn't even ping the router. I was surprised, because Ubuntu has built in support for my card right out of the box (the RT2500 Driver). When I go to network settings, it displays my card as RA0, just as it always has, but when I activate it, I have no connectivity. I've searched these forums for an answer, but I tried almost every suggestion I've come across with no results.

I am posting the output of the following commands as they seem to be frequently requested: iwconfig, ifconfig, route, lsmod, dhclient as well as my interfaces file. Thanks in advance for your help.

```
david@david-desktop:~$ iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"linksys"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:10:2B:B8:2E
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=79/100  Signal level=-69 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```
david@david-desktop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4142 (4.0 KiB)  TX bytes:4142 (4.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:63:83:9A
          inet6 addr: fe80::212:17ff:fe63:839a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:6 txqueuelen:1000
          RX bytes:8462 (8.2 KiB)  TX bytes:4056 (3.9 KiB)
          Interrupt:193 Base address:0x4000
```

```
david@david-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

```
david@david-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  2
nls_cp437               5888  2
vfat                   13440  2
fat                    53020  1 vfat
ipv6                  265600  46
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
af_packet              22920  2
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117156  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         92704  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
tsdev                   8000  0
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd                    55268  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10208  1 snd
rt2500                173540  1
pcspkr                  2180  0
emu10k1_gp              3840  0
gameport               15496  2 emu10k1_gp
psmouse                36228  0
serio_raw               7300  0
rtc                    13492  0
intel_agp              22940  1
nvidia               4550772  12
agpgart                34888  2 intel_agp,nvidia
hw_random               5652  0
i2c_core               21904  2 i2c_acpi_ec,nvidia
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sg                     37920  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
usb_storage            74176  3
ide_generic             1536  0
ohci_hcd               21892  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  5 usb_storage,ohci_hcd,ehci_hcd,uhci_hcd
sd_mod                 19984  7
ata_piix               11012  5
libata                 78992  1 ata_piix
scsi_mod              139496  6 sr_mod,sbp2,sg,usb_storage,sd_mod,libata
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

```
david@david-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:12:17:63:83:9a
Sending on   LPF/ra0/00:12:17:63:83:9a
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database – sleeping.
```

etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-key s:**********
wireless-essid linksys

auto ra0

```

---

### Post by sdbradley86 on 2006-06-25
No Responses? If there is any info I left out, please let me know. I'd really like to get this problem resolved. Thanks.

---

### Post by sdbradley86 on 2006-07-06
Now, I'm not sure why I am getting no responses to my question. I provided all of the information. I did the research, but francly, every suggestion I've seen has turned up no results. I can't even ping my router, yet the driver appears to be loaded and working correctly. 

I really need help on this, because I've been forced to use Windows for the time being, and it hasn't been pleasant. All of my wireless info is posted above in my first post. Somebody out there must see a pottential problem in my configuration. Like I said before, it used to work before with Breezy. If everyone is just as baffled as I am, then please tell me how to unload the RT2x00 driver. I will use ndiswrapper instead. Thanks.

---

### Post by stupidkid on 2006-07-06
Run iwlist <interface_name> scan and see if you can pick up networks. 

To remove your module run rmmod rt2500 (I think that's the module name from the looks of lsmod). Then you would want to black list it so it doesn't get reloaded. add rt2500 to /etc/modules/blacklist (I don't think that's the correct file name, but it should be something like that).

Oh sometimes the driver gets loaded and an interface is created, but wireless doesn't really work. That's the case with my laptop. I had to blacklist the islsm module and use ndiswraper instead.

---

### Post by Borongas on 2006-07-12
SOMBODY please help....
I got the new release of ubuntu (6.06), and I loaded my wireless firmware and everything. The card is working and it shows up in device manager even with a bar of signal but I still cant connect to anything... somebody please help me, im a total nub.. I will be willing to pay someburry to walk me through fixing this, I am totally stuck ](*,) ](*,) ](*,) ](*,)

---

### Post by Nyati on 2006-07-12
Hi

I have the same problem!!!!!!!!1

I've got a built-in Cisco Aironet Wireless card in my IBM T30 Thinkpad. I'm also using Dapper Drake.

It appears that my wireless is set up however when I look at my connection properties,

eth0 status is 'idle' even though my signal strength is 98%. I also can't connect to anything.

Does anyone know how to set the status to active / connected?

---

### Post by atgnag on 2006-07-12
I'm a one day user myself, but here's how I got my wireless card to work. Firstly I went into my router setup and turned off all wireless security, not WEP, no WPA, etc., just to take out one more variable that could be messing me up. I found I had access with the security off on the router (just don't put a password in on the laptop in the box for it seems to turn it off), so I started playing with my security settings on the laptop. For some reason it wouldn't work with the passphrase I used on the router for WEP, but my Linksys router shows me the hex version of the passphrase and I put that into the NETWORK tool settings for my card on the laptop and darned if that didn't work. The only setup tool I used was the built in SYSTEM/NETWORK setup. Guess I was lucky this time, I lost a nights sleep trying to get wireless working with SUSE 10.1. I'm using an old IBM Thinkpad A22M with a Linksys WPC-11V4 card and a Linksys router. Hope some of this helps!
Dean

---

### Post by gratefultux on 2006-07-12
Borongas & Nyati: I had a similar problem when i first set up my network.  Make sure that it's not a DNS error.  Check /etc/resolv.conf  It should have an entry saying:
```
nameserver IPADDRESS
```
where IPADDRESS is likely to be your router's IP.
Also make sure that your encryption settings are correct.

---

