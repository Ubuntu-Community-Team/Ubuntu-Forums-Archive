---
title: "Unable to get Tenda W54P/P+ drivers"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by raziel09 on 2011-04-22
This is really my first post on these forums however i have been using Ubuntu for about a year (primarily as an internet system).

I have created my own wireless network which connects my windows laptop and my lexmark printer and bought (a while ago now) an PCI wireless adapter to fit into my Linux box.


The machine itself is quite old now but still going strong; however since i fitted the wireless card the machine won't reboot. 

It'll start up and shut down fine but if i do updates which require an reboot to complete the machine shuts down fine. However it will only get so far as the Compaq splash screen and won't advance from there.

I have reseated all of the components, disabled the onboard lan, prioritized the hdd all TNA. 

The wireless itself works fine however i believe the issue might lay in the drivers (might be using really basic ones. I have an installation disc however it was created for windows and obviously won't run (not in wine either).

I have scoured the internet and these forums but can't see anything similar to the issue i have

This might not be an wireless card issue however any advice is welcome

---

### Post by chili555 on 2011-04-22
There are some wireless cards that have conflicts; that is, two or more drivers claim the card. Let's start by ruling that out. In a terminal, run and post:```
lspci -nn
lsmod
```Thanks.

---

### Post by raziel09 on 2011-04-22
Thanks for the speedy answer

from lspci -nn (assuming that the first letter should be an lowercase L) i get 

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GT] [10de:0391] (rev a1)
02:00.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
02:04.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80

---

### Post by raziel09 on 2011-04-22
and from lsmod i get the following output

Module                     Size            Used by
nls_utf8                    1069           1 
isofs                             30022       1 
ppp_deflate               3726           0 
zlib_deflate             19266     1 ppp_deflate
bsd_comp                     4791        0 
ppp_async                    6778       1 
crc_ccitt                         1351            1 ppp_async
rfcomm                        33811          4 
binfmt_misc                   6599             1 
sco                                      7998            2 
bnep               9542                  2 
l2cap                             37008           16 rfcomm,bnep
vboxnetadp                       6454           0 
vboxnetflt                      15152            0 
vboxdrv           190199          2 vboxnetadp,vboxnetflt
option                              13613           2 
usb_wwan                       9953             1 option
nvidia                          9329739             38 
ipt_REJECT                      2004               1 
ipt_LOG                              4490               5 
snd_atiixp                      12426               2 
snd_ac97_codec          99227           1 snd_atiixp
ac97_bus                             1014             1  snd_ac97_codec
usbserial                          33839        7 option,usb_wwan
snd_pcm                           71475               2 snd_atiixp,snd_ac97_codec
xt_limit                         1394                      7 
xt_tcpudp                          1927             7 
snd_seq_midi                  4588                    0 
ipt_addrtype                      1611           4 
arc4                    1165  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
xt_state                1014  7 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
nf_nat_irc              1168  0 
rt61pci                19187  0 
rt2x00pci               6029  1 rt61pci
rt2x00lib              27307  2 rt61pci,rt2x00pci
nf_conntrack_irc        3348  1 nf_nat_irc
led_class               2633  1 rt2x00lib
nf_nat_ftp              1398  0 
mac80211              231927  2 rt2x00pci,rt2x00lib
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd                    49102  11 snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              144790  2 rt2x00lib,mac80211
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_atiixp,snd_pcm
nf_conntrack_ftp        5361  1 nf_nat_ftp
btusb                  10969  2 
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
iptable_filter          1302  1 
eeprom_93cx6            1345  1 rt61pci
usbhid                 36882  0 
i2c_piix4               8635  0 
ip_tables              10460  1 iptable_filter
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
hid                    67742  1 usbhid
ati_agp                 5202  0 
ppdev                   5556  0 
k8temp                  3228  0 
agpgart                32011  2 nvidia,ati_agp
parport_pc             26058  1 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21234  0 
usb_storage            40492  1 
firewire_core          46643  1 firewire_ohci
sata_sil                7035  0 
pata_atiixp             3288  2 
crc_itu_t               1383  2 rt61pci,firewire_core

---

### Post by chili555 on 2011-04-22
Looks fine so far. May I assume you've tried removing the wireless card altogether and that it boots and shuts down correctly? What does this tell us?```
sudo cat /var/log/syslog | grep rt61
```

---

### Post by raziel09 on 2011-04-29
Apologies for the delay; been busy preparing my machine for the new version of Ubuntu. I wiped the machine clean and installed 11.04 beta 2 over my 10.10 installation.

However the issue is still there. It looks like the issue is not related to drivers for the wireless card (which i have removed and tried booting with no success)

After doing more research on google it appears that the issue i'm facing was known when this machine was first released (HP Compaq SR1539UK). They released an update to the BIOS which states that it fixed some reboot issues however the machine already has the latest version (released about 2006).

Looks like it might be time to get an new linux box made and finally retire this one. Problem being that most new machines are way overpowered for what i need (i only use this for email and web surfing).


Thanks for the help with this - looks like an issue that can't simply be resolved.

---

### Post by chili555 on 2011-04-29
> Problem being that most new machines are way overpowered for what i need (i only use this for email and web surfing). That is Mrs. Chili's situation, exactly. She is very happy with this: [http://www.system76.com/product_info.php?cPath=27&products_id=91](http://www.system76.com/product_info.php?cPath=27&products_id=91)

Ubuntu is pre-installed and works perfectly. It's very nearly silent and sits right behind her monitor.

---

### Post by raziel09 on 2011-04-29
Thanks for the link chili555; i have been thinking about getting an new atom based machine. However am slightly put off as i have read online that the CPU is hard wired to the board making upgrades impossible (i like having the option to upgrade).


Really i'm looking to buy from an company based in the UK (cheaper P+P).

One question is how responsive is an atom based system? can it handle multi-tasking well in linux?

Kinda going off the original subject now so might open a new thread (after doing a search on the forums as i'm sure this question has been asked a few times)

One question - how do you mark these threads as resolved?

---

### Post by chili555 on 2011-04-29
Mrs. Chili finds the system pretty responsive for her needs: email and browsing. She does play a flash game, as well. She never complains.

Use the thread tools at the top and 'Mark Solved.'

---

