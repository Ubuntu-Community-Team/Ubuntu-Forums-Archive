---
title: "Need to disable IPv6 in 9.10"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by incrediblekarma on 2010-01-08
Hi there. I just switched to Karmic from 7.10 (Fiesty). I tackled the grub2's problems with booting from an ext4 partition with gusto, and got this slick new version up and running. I was suprised to see that this version recognizes my Belkin USB wireless n device "out of the box" which is something previous versions have never done. I was thinking the toughest of my problems was behind me, however the network dialog recognizes every wireless LAN in a 3 block radius (at least that much) with the exception of my own. I played with all my router settings and eventually disabled all security, essentially draping my neighborhood in wifi. My network still went unrecognized and yes, my SSID is broadcasted. I had my suspicions of the problem based on networking issues I've had with previous versions of ubuntu. Namely, that IPv6 is enabled from the word go in ubuntu, which for the now, only seems to cause issues. In previous releases you could edit /etc/modprobe.d/aliases to disable the IPv6, however in 9.10 this file is conspicuously absent. Does anyone know how to disable IPv6 in this release? 

Here's some additional information:

My router worked with 7.10 and is configured for a WPA + WPA2 PSK security setup, using TKIP encrytion and a WPA key. It functions just fine. I would prefer to have it set up with a WPA + WPA2 key with TKIP + AES encryption as well as some other heightened security, but then my Wii/Blackberry/other non-desktop devices don't support this. *shrug* :D Another interesting bug to mention is in 7.10 my wireless connection would only stay connected for some irregular interval before my network settings were overwritten with some crazy long WPA passkey. Is there an fstab-like file I can edit to prevent this if the same problem arises in this version? All other settings remained intact but the passkey, and reentering that or unplugging/replugging the usb device and reentering the key always solved the problem, until the next interval anyway.

> jukebox-zero@jukebox-zero-desktop:~$ lsusb
Bus 001 Device 003: ID 03f0:3307 Hewlett-Packard 
Bus 001 Device 002: ID 050d:815c Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0566:3107 Monterey International Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jukebox-zero@jukebox-zero-desktop:~$ lsmod
Module                  Size  Used by
ndiswrapper           185404  0 
ipt_MASQUERADE          2204  1 
xt_state                1820  1 
ipt_REJECT              2812  2 
xt_tcpudp               2780  4 
nf_nat_h323             6204  0 
nf_conntrack_h323      48904  1 nf_nat_h323
nf_nat_pptp             2844  0 
nf_conntrack_pptp       5984  1 nf_nat_pptp
nf_conntrack_proto_gre     5344  1 nf_conntrack_pptp
nf_nat_proto_gre        2080  1 nf_nat_pptp
nf_nat_tftp             1340  0 
nf_conntrack_tftp       4048  1 nf_nat_tftp
nf_nat_sip              6300  0 
nf_conntrack_sip       17872  1 nf_nat_sip
nf_nat_irc              2012  0 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_nat_ftp              2652  0 
nf_conntrack_ftp        6880  1 nf_nat_ftp
iptable_nat             5500  1 
nf_nat                 17808  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      13352  4 iptable_nat,nf_nat
nf_conntrack           67608  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
isofs                  31620  1 
vfat                   10716  1 
fat                    51452  1 vfat
udf                    80900  0 
crc_itu_t               1852  1 udf
cbc                     3516  125 
aes_i586                8124  126 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
rt2870sta             488820  0 
arc4                    1660  2 
iptable_filter          3100  1 
snd_rawmidi            22208  1 snd_seq_midi
ecb                     2524  3 
ip_tables              11692  2 iptable_nat,iptable_filter
dm_crypt               12928  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
rt2800usb              37372  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00usb              11548  1 rt2800usb
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
ppdev                   6688  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
input_polldev           3716  1 rt2x00lib
joydev                 10272  0 
parport_pc             31940  1 
dell_wmi                2564  0 
shpchp                 32272  0 
dcdbas                  7292  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb
psmouse                56180  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52544  1 
e1000                 119264  0 
tulip                  48320  0 
intel_agp              27484  1 
agpgart                34988  1 intel_agp
floppy                 54916  0 

jukebox-zero@jukebox-zero-desktop:~$ dmesg | tail
[20037.107626] wlan1: associate with AP 00:11:50:5f:74:9f
[20037.109775] wlan1: RX AssocResp from 00:11:50:5f:74:9f (capab=0x401 status=0 aid=3)
[20037.109784] wlan1: associated
[20037.118346] wlan1: disassociating by local choice (reason=3)
[20091.989913] wlan1: Trigger new scan to find an IBSS to join
[20095.000283] wlan1: Trigger new scan to find an IBSS to join
[20098.000034] wlan1: Trigger new scan to find an IBSS to join
[20101.000380] wlan1: Trigger new scan to find an IBSS to join
[20101.812853] wlan1: Creating new IBSS network, BSSID de:c5:ed:73:5a:ba
[20102.104020] wlan1: no IPv6 routers present
jukebox-zero@jukebox-zero-desktop:~$Notice that last line printed by dmesg | tail  ?

It's interesting to note this is a Belkin USB Wireless n device, which seems to work fine with no restricted drivers installed although when I installed the rt2080 driver that came with using ndisgtk I am served a dialog that it cannot confirm the device is detected, or something along those lines, though in windows wireless drivers dialog it literally says "Hardware detected: Yes." None the less, as it can see several other wireless networks, and can even connect to some (fastest pirated speed got ndisgtk apt-get installed at 30kbp/s) and only fails to see my own, I suspect IPv6 is at fault. Or at the least, disabling it is the next logical step. I've located one solution though I would rather not alter my grub any further if I can avoid this.

> Edit /etc/default/grub file[INDENT]gksudo gedit  /etc/default/grub
[/INDENT]Change[INDENT]GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
[/INDENT]to[INDENT]GRUB_CMDLINE_LINUX_DEFAULT=&#8221;ipv6.disable=1 quiet splash&#8221;
[/INDENT]Save and exit the file
 If there's an alternative to this I'd be interested, I'd like to leave the grub as intact as possible until I get this install fully up and running so I know which problems I caused and what broke what. I already changed the grub once for the aformentioned booting from ext4 partition glich.

Can anyone help me tackle this issue so I can move on to my next problem? ;)

- A. Venez

---

### Post by Brandon Williams on 2010-01-09
I would be surprised if IPv6 is really thr problem here. It seems that IPv6 wouldn't come into play until you were already associated with the access point, and it sound like you aren't even getting that far. Still, it's always possible that there's some relationship that isn't obvious, so ...

You can disable IPv6 with sysctl:
```
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
```

If that solves the problem, then you can make it persistent by adding the following line to /etc/sysctl.conf:
```
net.ipv6.conf.all.disable_ipv6 = 1
```

---

