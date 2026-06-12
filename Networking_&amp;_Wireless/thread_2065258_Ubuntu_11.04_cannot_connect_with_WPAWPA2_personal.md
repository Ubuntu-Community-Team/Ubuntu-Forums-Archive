---
title: "Ubuntu 11.04 cannot connect with WPA/WPA2 personal"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by jppinto on 2012-10-01
My laptop has been connecting to my home wireless network with no problem until 5 days ago, when it stopped to be able to connect. In Network-Manager it sees the correct wireless network (wich is already pre-programmed with the password), lets me select it but after some time it says "Wireless network: Disconnected. You are now offline"

In attach I send more information including dmesg information.

All other laptops (and android phones) connect with no problems to the same wireless network. Nevertheless the router was already rebooted as well as the laptop.

The wired connection works fine.

I have tried to use Wicd instead of network-manager also without success.

My libssl is: 0.9.8

Thank you for your attention and help. Please do help... :)

Joao



Details:

PC: Toshiba Portege R830-10P
Router:
   Firmware	  	OpenWrt Kamikaze - With X-Wrt Extensions 7.09
   Kernel	  	Linux 2.4.34 #3 Sun Sep 30 20:33:21 CEST 2007
   MAC	  	  	00:1D:7E:60:9E:E2
   Device	 	Linksys WRT54G/GS/GL
   Board	 	Broadcom BCM5352 chip rev 0


lspci: -----------------------------------------------------------------

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 6 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
01:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
04:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

lsusb: -----------------------------------------------------------------

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0930:1314 Toshiba Corp. 
Bus 001 Device 004: ID 0bda:58f5 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 08ff:168b AuthenTec, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci --nn | grep -i "network":-------------------------------------------

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
04:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)

ifconfig: ----------------------------------------------------------------

eth0      Link encap:Ethernet  HWaddr e8:9d:87:9f:bc:21  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9d:87ff:fe9f:bc21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17186688 (17.1 MB)  TX bytes:2120571 (2.1 MB)
          Interrupt:20 Memory:c4800000-c4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:167989 (167.9 KB)  TX bytes:167989 (167.9 KB)

wlan0     Link encap:Ethernet  HWaddr 88:53:2e:08:8a:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79566 (79.5 KB)  TX bytes:16875 (16.8 KB)

iwconfig: ----------------------------------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

lsmod: -------------------------------------------------------------------

Module                  Size  Used by
aesni_intel            55663  0 
cryptd                 20647  1 aesni_intel
aes_x86_64             17208  1 aesni_intel
aes_generic            34183  2 aesni_intel,aes_x86_64
rfcomm                 48645  8 
binfmt_misc            17646  1 
bnep                   18517  2 
vboxnetadp             13382  1390688138 [permanent]
vboxnetflt             28297  522378510 [permanent]
vboxdrv               268275  655280917 vboxnetadp,vboxnetflt,[permanent]
parport_pc             37530  0 
ppdev                  17141  0 
snd_hda_codec_hdmi     33027  1 
snd_hda_codec_realtek   332834  1 
btusb                  18712  2 
bluetooth             165324  23 rfcomm,bnep,btusb
tpm_infineon           17508  0 
arc4                   12529  2 
snd_hda_intel          34236  2 
snd_hda_codec         106725  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
i915                  565970  3 
drm_kms_helper         43171  1 i915
uvcvideo               69124  0 
videodev               92905  1 uvcvideo
cdc_ncm                17526  0 
v4l2_compat_ioctl32    17341  1 videodev
cdc_wdm                17572  0 
cdc_acm                22911  0 
usbnet                 26147  1 cdc_ncm
snd_hwdep              13782  1 snd_hda_codec
snd_pcm                98306  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13370  0 
snd_rawmidi            30488  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 18043  0 
drm                   238079  4 i915,drm_kms_helper
snd_seq                62088  2 snd_seq_midi,snd_seq_midi_event
snd_timer              30240  2 snd_pcm,snd_seq
tpm_tis                18545  0 
snd_seq_device         14528  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                70193  0 
tpm                    22301  2 tpm_infineon,tpm_tis
toshiba_bluetooth      12807  0 
i2c_algo_bit           13436  1 i915
tpm_bios               13707  1 tpm
serio_raw              13294  0 
toshiba_acpi           18577  0 
sparse_keymap          13995  1 toshiba_acpi
iwlagn                317305  0 
mac80211              310164  1 iwlagn
cfg80211              196651  2 iwlagn,mac80211
video                  20027  1 i915
snd                    68651  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
coretemp               17875  0 
soundcore              12680  1 snd
snd_page_alloc         18572  2 snd_hda_intel,snd_pcm
mei                    42004  0 
lp                     17868  0 
parport                42788  3 parport_pc,ppdev,lp
usbhid                 48081  0 
hid                   100109  1 usbhid
xhci_hcd               88842  0 
ahci                   30380  3 
libahci                31326  1 ahci
sdhci_pci              18112  0 
sdhci                  32450  1 sdhci_pci
e1000e                161918  0 

dmesg: (extract from when I try to connect with network manager) -------------------------------------------------------------------------

[ 5392.400108] wlan0: deauthenticating from 00:1d:7e:60:9e:e4 by local choice (reason=3)
[ 5392.401172] wlan0: authenticate with 00:1d:7e:60:9e:e4 (try 1)
[ 5392.403930] wlan0: authenticated
[ 5392.404261] wlan0: associate with 00:1d:7e:60:9e:e4 (try 1)
[ 5392.406988] wlan0: RX AssocResp from 00:1d:7e:60:9e:e4 (capab=0x411 status=0 aid=3)
[ 5392.406997] wlan0: associated
[ 5392.419319] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5394.388524] type=1400 audit(1349108964.926:28): apparmor="DENIED" operation="open" parent=12736 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=12820 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[ 5403.349533] wlan0: no IPv6 routers present
[ 5403.380183] wlan0: deauthenticating from 00:1d:7e:60:9e:e4 by local choice (reason=3)
[ 5403.609574] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 5403.609589] cfg80211: Restoring regulatory settings
[ 5403.609601] cfg80211: Calling CRDA to update world regulatory domain
[ 5403.616964] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 5403.616982] cfg80211: World regulatory domain updated:
[ 5403.616986] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5403.616994] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5403.617001] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5403.617007] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5403.617013] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5403.617019] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

sudo lshw -C network ------------------------------------------------------

  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: e8:9d:87:9f:bc:21
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:08:8a:36
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-0300-generic firmware=17.168.5.2 build 35905 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:c2600000-c2601fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ncm driverversion=01-June-2011 firmware=CDC NCM link=no multicast=yes

lsb_release -d ----------------------------------------------------------

Description:	Ubuntu 11.04

uname -mr ---------------------------------------------------------------

3.0.0-0300-generic x86_64

uname -a ----------------------------------------------------------------

Linux Lia 3.0.0-0300-generic #201107220917 SMP Fri Jul 22 09:20:45 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

