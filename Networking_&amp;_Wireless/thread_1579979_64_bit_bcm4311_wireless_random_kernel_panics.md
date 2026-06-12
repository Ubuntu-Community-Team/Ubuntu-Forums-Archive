---
title: "64 bit bcm4311 wireless random kernel panics"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by glennvan on 2010-09-22
Okay, so I have this weird issue which only appears when I am using 64 bit Ubuntu.  Every now and then my laptop seems to go into a kernel panic (system unresponsive, numlock and scrollock lights flash repetitively) only when I am using the broadcom wireless.  I can connect to my wireless router and use the internet and local network, but eventually, kablamo, crash, bang, boom.  The only way out of the crash is to power off completely.  After repowering, the wireless network is fine until the next crash.  There does not seem to be a pattern or time period to cause this crash either.

I have purged network manager(which I couldn't get to use my wireless) and am using wicd, which allows me to connect wirelessly.

Here is the details of my system:

Dell inspiron 1520
lspci (snipped)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
        Subsystem: Dell Device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, ssb

ifconfig (snipped)
eth1      Link encap:Ethernet  HWaddr 00:1e:4c:75:b6:b0  
          inet addr:192.168.0.35  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe75:b6b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26444 errors:0 dropped:0 overruns:0 frame:1037
          TX packets:24606 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24911388 (24.9 MB)  TX bytes:3108943 (3.1 MB)
          Interrupt:17 Base address:0xc000 

iwconfig (snipped)
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:209  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

lsmod (complete)
Module                  Size  Used by
usb_storage            49961  0 
michael_mic             2164  8 
arc4                    1473  4 
hidp                   14218  1 
rfcomm                 40393  4 
binfmt_misc             7960  1 
sco                     9649  2 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34806  21 hidp,rfcomm,bnep
vmnet                  46870  13 
ppdev                   6375  0 
parport_pc             29958  0 
vmblock                12995  1 
vsock                  43304  0 
vmci                   60063  1 vsock
vmmon                  79433  0 
joydev                 11072  0 
snd_hda_codec_idt      61450  1 
snd_hda_intel          25773  2 
snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
dell_wmi                2177  0 
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
b44                    30687  0 
snd_rawmidi            23420  1 snd_seq_midi
ssb                    45395  1 b44
mii                     5237  1 b44
lib80211_crypt_tkip     8676  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wl                   1964968  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62595  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11956  1 videodev
btusb                  13001  4 
bluetooth              58685  10 hidp,rfcomm,sco,bnep,l2cap,btusb
ricoh_mmc               3416  0 
dell_laptop             7941  0 
dcdbas                  6886  1 dell_laptop
psmouse                64576  0 
serio_raw               4918  0 
snd                    71187  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3764  1 sdhci
nvidia              10832442  50 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lib80211                6151  2 lib80211_crypt_tkip,wl
lp                      9336  0 
video                  20623  0 
output                  2503  1 video
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29095  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41084  0 
hid                    83472  2 hidp,usbhid
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
ahci                   37870  3 

dmseg |grep "eth1"
[   14.070928] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:ae:e7:00
[   14.077465] udev: renamed network interface eth0 to eth1
[   14.126566] udev: renamed network interface eth1_rename to eth0
[   28.311456] bridge-eth1: is a Wireless Adapter
[   28.311460] bridge-eth1: up
[   28.312073] bridge-eth1: attached
[   36.213593] bridge-eth1: disabling the bridge on dev down
[   36.240050] bridge-eth1: down
[   36.240089] bridge-eth1: detached
[   36.420294] bridge-eth1: is a Wireless Adapter
[   36.420297] bridge-eth1: up
[   36.420300] bridge-eth1: attached
[   36.460983] bridge-eth1: disabling the bridge on dev down
[   36.490086] bridge-eth1: down
[   36.490130] bridge-eth1: detached
[   46.690214] eth1: no IPv6 routers present
[   52.312789] bridge-eth1: is a Wireless Adapter
[   52.312793] bridge-eth1: up
[   52.312798] bridge-eth1: attached

sudo lshw -c network
[sudo] password for glenn: 
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:4c:75:b6:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.35 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ae:e7:00
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff

iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

lsb_release -d
Description:    Ubuntu 10.04.1 LTS

uname -mr
2.6.32-25-generic x86_64

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                      [ OK ]


Thanks in advance...


Glenn

---

### Post by glennvan on 2010-10-04
Just a quick update, I downloaded the 10.10 Kubuntu and Ubuntu and installed to external usb drive and the same issue appears, but much sooner.  Also it appears that the fwcutter is autmagically installed now, and all you can install is the sta driver...

---

