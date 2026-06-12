---
title: "A slight annoyance"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by joebrueske on 2009-02-05
The problem, I'm getting an error when trying to connect to my router manually through command prompts. As required by the sticky, here is the information to get you all started to help me out. And before I go any further, thanks. This forum has always been very helpful in helping Microcrap break my addiction. . . lol.

Laptop: Toshiba Satalite M65
```
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```
```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:13:ce:94:64:0a  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe94:640a/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:1492  Metric:1
          RX packets:433701 errors:47 dropped:47 overruns:0 frame:0
          TX packets:217900 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1612017760 (1.5 GB)  TX bytes:50685081 (48.3 MB)
          Interrupt:23 Base address:0xc000 Memory:c4005000-c4005fff 

eth2      Link encap:Ethernet  HWaddr 00:0f:b0:dd:76:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111500 (108.8 KB)  TX bytes:111500 (108.8 KB)
```
```
$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:AE:AB:C6   
          Bit Rate:5.5 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/100  Signal level=-67 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:47  Rx invalid frag:0
          Tx excessive retries:166  Invalid misc:0   Missed beacon:5
```
```
$ lsmod
Module                  Size  Used by
ipw2200               146120  0 
arc4                    2944  0 
ecb                     4480  0 
blkcipher               8324  1 ecb
ieee80211_crypt_wep     6272  0 
af_packet              23812  6 
ipv6                  267908  8 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
snd_intel8x0           35356  5 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
evdev                  13056  7 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
psmouse                40336  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
sdhci                  19076  0 
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               51460  1 sdhci
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  19 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
fglrx                1555468  23 
battery                14212  0 
ac                      6916  0 
video                  19856  0 
output                  4736  1 video
button                  9232  0 
shpchp                 34452  0 
intel_agp              25492  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 fglrx,intel_agp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ahci                   28548  0 
pata_acpi               8320  0 
ata_generic             8324  0 
8139too                27520  0 
ata_piix               19588  2 
libata                159600  4 ahci,pata_acpi,ata_generic,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
joe@rogue-three:~$ clear

joe@rogue-three:~$ lsmod
Module                  Size  Used by
ipw2200               146120  0 
arc4                    2944  0 
ecb                     4480  0 
blkcipher               8324  1 ecb
ieee80211_crypt_wep     6272  0 
af_packet              23812  6 
ipv6                  267908  8 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
snd_intel8x0           35356  5 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
evdev                  13056  7 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
psmouse                40336  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
sdhci                  19076  0 
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               51460  1 sdhci
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  19 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
fglrx                1555468  23 
battery                14212  0 
ac                      6916  0 
video                  19856  0 
output                  4736  1 video
button                  9232  0 
shpchp                 34452  0 
intel_agp              25492  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 fglrx,intel_agp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ahci                   28548  0 
pata_acpi               8320  0 
ata_generic             8324  0 
8139too                27520  0 
ata_piix               19588  2 
libata                159600  4 ahci,pata_acpi,ata_generic,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```
```
$ iwlist scan
       *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:94:64:0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.6 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 promiscuous=yes wireless=IEEE 802.11b
```
```
$ iwlist scan
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:AE:AB:C6
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=50/100  Signal level=-70 dBm  
                    Extra: Last beacon: 4328ms ago

rtap0     Interface doesn't support scanning.
```
```
$ lsb_release -d
Description:	Ubuntu 8.04.2
```
```
$ uname -mr
2.6.24-23-generic i686
```
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```

Of course the NetworkManager applet works just fine, but I would like to be able to know how to connect to other routers in command prompt. Here are the steps I'm taking and the output.

This is being tested on my Netgear MR-814 v2. Of course I connect just fine using the applet. I'm a bit curious as to how it's connecting and I'm unable to. I don't know.

```
$ sudo ifconfig eth1 down
$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 24566
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

rtap0: unknown hardware address type 803
rtap0: unknown hardware address type 803
Listening on LPF/eth1/00:13:ce:94:64:0a
Sending on   LPF/eth1/00:13:ce:94:64:0a
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
$ sudo ifconfig eth1 up
```
You'll see that rtap0 error later too.
```
$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

rtap0: unknown hardware address type 803
rtap0: unknown hardware address type 803
Listening on LPF/eth1/00:13:ce:94:64:0a
Sending on   LPF/eth1/00:13:ce:94:64:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Now, of course, if there's a connection, it'll give me the IP Addresses assigned and the time until renewal.

I was told to use these commands to connect. As you can see I am not using an wrapper. Should I be? I'm not sure the purpose of one. Again, this is just out of curiosity in case the NetworkManager conks out on me one day.

---

### Post by Iowan on 2009-02-05
I'm not sure what **rtap0** is... looks like the machine might be confused, too. **ifconfig -a** should show all interfaces - active or not.  You can check */etc/udev/rules.d/70-persistent-net.rules* to see if it shows up there.

---

### Post by joebrueske on 2009-02-06
Well, apparently rtap0 is an interface. It's used with packet injection apparently. So, that's not the reason why I can't connect to an AP from command prompts.

---

### Post by azr on 2009-02-06
I don't think  you need to worry about rtap0 to get an ip address eth1. Though why do you bring the eth1 interface down before dhclient? I suggest trying it with the interface up (and with the router details set as well).

A shot in the dark if that doesn't work: use dhpcd instead of dhclient. Though with the interface up.

---

