---
title: "Connecting to an unencrypted wireless network from a Command Line Installation"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by malangbaba on 2010-01-07
I am trying to do a command line installation.
Finished the installation and my wireless card wasnt working
Did a "sudo ifconfig wlan0 up" and got it working
But for some reason wireless-tools is not installed thus I dont have iwconfig, iwlist, etc.

The wireless works and connects fine off a liveUSB
So I am going to give info from this liveUSB run and maybe someone can suggest how I can set the right settings on the Command Line Installation I presume in the **etc/network/interfaces**

HP 5310m (no CD/DVD)
Karmic Koala
2.6.31-14-generic i686 32-bit


lspci
> 02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection


lsusb
> Bus 002 Device 002: ID 08ec:0020 M-Systems Flash Disk Pioneers TravelDrive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:26:22:ac:02:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:39:f8:a4  
          inet addr:192.168.10.107  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe39:f8a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2474724 (2.4 MB)  TX bytes:239389 (239.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-D6-39-F8-A4-33-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"TRENDnet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:D1:67:5C:0E   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  Noise level=-76 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lsmod | grep "wlan0" yields nothing

lsmod
> Module                  Size  Used by
nls_utf8                1568  1 
isofs                  31620  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
arc4                    1660  2 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ecb                     2524  2 
joydev                 10272  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               11228  0 
lis3lv02d               7452  1 hp_accel
iwlagn                109052  0 
uvcvideo               59080  0 
input_polldev           3716  1 lis3lv02d
videodev               36736  1 uvcvideo
psmouse                56180  0 
iwlcore               112508  1 iwlagn
mac80211              181236  2 iwlagn,iwlcore
led_class               4096  2 hp_accel,iwlcore
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            14496  2 uvcvideo,videodev
serio_raw               5280  0 
iptable_filter          3100  0 
dm_crypt               12928  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
ip_tables              11692  1 iptable_filter
cfg80211               93052  3 iwlagn,iwlcore,mac80211
x_tables               16544  1 ip_tables
squashfs               22912  1 
aufs                  149420  1 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52544  2 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
sky2                   46560  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
output                  2780  1 video


dmesg | grep "wlan0"
> 
[   37.876681] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.542987] wlan0: authenticate with AP 00:14:d1:67:5c:0e
[   86.544889] wlan0: authenticated
[   86.544892] wlan0: associate with AP 00:14:d1:67:5c:0e
[   86.547556] wlan0: RX AssocResp from 00:14:d1:67:5c:0e (capab=0x421 status=0 aid=8)
[   86.547558] wlan0: associated
[   86.549327] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   97.060184] wlan0: no IPv6 routers present


sudo lshw -C network
>   *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:24:d6:39:f8:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.10.107 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:90700000-90701fff


iwlist scan
> wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:67:5C:0E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"TRENDnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a4c148019b
                    Extra: Last beacon: 26324ms ago
                    IE: Unknown: 00085452454E446E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD7F0050F204104A0001101044000101103B00010310470010630412531019200612280014D1675C0E102100085452454E446E65741023000A5445572D34333242525010240004313030301042000D32303037303431332D303030311054000800060050F20400011011000F576972656C65737320526F75746572100800020086
                    IE: Unknown: DD0700E04C01020300

here is my current etc/network/interfaces from the command line installation:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
 
iface wlan0 inet static
	essid "TRENDnet"
	mode managed
	channel 01
	key open
	address 192.168.10.107
	netmask 255.255.255.0
	network 192.168.10.0
	broadcast 192.168.10.255
	gateway 192.168.10.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.10.1
auto wlan0

---

### Post by malangbaba on 2010-01-08
SOLVED!

Went and got the wireless-tools, libc6 (udev), libiw29 packages from packages.ubuntu.com

installed them on CL through dpkg

got wireless-tools on

now wireless works!

---

