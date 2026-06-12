---
title: "no networks found ?"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by tanago on 2011-01-02
hey guys i'm trying to get my Linksys WUSB100v2 injecting.It's with rt2870 chipset.There are very much tutorials how to do this and i'm pretty sure I am doing something wrong.I have 6 drivers for this chipset:
Ralink v1.4.0.0 ; Ralink v2.4.0.1(latest) ; compat-wireless-2.6.32.16 ; rt2870-2.6.24-nemesis ; rt2870-2.6.25-hirte ; rt2870-2.6.30.9-darkelf and NOONE is working properly. I'm following these commands : 
make(no errors,1-5 warnings depending on the driver)
make install(no errors,no warnings) 
modprobe rt2870sta(no output) 
ifconfig ra0 up(no output)

and now the problem

iwlist scan 
eth0 Interface doesn't support scanning
ra0 No scan results

I tried changing HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to Y;following ralink's instruction;blacklisting rt2800usb,rt2x00usb and rt2x00lib all with no luck.

please anybody help me :( Thanks in advance

---

### Post by tanago on 2011-01-02
here is a complete output
```
**root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# make**

make -C tools
make[1]: Entering directory `/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/tools'
/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/tools/bin2h
cp -f os/linux/Makefile.6 /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/Makefile
make  -C  /lib/modules/2.6.30.9/build SUBDIRS=/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux modules
make[1]: Entering directory `/usr/src/linux-source-2.6.30.9'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.30.9/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/md5.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/mlme.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/rtmp_wep.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/action.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/ba_action.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/cmm_data.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/rtmp_init.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/rtmp_tkip.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/cmm_sync.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/eeprom.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/cmm_sanity.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/cmm_info.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/cmm_wpa.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/dfs.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/assoc.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/aironet.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/auth.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/auth_rsp.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/sync.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/sanity.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/rtmp_data.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/connect.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../sta/wpa.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/rt_linux.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/rt_profile.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/2870_main_dev.o
/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/2870_main_dev.c: In function &#1074;&#1026;&#152;RT28xxThreadTerminate&#1074;&#1026;™:
/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/2870_main_dev.c:874: warning: passing argument 1 of &#1074;&#1026;&#152;kill_pid&#1074;&#1026;™ makes pointer from integer without a cast
/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/2870_main_dev.c:894: warning: passing argument 1 of &#1074;&#1026;&#152;kill_pid&#1074;&#1026;™ makes pointer from integer without a cast
/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../os/linux/2870_main_dev.c:917: warning: passing argument 1 of &#1074;&#1026;&#152;kill_pid&#1074;&#1026;™ makes pointer from integer without a cast
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/2870_rtmp_init.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/rtusb_io.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/rtusb_bulk.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/rtusb_data.o
  CC [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/../../common/cmm_data_2870.o
  LD [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/rt2870sta.mod.o
  LD [M]  /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.30.9'

**root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# make install**

make -C /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.30.9/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.30.9/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.30.9
make[1]: Leaving directory `/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf/os/linux'

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# modprobe rt2870sta
[/B]
[B]Now i plug in the stick

root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# dmesg
[/B]
usb 1-3: new high speed USB device using ehci_hcd and address 7
usb 1-3: configuration #1 chosen from 1 choice


=== pAd = f8846000, size = 501704 ===

<-- RTMPAllocAdapterBlock, Status=0
MAC: 00,31,2E,32,2E,31
MAC: 00,31,2E,32,2E,31
ra0 (usb): not using net_device_ops yet

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# lsusb
[/B]
Bus 002 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1737:0078 Linksys WUSB100 RangePlus Wireless USB Network Adapter ver. 2
Bus 001 Device 002: ID 0c45:6242 Microdia PC Camera (SN9C201 + MI1310)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# ifconfig ra0
[/B]
ra0       Link encap:Ethernet  HWaddr 00:31:2e:32:2e:31
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# ifconfig ra0 up
[/B]
[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# ifconfig ra0
[/B]
ra0       Link encap:Ethernet  HWaddr 00:25:9c:b5:3d:03
          inet6 addr: fe80::225:9cff:feb5:3d03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# iwconfig ra0
[/B]
ra0       RT2870 Wireless  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:150 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:159
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# lsmod
[/B]
Module                  Size  Used by
ipv6                  239348  18
rt2870sta             468184  1
video                  18024  0
output                  2388  1 video
sbs                    10940  0
sbshc                   4500  1 sbs
cpufreq_stats           4728  0
cpufreq_powersave       1268  0
cpufreq_performance     1300  0
cpufreq_ondemand        7080  0
freq_table              3476  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7048  0
iptable_filter          2324  0
ip_tables              10916  1 iptable_filter
x_tables               13592  1 ip_tables
lp                      9412  0
snd_hda_codec_via      27384  1
joydev                  9728  0
snd_hda_intel          24712  0
snd_hda_codec          57204  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6776  1 snd_hda_codec
snd_pcm_oss            37728  0
snd_mixer_oss          14324  1 snd_pcm_oss
snd_pcm                67704  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
hid_drff                2836  0
rtc_cmos               10156  0
rtc_core               15792  1 rtc_cmos
rtc_lib                 2388  1 rtc_core
parport_pc             24292  1
parport                30572  2 lp,parport_pc
psmouse                41732  0
serio_raw               5016  0
snd_seq_dummy           2424  0
i2c_nforce2             6648  0
shpchp                 31560  0
snd_seq_oss            27328  0
snd_seq_midi            5952  0
snd_rawmidi            19488  1 snd_seq_midi
snd_seq_midi_event      5972  2 snd_seq_oss,snd_seq_midi
snd_seq                47568  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19068  2 snd_pcm,snd_seq
snd_seq_device          6048  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    50468  11 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               5856  1 snd
snd_page_alloc          7836  2 snd_hda_intel,snd_pcm
evdev                   9120  6
aufs                  143020  1
exportfs                3828  1 aufs
squashfs               21144  1
sg                     25064  0
forcedeth              55136  0
pata_amd               10744  0
pata_acpi               3892  0
ata_generic             4536  0
fuse                   53104  3

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# lshw -C network
[/B]
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:25:9c:b5:3d:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2870 Wireless

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# iwlist ra0 scan
[/B]
ra0       No scan results

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# lsb_release -d
[/B]
Description:    Ubuntu 8.10

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# uname -mr
[/B]
2.6.30.9 i686

[B]root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# sudo /etc/init.d/networking restart
[/B]
Reconfiguring network interfaces...Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:25:22:16:e7:40
Sending on   LPF/eth0/00:25:22:16:e7:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
if-up.d/mountnfs[eth0]: waiting for interface eth2 before doing NFS mounts
if-up.d/mountnfs[eth0]: waiting for interface ath0 before doing NFS mounts
if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
eth1: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
done. 

```

as you can see the kernel is 2.6.30.9 and the driver is built for the same kernel
and another interesting thing is when i type ifconfig ra0 before ifconfig ra0 up , the device's mac is read different from my actual one.

---

### Post by tanago on 2011-01-02
come on 100 views and noone can't suggest anything. Oh dear :cry:.I must say that under Windows there are 5 networks and one of them is mine and i have internet.

---

### Post by tanago on 2011-01-05
anyone ?

---

### Post by jsnelli2 on 2011-01-07
Mine is a WUSB100 and I can see networks right just fine, and am able to connect to mine when the PC first starts up, but speeds are very slow and after 5-10 minutes I lose connection and keep getting asked for a password.

---

### Post by tanago on 2011-01-08
under ubuntu 10.10 and it's integrated driver i can even connect but it loses connection in 5-10 minutes.

---

### Post by PatchesTheCaveman on 2011-01-08
Run these commands on a terminal and copy/paste the output:
```
sudo iwconfig
dmesg | grep -i rt
lsmod
```

---

### Post by tanago on 2011-01-09
> **PatchesTheCaveman said:**
> Run these commands on a terminal and copy/paste the output:
```
sudo iwconfig
dmesg | grep -i rt
lsmod
```
```
root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=150 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:159
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# dmesg | grep -i rt
KERNEL supported cpus:
Movable zone start PFN for each node
ACPI: PM-Timer IO Port: 0x508
Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
Enabling unmasked SIMD FPU exception support... done.
virtual kernel memory layout:
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
ACPI: (supports S0 S1 S3 S4 S5)
pci 0000:00:01.0: reg 10 io port: [0x900-0x9ff]
pci 0000:00:01.1: reg 10 io port: [0xdc00-0xdc3f]
pci 0000:00:01.1: reg 20 io port: [0x600-0x63f]
pci 0000:00:01.1: reg 24 io port: [0x700-0x73f]
pci 0000:00:01.1: PME# supported from D3hot D3cold
pci 0000:00:02.0: supports D1 D2
pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:02.1: supports D1 D2
pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:05.0: PME# supported from D3hot D3cold
pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
pci 0000:00:07.0: reg 14 io port: [0xd480-0xd487]
pci 0000:00:07.0: supports D1 D2
pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:08.0: reg 10 io port: [0xd400-0xd407]
pci 0000:00:08.0: reg 14 io port: [0xd080-0xd083]
pci 0000:00:08.0: reg 18 io port: [0xd000-0xd007]
pci 0000:00:08.0: reg 1c io port: [0xcc00-0xcc03]
pci 0000:00:08.0: reg 20 io port: [0xc880-0xc88f]
pci 0000:00:08.1: reg 10 io port: [0xc800-0xc807]
pci 0000:00:08.1: reg 14 io port: [0xc480-0xc483]
pci 0000:00:08.1: reg 18 io port: [0xc400-0xc407]
pci 0000:00:08.1: reg 1c io port: [0xc080-0xc083]
pci 0000:00:08.1: reg 20 io port: [0xc000-0xc00f]
pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]
pci 0000:00:09.0: bridge io port: [0xe000-0xefff]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
system 00:06: ioport range 0x4d0-0x4d1 has been reserved
system 00:06: ioport range 0x500-0x57f has been reserved
system 00:06: ioport range 0x580-0x5ff has been reserved
system 00:06: ioport range 0x800-0x87f has been reserved
system 00:06: ioport range 0x880-0x8ff has been reserved
system 00:06: ioport range 0xd00-0xd7f has been reserved
system 00:06: ioport range 0xd80-0xdff has been reserved
system 00:06: ioport range 0x1100-0x117f has been reserved
system 00:06: ioport range 0x1180-0x11ff has been reserved
system 00:0c: ioport range 0x280-0x28f has been reserved
system 00:0c: ioport range 0x290-0x29f has been reserved
pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X
pcieport-driver 0000:00:09.0: setting latency timer to 64
pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X
pcieport-driver 0000:00:0b.0: setting latency timer to 64
pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X
pcieport-driver 0000:00:0c.0: setting latency timer to 64
vesafb: pmi: set display start = c00cb473, set palette = c00cb4ce
vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Compaq SMART2 Driver (v 2.6.0)
amd74xx 0000:00:06.0: IDE port disabled
ide_generic: please use "probe_mask=0x3f" module parameter for probing all legacy ISA IDE ports
Loading iSCSI transport class v2.0-870.
iscsi: registered transport (tcp)
iscsi: registered transport (qla4xxx)
       with "disable_clustering=1" and report to maintainers
ehci_hcd 0000:00:02.1: debug port 1
ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: 9 ports detected
hub 2-0:1.0: 9 ports detected
USB Mass Storage support registered.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
Using IPI No-Shortcut mode
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
udevd version 124 started
rtc_cmos 00:02: RTC can wake from S4
rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
parport_pc 00:05: reported by Plug and Play ACPI
parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
rtusb init --->
<-- RTMPAllocAdapterBlock, Status=0
usbcore: registered new interface driver rt2870
<-- RTMPAllocTxRxRingMemory, Status=0
-->RTUSBVenderReset
<--RTUSBVenderReset
RTMPSetPhyMode: channel is out of range, use first channel=1
<==== RTMPInitialize, Status=0
root@bt:/media/Media/Installs/drivers/linux/rt2870/rt2870-2.6.30.9-darkelf# lsmod
Module                  Size  Used by
rt2870sta             463032  1
video                  18024  0
output                  2388  1 video
sbs                    10940  0
sbshc                   4500  1 sbs
cpufreq_stats           4728  0
cpufreq_powersave       1268  0
cpufreq_performance     1300  0
cpufreq_ondemand        7080  0
freq_table              3476  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7048  0
iptable_filter          2324  0
ip_tables              10916  1 iptable_filter
x_tables               13592  1 ip_tables
lp                      9412  0
snd_hda_codec_via      27384  1
snd_hda_intel          24712  0
snd_hda_codec          57204  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6776  1 snd_hda_codec
snd_pcm_oss            37728  0
snd_mixer_oss          14324  1 snd_pcm_oss
joydev                  9728  0
snd_pcm                67704  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2424  0
hid_drff                2836  0
snd_seq_oss            27328  0
snd_seq_midi            5952  0
snd_rawmidi            19488  1 snd_seq_midi
snd_seq_midi_event      5972  2 snd_seq_oss,snd_seq_midi
snd_seq                47568  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19068  2 snd_pcm,snd_seq
snd_seq_device          6048  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                41732  0
serio_raw               5016  0
snd                    50468  11 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             24292  1
parport                30572  2 lp,parport_pc
rtc_cmos               10156  0
rtc_core               15792  1 rtc_cmos
rtc_lib                 2388  1 rtc_core
soundcore               5856  1 snd
snd_page_alloc          7836  2 snd_hda_intel,snd_pcm
shpchp                 31560  0
i2c_nforce2             6648  0
evdev                   9120  6
aufs                  143020  1
exportfs                3828  1 aufs
squashfs               21144  1
sg                     25064  0
pata_amd               10744  0
forcedeth              55136  0
pata_acpi               3892  0
ata_generic             4536  0
fuse                   53104  3

```

---

### Post by tanago on 2011-01-11
Downloaded Backtrack 4 R2 and it is working with the integrated driver

---

### Post by jsnelli2 on 2011-01-15
Isn't that just another Linux distribution? If so, that is hardly a solution to getting the adapter to work in Ubuntu.

---

### Post by tanago on 2011-01-20
> **jsnelli2 said:**
> Isn't that just another Linux distribution? If so, that is hardly a solution to getting the adapter to work in Ubuntu.
yes it is

---

