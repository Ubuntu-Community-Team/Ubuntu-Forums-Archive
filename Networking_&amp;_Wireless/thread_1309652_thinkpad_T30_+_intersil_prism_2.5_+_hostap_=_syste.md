---
title: "thinkpad T30 + intersil prism 2.5 + hostap = system hang"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by utylerr on 2009-11-01
Hello,

I'm trying to get my T30 laptop with the standard built-in intersil prism 2.5 wavelan wireless card to work with WPA2 authentication.

I have flashed the firmware of the prism card to v1.8.4 (see [http://junsun.net/linux/intersil-prism/](http://junsun.net/linux/intersil-prism/)), and this was working correctly for me in early Jaunty releases, but with some patch or other it now does not work.

The standard workaround (<http://ubuntuforums.org/showthread.php?t=446010>, <https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan>) is to blacklist orinoco and associated modules so that the hostap modules will be used to interact with the card. This workaround appears to be standardized now to the point that if you install the optional hostap-utils package via synaptic then it will create an /etc/modprobe.d/hostap-utils.conf file which blacklists orinoco and associated modules.

As stated, this all worked for me in early Jaunty. As of a patch to Jaunty a month or so ago, and still with Kosmic, it now causes my machine to hang whenever the hostap module tries to talk to the card. From a practical standpoint, this means that if I blacklist the orinoco drivers (per the workaround) then the machine will no longer boot. If I leave them un-blacklisted, but attempt to remove them via rmmod, and then re-load hostap with modprobe, the machine does a hard hang and will no longer respond.

This happens on two different T30 laptops (I bought a second one assuming that the first had some kind of hardware problem), so I suspect it is a kernel bug and not a hardware error.

Any help would be appreciated.


Standard diagnostic info and command output is below, though note that this is the pre-workaround status, with both orinoco and hostap modules loaded, and orinoco is the one that has grabbed the wireless card.

- machine brand/model/etc.
IBM Thinkpad T30 Type 2366 model 41U

- lspci
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

- ifconfig

eth0      Link encap:Ethernet  HWaddr 00:09:6b:90:c5:e7  
          inet6 addr: fe80::209:6bff:fe90:c5e7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9082 (9.0 KB)  TX bytes:17907 (17.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:05:3c:08:cf:39  
          inet6 addr: fe80::205:3cff:fe08:cf39/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:420 (420.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

- iwconfig

eth1      IEEE 802.11b  ESSID:"wintermute"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/92  Signal level=-53 dBm  Noise level=-144 dBm
          Rx invalid nwid:0  Rx invalid crypt:726  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0


- lsmod

Module                  Size  Used by
binfmt_misc             8356  1 
pcmcia                 36808  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
hostap_pci             48652  0 
snd_rawmidi            22208  1 snd_seq_midi
hostap                103360  1 hostap_pci
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
lib80211                6432  2 hostap_pci,hostap
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
orinoco_pci             4700  0 
thinkpad_acpi          67108  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
orinoco                63600  1 orinoco_pci
soundcore               7264  1 snd
led_class               4096  1 thinkpad_acpi
lp                      8964  0 
psmouse                56180  0 
yenta_socket           24200  2 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
nsc_ircc               20976  0 
irda                  189564  1 nsc_ircc
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
ppdev                   6688  0 
parport_pc             31940  1 
shpchp                 32272  0 
crc_ccitt               1852  1 irda
serio_raw               5280  0 
nvram                   7528  1 thinkpad_acpi
parport                35340  3 lp,ppdev,parport_pc
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
e100                   32452  0 
mii                     5212  1 e100
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp


- dmesg | grep "orinoco"

[   12.159509] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   12.262095] orinoco_pci 0.15 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[   12.262167] orinoco_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.220736] eth1: orinoco_pci at 0000:02:02.0

- iwlist scan

  *-network:0
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 01
       serial: 00:05:3c:08:cf:39
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.8.4 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:f8000000-f8000fff(prefetchable)


- lsb_release -d

Description:	Ubuntu 9.10

- uname -mr

2.6.31-14-generic i686

---

### Post by anystupidname1 on 2009-11-27
Make that three T30 laptops. (type 2367 in my case)

> 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
> lsmod
Module                  Size  Used by
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
radeon                636000  2 
ttm                    36212  1 radeon
hostap_pci             48652  0 
hostap                103360  1 hostap_pci
snd_seq_oss            28576  0 
pcmcia                 36808  0 
drm                   159584  4 radeon,ttm
snd_seq_midi            6432  0 
lib80211                6432  2 hostap_pci,hostap
thinkpad_acpi          67108  0 
binfmt_misc             8356  1 
snd_rawmidi            22208  1 snd_seq_midi
yenta_socket           24200  2 
rsrc_nonstatic         11644  1 yenta_socket
orinoco_pci             4700  0 
led_class               4096  1 thinkpad_acpi
video                  19380  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ppdev                   6688  0 
output                  2780  1 video
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
i2c_algo_bit            5760  1 radeon
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp
psmouse                56500  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
nvram                   7528  1 thinkpad_acpi
orinoco                63600  1 orinoco_pci
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               5280  0 
shpchp                 32272  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
irda                  189564  0 
crc_ccitt               1852  1 irda
e100                   32452  0 
mii                     5212  1 e100

I wish I could add more but the only thing you didn't mention that I noticed was the error during startup:
> BUG: soft lockup - CPU#0 stuck for 61s!
(incomplete)

Did your hangs manifest themselves in a different way?
(except the ones when you load hostap_pci manually of course)

I'll post a comment in your bug too [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461654](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461654)

Found this too [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432636](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432636)

possibly related?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/62685](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/62685)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/46228](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/46228)

---

### Post by utylerr on 2009-11-28
This does seem to be a known bug; someone also noted this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282840](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282840)

---

### Post by ktp on 2009-12-26
I hope this gets fixed soon...I am seeing lots of regression in 9.10...also seeing issues with USB TV tuner not working.

Maybe time to get new hardware...but Ubuntu is so good on old stuff =)

---

### Post by tomsky007 on 2010-01-11
Hi,
I have the very same problem on a Fujitsu Lifebook S6010 and a Prism 2.5 WLAN miniPCI card. In the end I got hostap working by compiling a new kernel from the 2.6.31.11 sources. It's cumbersome but it worked for me. I hope they'll fix the the karmic kernel soon though.

---

