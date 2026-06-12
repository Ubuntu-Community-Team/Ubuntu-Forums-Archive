---
title: "network disabled, but works fine in normal karmic"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by pip-le-pip on 2010-03-08
[B]hi all!

My problem: no wlan connection with ubuntu studio. normal karmic is fine (it's on the same laptop and i'm using it this moment).

I believe it's got something to do with the "*-network DISABLED" thingy in sudo lshw -c network (see below) but can't figure out how to solve this.[/B]  

I tried installing the linux driver from the realtek website -no effect.

tried this script ([http://acm.cse.lehigh.edu:8080/~jhw204/hardy-r8168):]("http://acm.cse.lehigh.edu:8080/%7Ejhw204/hardy-r8168%29:")
> 
pip@localhost:~/Desktop/r8168_scripts$ sudo ./switchmods
Attempting to remove running r8168 and r8169 modules if loaded...
Attempting to move /lib/modules/2.6.31-9-rt/kernel/drivers/net/r8169.ko to /lib/modules/2.6.31-9-rt/kernel/drivers/net/r8169.ko.bak.
Blacklisting r8169 in /etc/modprobe.d/blacklist...
Creating a tmp dir in which to build the module...
Checking for gcc and linux-headers-2.6.31-9-rt...    OK
Attempting to build the module...Could not build module.didn't work.

system info (according to the "how to post an wireless issue" thread):

> pip@localhost:~$ lspci
...
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
...

pip@localhost:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  Hardware Adresse 00:19:db:98:f5:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pip@localhost:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"wlan0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pip@localhost:~$ lsmod
Module                  Size  Used by
ppdev                   6712  0 
sha256_generic         11572  0 
aes_i586                8116  81 
snd_hda_codec_si3054     4692  1 
snd_hda_codec_realtek   203576  1 
snd_hda_intel          26824  2 
snd_hda_codec          76052  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7416  1 snd_hda_codec
snd_pcm_oss            38112  0 
snd_mixer_oss          16564  1 snd_pcm_oss
aes_generic            27476  1 aes_i586
cbc                     3508  79 
arc4                    1652  2 
ecb                     2516  3 
snd_pcm                75096  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2680  0 
rt73usb                26392  0 
snd_seq_oss            28736  0 
crc_itu_t               1844  1 rt73usb
snd_seq_midi            6560  0 
snd_rawmidi            22240  1 snd_seq_midi
snd_seq_midi_event      7092  2 snd_seq_oss,snd_seq_midi
rt2x00usb              11572  1 rt73usb
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00lib              29844  2 rt73usb,rt2x00usb
snd_timer              22040  2 snd_pcm,snd_seq
iptable_filter          3092  0 
pcmcia                 35560  0 
ip_tables              11652  1 iptable_filter
snd_seq_device          6944  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           24288  1 
sdhci_pci               7188  0 
lp                      9604  0 
parport                35976  2 ppdev,lp
dm_crypt               12728  1 
input_polldev           3772  1 rt2x00lib
joydev                 10304  0 
mac80211              183336  2 rt2x00usb,rt2x00lib
snd                    60740  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         11860  1 yenta_socket
sdhci                  17656  1 sdhci_pci
x_tables               17176  1 ip_tables
pcmcia_core            36940  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               4088  2 rt2x00lib,sdhci
psmouse                56460  0 
soundcore               7968  1 snd
cfg80211               93508  2 rt2x00lib,mac80211
serio_raw               5432  0 
snd_page_alloc          9244  2 snd_hda_intel,snd_pcm
fbcon                  37024  72 
tileblit                2452  1 fbcon
font                    8116  1 fbcon
bitblit                 5204  1 fbcon
softcursor              1748  1 bitblit
i915                  221992  2 
usb_storage            52512  1 
ohci1394               30308  0 
drm                   160512  2 i915
ieee1394               87284  1 ohci1394
i2c_algo_bit            5752  1 i915
r8169                  32152  0 
intel_agp              27516  2 i915
mii                     5204  1 r8169
video                  19244  1 i915
agpgart                35440  2 drm,intel_agp
output                  2836  1 video

pip@localhost:~$ dmesg
...
[   82.574230] ADDRCONF(NETDEV_UP): wlan0: link is not ready

pip@localhost:~$ sudo lshw -c network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:3e:79:42
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:d800(size=256) memory:fe2ff000-fe2fffff memory:fe2c0000-fe2dffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:98:f5:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

pip@localhost:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pip@localhost:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                              There is already a pid file /var/run/dhclient.wlan0.pid with pid 2595
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:db:98:f5:1d
Sending on   LPF/wlan0/00:19:db:98:f5:1d
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:db:98:f5:1d
Sending on   LPF/wlan0/00:19:db:98:f5:1d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory


distro: Ubuntu Studio 9.10 2.6.31-9-rt i686
the connection utility says (when trying to connect):
> "Die Schnittstelle existiert nicht
Stellen Sie sicher, dass es richtig geschrieben und dass es korrekt von Ihrem System unterstützt wird."

-->~"Interface doesn't exist"I'd be very greatful for some help, been on this for 3 days now.

- I installed studio before normal karmic, only installed normal ubuntu to get help :)

oh, laptop is by MSI, can't say wich model.

cheers,
pip

---

### Post by pip-le-pip on 2010-03-08
by the way, I also tried using an USB wlan device by DLINK, no success of course, is also listed as disabled by lshw

---

### Post by pip-le-pip on 2010-03-10
If no one answers, should I give it up and report it as a bug? or is there a problem with my post above?

---

### Post by cchhrriiss121212 on 2010-03-12
Have you installed network manager or wicd? Ubuntu Studio does not come with it installed as it messes with audio work (Xruns in jack).
Plug in to a wired connection and install one of those using synaptic.

---

### Post by pip-le-pip on 2010-03-13
thanks for the reply,

have done what you said, and in addition found out that my user wasn't in the wireless networking group or whatever it's called. now I've got cable connection via network manager, wicd just displays error messages (I'll post them shortly) on startup. 

problem is I share a house with 14 people and don't want to hang around the kitchen all the time where the router is for cable connection ;)

---

### Post by pip-le-pip on 2010-03-13
okay, installed the appropriate driver,
wicd gets past authentication but can't get IP address. I tried all the possibilities from this thread: [http://wicd.net/punbb/viewtopic.php?id=277](http://wicd.net/punbb/viewtopic.php?id=277)
but didn't change a thing...

---

### Post by cchhrriiss121212 on 2010-03-13
I had to reboot in order for wicd to allow a connection. If that does not work then give gnome network manager a try.

---

### Post by pip-le-pip on 2010-03-13
yeah  I think I'll have to do that after I've updated my driver... before network manager didn't find any wlan network, though wicd did. hope it's better now...

getting very frustrated b/c jack is also messing around and I have no clue whatsoever... I really want to stick to linux, but if this doesn't get much better soon (I've been working on it most of the time of 1 1/2 weeks now, often till 4 o'clock in the morning) I see no other possibility than switching back to windoze, which would really be a shame... apart from using the internet, music production is the only reason for me to have a computer at all at the moment...

---

### Post by pip-le-pip on 2010-03-14
hmpf. didn't make a difference...

---

### Post by cchhrriiss121212 on 2010-03-14
As far as I know, the only difference between desktop and studio in terms of networking is the lack of network manager. Perhaps try a fresh install of studio then use gnome network manager as that is what the desktop version uses.

---

