---
title: "Nat Loopback"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by Atsuisofu on 2011-08-24
So I have an Ubuntu server setup but my modem from my ISP only has one ethernet port so I have to run my server behind a router. I have been able to get the sever viewable to everyone outside of my network but when someone is inside my network they have to view the server by the direct IP the web address doesnt work nor does the actual static IP. I believe this is something to do with my router not being able to loopback. It is a belkin N600 DB. Any info would be greatly appreciated.

Thanks again

---

### Post by praseodym on 2011-08-24
Do you have a GUI on your server? Do you use the network-manager? Please show:

```
cat /etc/network/interfaces
route -n
lspci -nnk | grep -iA2 net
lsmod
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by Atsuisofu on 2011-08-24
I do have a GUI I went for a LAMP install on 11.04.

---

### Post by Atsuisofu on 2011-08-24
cat /etc/network/interfaces
auto lo
iface lo inet loopback

~~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
ethan@ethan-System-Product-Name:~$ lspci -nnk | grep -iA2 net
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
	Subsystem: ASUSTeK Computer Inc. A7V8X-X Motherboard [1043:80a1]
	Kernel driver in use: via-rhine
ethan@ethan-System-Product-Name:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
snd_via82xx            24685  2 
snd_ac97_codec        105614  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_via82xx,snd_ac97_codec
radeon                925094  3 
snd_page_alloc         14073  2 snd_via82xx,snd_pcm
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_viapro             12969  0 
via_ircc               26953  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
snd                    55295  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  185091  1 via_ircc
soundcore              12600  1 snd
ns558                  12618  0 
parport_pc             32111  1 
gameport               15027  3 snd_via82xx,ns558
crc_ccitt              12595  1 irda
i2c_algo_bit           13184  1 radeon
shpchp                 32345  0 
it87                   29275  0 
hwmon_vid              12658  1 it87
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
pata_via               13368  3 
via_rhine              27131  0 
floppy                 60032  0

---

### Post by lmarmisa on 2011-08-24
> **Atsuisofu said:**
> So I have an Ubuntu server setup but my modem from my ISP only has one ethernet port so I have to run my server behind a router. I have been able to get the sever viewable to everyone outside of my network but when someone is inside my network they have to view the server by the direct IP the web address doesnt work nor does the actual static IP. I believe this is something to do with my router not being able to loopback. It is a belkin N600 DB. Any info would be greatly appreciated.

Thanks again

I think that your router does not support that feature.

I have checked that your router is not compatible with the firmware [**DD-WRT**]("http://www.dd-wrt.com/"). This firmware is Linux based and has no problem about NAT loopback. Some inexpensive routers like the Buffalo WHR-300N or the classic Linksys WRT54GL runs fine with DD-WRT.

If you do not plan to substitute your router, try to use a http proxy server located in Internet.

---

### Post by never say never on 2011-08-24
there are a couple of easy ways around this. The way I normally do it is:

1. Set up a DNS server, make it authoritative  for your domain. i.e. mysite.me.  Do NOT change the DNS servers listed in your Domain Registration.

2. Have all systems in your network use your DNS server.

So if your LAMP box is at 192.168.0.200, add a DNS server to that box making it authoritive for your site.  Then set up the DHCP on your router to use 192.168.0.200 for DNS.  Now all systems in your network will see mysite.me as being 192.168.0.200 and the rest of the world will see it as your ISP provided IP.  Problem solved.

This makes it virtually seamless for access and just plain works.  Not quite as clean as a Nat reflection but, it works.

---

### Post by Atsuisofu on 2011-08-24
Thanks very much for your timely replies. I will have to get a new router I work for the GeekSquad so that shouldnt be to difficult. Pick one up after work. I have never flashed new firmware to a router is it difficult? I have flash new firmware to phones and I am familiar with flashing Binaries to a NANDS is it similar?

---

### Post by lmarmisa on 2011-08-24
I have two [Linksys WRT54GL]("http://en.wikipedia.org/wiki/Linksys_WRT54G_series") for many years. I am very happy with them. They are great. The main disadvantage is that they do not include the new standards like Ethernet Gigabit 1000 Mbps or wireless 802.11n 300 Mbps. I had no problems when flashing alternative linux based firmwares like [DD-WRT]("http://www.dd-wrt.com") or [Tomato]("http://www.polarcloud.com/tomato"). That was very easy. Anyway, pay attention to the instructions. If you make a mistake, you could brick your device.

I am thinking to buy a Buffalo router of new generation now. I have read that they use DD-WRT as factory default firmware:

[http://www.dd-wrt.com/site/content/buffalo-highpower-routers-with-dd-wrt-factory-firmware](http://www.dd-wrt.com/site/content/buffalo-highpower-routers-with-dd-wrt-factory-firmware)

---

