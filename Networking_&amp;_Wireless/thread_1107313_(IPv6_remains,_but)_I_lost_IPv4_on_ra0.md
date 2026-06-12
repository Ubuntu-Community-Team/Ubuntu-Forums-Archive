---
title: "(IPv6 remains, but) I lost IPv4 on ra0"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by TBerk on 2009-03-26
Here is a list of Wireless related information with their respective commands. 


1 ) Machine Brand and Model (PC/Laptop):

Code:Get it from your product information.



Desktop Gateway using an irlink101 300N PCI based 80211n (in a 'g' only wireless environment.) The card is using a RT2866 chipset. I am not using ndiswrapper.


2 ) Wireless Brand, Model and Wireless Chipset:

Code:$ lspci


02:02.0 Network controller: RaLink RT2800 802.11n PCI
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)




(hint) use grep to get only information about the Wireless

Code:



$ lspci -nn | grep 'Wireless Brand'



3 ) check interface:

Code:$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:07:e9:5c:d4:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

ra0       Link encap:Ethernet  HWaddr 00:1d:6a:20:6a:eb  
          inet6 addr: fe80::21d:6aff:fe20:6aeb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:751881 (751.8 KB)  TX bytes:5539 (5.5 KB)
          Interrupt:18 




Code:$ iwconfig



(hint) if the Wireless interface name is wlan0 you can also use

Code:$ iwconfig wlan0


lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.462 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-56 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




4 ) Check for modules:

Code:$ lsmod

Module                  Size  Used by
binfmt_misc            16904  1 
ppdev                  15620  0 
lp                     17156  0 
speedstep_lib          12676  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
battery                18436  0 
ipv6                  263972  10 
af_packet              25728  2 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  4 snd_emu10k1_synth
snd_ac97_codec        111652  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_emu10k1,snd_pcm
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57776  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
evdev                  17696  6 
snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  20 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             39204  1 
soundcore              15328  1 snd
parport                42604  3 ppdev,lp,parport_pc
rt2860sta             520664  1 
pcspkr                 10624  0 
nvidia               7103300  34 
i2c_core               31892  1 nvidia
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  2 nvidia,intel_agp
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42392  4 
sr_mod                 22212  0 
crc_t10dif              9984  1 sd_mod
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24580  3 
ata_generic            12932  0 
e100                   41356  0 
libata                178208  3 pata_acpi,ata_piix,ata_generic
mii                    13440  1 e100
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  4 usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 




(hint) search for the Wireless module

Code:$ lsmod | grep "wlan_module_name"

$ lsmod | grep "rt2860sta"
rt2860sta             520664  1 





5 ) Kernel boot messages

Code:$ dmesg



(hint) the same as in (4)


$ dmesg | grep "ra0"
[   17.819847] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   17.819882] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   17.819916] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   17.819950] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   35.039545] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   35.039601] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   35.039647] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   35.039694] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   45.484010] ra0: no IPv6 routers present
[   79.333215] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   79.333267] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   79.333315] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   79.333364] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   79.433433] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   79.433481] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   79.433527] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   79.433573] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   90.180007] ra0: no IPv6 routers present
[  122.934430] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  122.934478] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  122.934523] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  122.934570] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  123.041274] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  123.041321] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  123.041366] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  123.041412] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  133.140011] ra0: no IPv6 routers present
[  166.525498] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  166.525545] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  166.525590] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  166.525636] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  166.632068] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  166.632117] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  166.632162] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  166.632209] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  176.944010] ra0: no IPv6 routers present
[  471.330131] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  471.330179] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  471.330224] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  471.330270] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  471.441040] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  471.441087] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  471.441133] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  471.441179] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  482.040010] ra0: no IPv6 routers present




6 ) Network configuration

Code:$ sudo lshw -C network


 *-network:0             
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=rt2860 latency=32 maxlatency=4 mingnt=2 module=rt2860sta
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 82
       serial: 00:07:e9:5c:d4:73
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:1d:6a:20:6a:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2860 Wireless




7 ) Scan for networks:

Code: $ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

[Note: wicd does see many local networks.]



(hint) the same as in (3)

Code:$ iwlist scan wlan0



8 ) Ubuntu Version:

Code:$ lsb_release -d


Description:	Ubuntu 8.10



9 ) Kernel/architecture (including 32 vs. 64 bit):

Code:$ uname -mr

2.6.27-11-generic i686




10 ) Restarting the network:

Code:$ sudo /etc/init.d/networking restart



 * Reconfiguring network interfaces...                                                       
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ra0.pid with pid 4118
removed stale PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:1d:6a:20:6a:eb
Sending on   LPF/ra0/00:1d:6a:20:6a:eb
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.1.2 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:1d:6a:20:6a:eb
Sending on   LPF/ra0/00:1d:6a:20:6a:eb
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
receive_packet failed on ra0: Network is down
Terminated
Failed to bring up ra0.


[end]

---

### Post by TBerk on 2009-03-26
In trying some of these useful commands:
[http://ubuntuforums.org/showthread.php?t=1106353](http://ubuntuforums.org/showthread.php?t=1106353)

I got as far as the following:


$ sudo dhclient3 ra0
There is already a pid file /var/run/dhclient.pid with pid 6174
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:1d:6a:20:6a:eb
Sending on   LPF/ra0/00:1d:6a:20:6a:eb
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
===========================

btw - a scan of local cells show 11, with the information I expect.  I can scan but I've lost IPv4 connectivity, so it seems. 

IS there a way to reinstall just that portion of TCP/IP or do I need to reinstall the wifi card from scratch?

TBerk

---

### Post by TBerk on 2009-03-26
OK, so I am back online in Ubuntu, but in a manual fashion (so far).

I did some searching and discovered a thread with 'how to disable IPv6' in it.  The relevant portion for me was:

> $ sudo nano /etc/modprobe.d/aliases


alias net-pf-10 ipv6 off

alias net-pf-10 off

alias ipv6 off

#alias net-pf-10 ipv6

and after a reboot I ran the following command; 

> $ sudo dhclient3 ra0


which was able to get me a DHCP IP address. Now, to reboot once again and see if I can start relying on things to kick in automatically or perhaps I'll need to dig a little deeper.

TBerk

---

### Post by TBerk on 2009-03-27
OK, so upon a reboot I find I have the same symptoms as before;

- wicd wont get past validation. (But 'sees' all the local wifi nodes just fine.)

- ```
sudo dhclient ra0
``` enables DHCP and allows a connection through to the Internet.

That then becomes the focus of my research going forward. For some reason I may need to (re)enable dhclient in an automatic role.


TBerk
seems I'm having a dialogue with myself here...

---

### Post by TBerk on 2009-03-27
Latest news: Booted from the beta 9.04 CD and everything just works.

I'm likely going to let this thread die off.


TBerk

---

