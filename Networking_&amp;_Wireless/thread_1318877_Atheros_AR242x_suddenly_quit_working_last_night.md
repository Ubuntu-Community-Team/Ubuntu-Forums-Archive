---
title: "Atheros AR242x suddenly quit working last night"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by E. Mark Mitchell on 2009-11-08
Preface: I am not a programmer, but I believe in open source and I support and promote Linux and Ubuntu when I can as a matter of philosophy.  I've learned a few things in the year I've been using it, but when suggesting fixes, it will help immensely to give step-by-step instructions; I can fairly easily grasp many of the concepts, but when it comes to actually enacting them, might be best to translate it to Captain Dummy talk.

According to the lead thread of Howto Post a Wireless Issue, let me get the basics out of the way, and let me apologize in advance for the length of this data, but with only a few exceptions, I don't recognize what's relevant and what isn't.  My story of what went wrong is at the bottom; this whole middle bit is just copy-pasted stuff:

1) Machine Brand and Model

```
Compaq Laptop, says Presario C700 up on the corner.
```

2) Wireless Brand, Model, and Wireless Chipset

```
bbanzai@little-sparky:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


bbanzai@little-sparky:~$ lsusb

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 001: ID 0000:0000
```  


3) Check Interface

```
bbanzai@little-sparky:~$ ifconfig

ath0      Link encap:Ethernet  HWaddr 00:1f:3a:26:8f:1f  

          inet6 addr: fe80::21f:3aff:fe26:8f1f/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



ath0:avahi Link encap:Ethernet  HWaddr 00:1f:3a:26:8f:1f  

          inet addr:169.254.3.221  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1



eth0      Link encap:Ethernet  HWaddr 00:1b:38:ff:2f:e3  

          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::21b:38ff:feff:2fe3/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:3577 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3967 errors:0 dropped:0 overruns:1 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:3240181 (3.0 MB)  TX bytes:1542905 (1.4 MB)

          Interrupt:20 Base address:0x1000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1652 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1652 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:82600 (80.6 KB)  TX bytes:82600 (80.6 KB)



wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-26-8F-1F-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:280 

          RX bytes:0 (0.0 B)  TX bytes:6546 (6.3 KB)

          Interrupt:20 



bbanzai@little-sparky:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wifi0     no wireless extensions.



ath0      IEEE 802.11g  ESSID:"mitchell"  Nickname:""

          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   

          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  

          Retry:off   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



4) Check for Modules

```
bbanzai@little-sparky:~$ lsmod

Module                  Size  Used by

i915                   32640  2 

drm                    82452  3 i915

binfmt_misc            12808  1 

rfcomm                 41744  2 

l2cap                  25728  13 rfcomm

bluetooth              61028  4 rfcomm,l2cap

ppdev                  10372  0 

acpi_cpufreq           10796  1 

cpufreq_stats           7104  0 

ipv6                  268036  10 

cpufreq_userspace       5284  0 

cpufreq_ondemand        9740  1 

freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand

cpufreq_conservative     8712  0 

cpufreq_powersave       2688  0 

sbs                    15112  0 

sbshc                   7680  1 sbs

container               5632  0 

dock                   11280  0 

wlan_scan_sta          16000  1 

ath_rate_sample        16128  1 

ath_pci               251960  0 

wlan                  236528  4 wlan_scan_sta,ath_rate_sample,ath_pci

ath_hal               305376  3 ath_rate_sample,ath_pci

parport_pc             36260  0 

lp                     12324  0 

parport                37832  3 ppdev,parport_pc,lp

af_packet              23812  6 

joydev                 13120  0 

snd_hda_intel         346264  2 

serio_raw               7940  0 

evdev                  13056  7 

snd_pcm_oss            42144  0 

snd_mixer_oss          17920  1 snd_pcm_oss

psmouse                40336  0 

pcspkr                  4224  0 

snd_pcm                78724  2 snd_hda_intel,snd_pcm_oss

snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

snd_hwdep              10500  1 snd_hda_intel

iTCO_wdt               13092  0 

iTCO_vendor_support     4868  1 iTCO_wdt

snd_seq_dummy           4868  0 

snd_seq_oss            35584  0 

snd_seq_midi            9376  0 

snd_rawmidi            25760  1 snd_seq_midi

snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi

snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              24836  2 snd_pcm,snd_seq

snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

video                  19856  0 

output                  4736  1 video

wmi_acer                9644  0 

battery                14212  0 

ac                      6916  0 

button                  9232  0 

shpchp                 34452  0 

pci_hotplug            30880  1 shpchp

soundcore               8800  1 snd

intel_agp              25492  1 

agpgart                34760  3 drm,intel_agp

iptable_nat             8324  0 

nf_nat                 20396  1 iptable_nat

nf_conntrack_ipv4      19208  2 iptable_nat

nf_conntrack           66752  3 iptable_nat,nf_nat,nf_conntrack_ipv4

iptable_mangle          3712  0 

iptable_filter          3840  0 

ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter

x_tables               16132  2 iptable_nat,ip_tables

ext3                  136968  1 

jbd                    48404  1 ext3

mbcache                 9600  1 ext3

sr_mod                 17956  0 

cdrom                  37408  1 sr_mod

ata_generic             8324  0 

sg                     36880  0 

sd_mod                 30720  3 

ata_piix               19588  0 

8139cp                 24704  0 

ahci                   28548  2 

pata_acpi               8320  0 

libata                159728  4 ata_generic,ata_piix,ahci,pata_acpi

scsi_mod              151692  4 sr_mod,sg,sd_mod,libata

8139too                27648  0 

mii                     6400  2 8139cp,8139too

ehci_hcd               37900  0 

uhci_hcd               27024  0 

usbcore               146412  3 ehci_hcd,uhci_hcd

thermal                16796  0 

processor              36616  4 acpi_cpufreq,thermal

fan                     5636  0 

fbcon                  42912  0 

tileblit                3584  1 fbcon

font                    9472  1 fbcon

bitblit                 6784  1 fbcon

softcursor              3072  1 bitblit

fuse                   50708  3
```

5) Kernel Boot Messages

... Okay, this gave me such a lengthy response it completely scrolled out of my terminal window.  That seems like far too much data to copy/paste here, so if someone needs this, tell me how to run a more dedicated and specific dmesg command, and I'll be happy to post it.  The hint given in the initial Howto didn't get me any response.

6) Network Configuration

```
bbanzai@little-sparky:~$ sudo lshw -C network

[sudo] password for bbanzai: 

  *-network               

       description: Wireless interface

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: wifi0

       version: 01

       serial: 00:1f:3a:26:8f:1f

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

  *-network

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 1

       bus info: pci@0000:02:01.0

       logical name: eth0

       version: 10

       serial: 00:1b:38:ff:2f:e3

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.105 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```


7) Scan for Networks

```
bbanzai@little-sparky:~$ iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wifi0     Interface doesn't support scanning.



ath0      No scan results
```



(which is bunk, by the way, because every other wireless machine in the apartment reads at least 5 networks, so I know they're there, my machine just can't see them)

8) Ubuntu Version

```
bbanzai@little-sparky:~$ lsb_release -d

Description:	Ubuntu 8.04.3 LTS
```


9) Kernel/architecture

```
bbanzai@little-sparky:~$ uname -mr

2.6.24-25-generic i686
```


10) Restarting the Network

```
bbanzai@little-sparky:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...

   ...done.

 * Starting the Firestarter firewall...

   ...fail!

run-parts: /etc/network/if-down.d/50firestarter exited with return code 2

There is already a pid file /var/run/dhclient.eth0.pid with pid 4317

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wifi0: unknown hardware address type 801

wifi0: unknown hardware address type 801

Listening on LPF/eth0/00:1b:38:ff:2f:e3

Sending on   LPF/eth0/00:1b:38:ff:2f:e3

Sending on   Socket/fallback

DHCPRELEASE on eth0 to 192.168.1.1 port 67

 * Stopping the Firestarter firewall...

   ...done.

 * Starting the Firestarter firewall...

   ...fail!

run-parts: /etc/network/if-down.d/50firestarter exited with return code 2

There is already a pid file /var/run/dhclient.ath0.pid with pid 6029

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wifi0: unknown hardware address type 801

wifi0: unknown hardware address type 801

Listening on LPF/ath0/00:1f:3a:26:8f:1f

Sending on   LPF/ath0/00:1f:3a:26:8f:1f

Sending on   Socket/fallback

DHCPRELEASE on ath0 to 192.168.1.1 port 67

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wifi0: unknown hardware address type 801

wifi0: unknown hardware address type 801

Listening on LPF/eth0/00:1b:38:ff:2f:e3

Sending on   LPF/eth0/00:1b:38:ff:2f:e3

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

DHCPOFFER of 192.168.1.105 from 192.168.1.1

DHCPREQUEST of 192.168.1.105 on eth0 to 255.255.255.255 port 67

DHCPACK of 192.168.1.105 from 192.168.1.1

bound to 192.168.1.105 -- renewal in 33992 seconds.

 * Stopping the Firestarter firewall...

   ...done.

 * Starting the Firestarter firewall...

   ...fail!

run-parts: /etc/network/if-up.d/50firestarter exited with return code 2

There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wifi0: unknown hardware address type 801

wifi0: unknown hardware address type 801

Listening on LPF/ath0/00:1f:3a:26:8f:1f

Sending on   LPF/ath0/00:1f:3a:26:8f:1f

Sending on   Socket/fallback

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

 * Stopping the Firestarter firewall...

   ...done.

 * Starting the Firestarter firewall...

   ...fail!

run-parts: /etc/network/if-up.d/50firestarter exited with return code 2

                                                                         [ OK ]
```


Okay, the number of "fail" messages in starting the firewall?  Concerning to me.  But that's not specifically the purpose of this post, just an unhappy side effect of all this information gathering.

The details: In the wee hours of this morning, my wicd network manager (which had been the only method by which I could get my wireless to work a year ago, but I'm not inherently attached to it) suddenly told me it couldn't find any networks.  I'd been happily cruising along only a few minutes before, so I knew that was bunk.

I rebooted, but nothing doing.  I did the reset procedure that I have to do after a kernel upgrade (one of the drawbacks of the wicd method I had to use) and rebooted, but nothing doing once again.  I went to bed and let it cool off, wondering if overheated components might be some kind of physical fault, but this afternoon when I finally got to booting it up again, still nothing doing.

It has cut out on me in mid-browsing once before, about a week ago, again without warning or explanation, but the reset procedure fixed it at that time.

I have been working fine with my rather clunky use of wicd, which again, at the time I was getting rolling a little over a year ago, was the one way I could get it to work.  However, it's been a year; if there are better ways to do it, by all means, let's work it.  Right now, it seems like I'm trying to get my machine rolling all over again.

Damn, that's long.

Anyway... suggestions?

---

### Post by E. Mark Mitchell on 2009-11-09
Do I need to bump it?  It was posted past local midnight yesterday, and it's been up all of yesterday and today (it's local early evening now).  Aren't there usually some views or another?

Do we bump for attention here, if there's no nibbles?  I'm not sure about how you handle things like that on this board...

---

