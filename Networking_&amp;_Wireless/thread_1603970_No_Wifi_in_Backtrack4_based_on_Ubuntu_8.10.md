---
title: "No Wifi in Backtrack4 based on Ubuntu 8.10"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by nbulchandani on 2010-10-23
Hello everyone,

i just installed backtrack 4 and had some noob doubts.i have no idea of configuring networks on Linux....however i figured out some commands and here are the results.
Please help me get my WiFi working.
I am having a Dell Vostro 1510 laptop.

1)
root@bt:/home/noks# /etc/init.d/networking start

Configuring network interfaces...eth1: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
done.
2)
root@bt:/home/noks# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
3)lspci output has a line as:
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
4)lsusb has a line as:
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
5)output of ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:21:70:be:30:28
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
6)output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.
7)output of lsmod:
Module                  Size  Used by
i915                  172552  2
drm                   142208  3 i915
sbs                    10940  0
sbshc                   4500  1 sbs
acpi_cpufreq            7808  0
cpufreq_stats           4728  0
cpufreq_ondemand        7080  2
freq_table              3476  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_performance     1300  0
cpufreq_conservative     7048  0
cpufreq_powersave       1268  0
iptable_filter          2324  0
ip_tables              10916  1 iptable_filter
x_tables               13592  1 ip_tables
ipv6                  239348  10
joydev                  9728  0
parport_pc             24292  0
lp                      9412  0
parport                30572  2 parport_pc,lp
snd_hda_codec_realtek   194936  1
snd_hda_intel          24712  0
snd_hda_codec          57204  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6776  1 snd_hda_codec
snd_pcm_oss            37728  0
snd_mixer_oss          14324  1 snd_pcm_oss
snd_pcm                67704  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2424  0
snd_seq_oss            27328  0
sdhci_pci               6900  0
sdhci                  15864  1 sdhci_pci
mmc_core               46704  1 sdhci
uvcvideo               58016  0
videodev               37056  1 uvcvideo
v4l1_compat            13336  2 uvcvideo,videodev
snd_seq_midi            5952  0
led_class               3608  1 sdhci
serio_raw               5016  0
btusb                  11592  0
bluetooth              54148  1 btusb
snd_rawmidi            19488  1 snd_seq_midi
wl                   1275008  0
lib80211                5176  1 wl
iTCO_wdt               10584  0
iTCO_vendor_support     2840  1 iTCO_wdt
snd_seq_midi_event      5972  2 snd_seq_oss,snd_seq_midi
snd_seq                47568  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtc_cmos               10156  0
rtc_core               15792  1 rtc_cmos
snd_timer              19068  2 snd_pcm,snd_seq
snd_seq_device          6048  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtc_lib                 2388  1 rtc_core
video                  18024  1 i915
output                  2388  1 video
snd                    50468  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               5856  1 snd
snd_page_alloc          7836  2 snd_hda_intel,snd_pcm
intel_agp              26108  1
agpgart                29356  3 drm,intel_agp
shpchp                 31560  0
wmi                     5960  0
dell_laptop             3380  0
rfkill                  9328  3 dell_laptop
evdev                   9120  13
dcdbas                  7092  1 dell_laptop
sg                     25064  0
firewire_ohci          22648  0
firewire_core          40640  1 firewire_ohci
pata_acpi               3892  0
ata_generic             4536  0
fuse                   53104  5
8)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:be:30:28
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
9)
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
10)
root@bt:/home/noks# lsb_release -d
Description:    Ubuntu 8.10
11)
root@bt:/home/noks# uname -mr
2.6.30.9 i686
12)some lines in dmesg were as:
b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
b43-pci-bridge 0000:06:00.0: setting latency timer to 64
ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0


Please help me out,
Thanks...

---

### Post by nbulchandani on 2010-11-02
any one has any idea???

---

