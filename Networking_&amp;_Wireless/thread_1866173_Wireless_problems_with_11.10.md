---
title: "Wireless problems with 11.10"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by keyem on 2011-10-21
Hey out there,

since I installed 11.10 on my notebook I have problems connecting with my university network. Most of the time it doesn't connect at all, when it does connection almost always breaks after a few seconds. Sometimes after several tries i can establish a stable connection.

I don't have any problems connecting to my network at home or to my android hotspot. With 10.04 it also worked fine at university. 11.10 (32 and 64bit) just fails.

Hope somebody can help...

**1 ) Machine Brand and Model (PC/Laptop)**:
```
lenovo ThinkPad T400
```**2 ) Wireless Brand, Model and Wireless Chipset:**
```
emkey@emkey-ThinkPad-T400:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
emkey@emkey-ThinkPad-T400:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:074f Microsoft Corp. 
Bus 004 Device 006: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II

```[B]3 ) check interface:
[/B]```
emkey@emkey-ThinkPad-T400:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:27:13:69:9e:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123553 (123.5 KB)  TX bytes:123553 (123.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c6:80:cf:d8  
          inet addr:192.168.43.113  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c6ff:fe80:cfd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1679311 (1.6 MB)  TX bytes:532733 (532.7 KB)

emkey@emkey-ThinkPad-T400:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"emkey"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 04:46:65:54:1D:FF   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-13 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:158   Missed beacon:0

```[B]4 ) Check for modules:
[/B]```
emkey@emkey-ThinkPad-T400:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
dm_crypt               23199  0 
ppdev                  17113  0 
joydev                 17693  0 
arc4                   12529  2 
bnep                   18436  2 
rfcomm                 47946  8 
thinkpad_acpi          81819  0 
snd_seq_midi           13324  0 
pcmcia                 49378  0 
snd_rawmidi            30547  1 snd_seq_midi
iwlagn                314213  0 
mac80211              310872  1 iwlagn
snd_hda_codec_conexant    62197  1 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
cfg80211              199587  2 iwlagn,mac80211
psmouse                73882  0 
serio_raw              13166  0 
snd_timer              29991  2 snd_seq,snd_pcm
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd                    68266  14 thinkpad_acpi,snd_rawmidi,snd_hda_codec_conexant,snd_seq,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              12680  1 snd
nvram                  14413  1 thinkpad_acpi
tpm_tis                18546  0 
binfmt_misc            17540  1 
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
ahci                   26002  1 
libahci                26861  1 ahci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
wmi                    19256  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
e1000e                160535  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
emkey@emkey-ThinkPad-T400:~$ clear

emkey@emkey-ThinkPad-T400:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
dm_crypt               23199  0 
ppdev                  17113  0 
joydev                 17693  0 
arc4                   12529  2 
bnep                   18436  2 
rfcomm                 47946  8 
thinkpad_acpi          81819  0 
snd_seq_midi           13324  0 
pcmcia                 49378  0 
snd_rawmidi            30547  1 snd_seq_midi
iwlagn                314213  0 
mac80211              310872  1 iwlagn
snd_hda_codec_conexant    62197  1 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
cfg80211              199587  2 iwlagn,mac80211
psmouse                73882  0 
serio_raw              13166  0 
snd_timer              29991  2 snd_seq,snd_pcm
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd                    68266  14 thinkpad_acpi,snd_rawmidi,snd_hda_codec_conexant,snd_seq,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              12680  1 snd
nvram                  14413  1 thinkpad_acpi
tpm_tis                18546  0 
binfmt_misc            17540  1 
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
ahci                   26002  1 
libahci                26861  1 ahci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
wmi                    19256  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
e1000e                160535  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915

```[B]5 ) Kernel boot messages
[/B]way too long with thousands of failed connections...

[B]6 ) Network configuration
[/B]```
emkey@emkey-ThinkPad-T400:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:27:13:69:9e:bb
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fc000000-fc01ffff memory:fc025000-fc025fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c6:80:cf:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=8.83.5.1 build 33692 ip=192.168.43.113 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f4300000-f4301fff

```[B]7 ) Scan for networks:
[/B]too long again...

[B]8 ) Ubuntu Version: 
[/B]```
emkey@emkey-ThinkPad-T400:~$ lsb_release -d
Description:    Ubuntu 11.10

```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]```
emkey@emkey-ThinkPad-T400:~$ uname -mr
3.0.0-12-generic x86_64

```[B]10 ) Restarting the network:
[/B]```
emkey@emkey-ThinkPad-T400:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```

---

