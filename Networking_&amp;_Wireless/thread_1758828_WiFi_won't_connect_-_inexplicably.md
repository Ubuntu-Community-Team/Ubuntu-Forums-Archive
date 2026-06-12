---
title: "WiFi won't connect - inexplicably"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by karlm on 2011-05-15
I posted about this yesterday, apparently in the wrong place. So I'll just copy/paste what I wrote there to here:


> **karlm said:**
> Using 10.04LTS here, every now and then my connection seems to die for no apparent reason.

I use an ISP that allows me to log into other routers when I'm out and about in an open-exchange, so my router also puts out a public connection...

All my other machines connect including my android phone and my two daughter's smart-phones too.

Now the weird thing is, when I try to connect using a saved and working connection - it for no reason moves away from it and moves on to my free connection (the public one I broadcast, i.e. the same router and same wifi card - so it's NOT a hardware issue either on my laptop NOR on my router).

So I can connect to the very same router using the very same wifi card using windows & linux - but when I try to use my always previously working connection it doesn't want to know.

I've deleted it and got it to refind it - which it did without issue, and put my correct p/w back in and it continues to ignore it.

It's a lil on the infuriating side... 



ps - i'm currently connected via my ubuntu OS and on my public open-access connection, thus confirming there is no hardware issue.
I'm now using windows xp on my laptop (same one as has ubuntu on it) and it connects without issue.

Last night, I booted into linux and I've tried a program I saw mentioned named 'wicd' but the same issue persists whether it's wicd or the standard network manager app.

---

### Post by karlm on 2011-05-16
> **karlm said:**
> I posted about this yesterday, apparently in the wrong place. So I'll just copy/paste what I wrote there to here:


bump

---

### Post by josephmills on 2011-05-16
Hi there could you please open your terminal (ctrl+alt+t )and then type in ```
lspci -nn
``` then ```
rfkill list all
``` then paste here for all too see thanks

---

### Post by karlm on 2011-05-16
xxxx@xxxx-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 7930 Host Bridge [1002:7930]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS7932 PCI Bridge [1002:7932]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:7935]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS7936 PCI Bridge [1002:7936]
00:07.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:7937]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Xpress 1250 [1002:7942]
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 15)

xxxx@xxxx-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
xxxx@xxxx-laptop:~$ 


-------
ps - currently connected via my own open access (ie same router, same wifi card, etc.)

---

### Post by josephmills on 2011-05-16
try ```
rfkill unblock all 
``` anything ?

---

### Post by josephmills on 2011-05-16
could we also see a ```
lsmod | grep ath 
``` and a ```
dmesg | grep ath
``` thanks

---

### Post by karlm on 2011-05-16
xxxx@xxxx-laptop:~$ rfkill unblock all
xxxx@xxxx-laptop:~$ lsmod | grep ath
ath5k                 121632  0 
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
xxxx@xxxx-laptop:~$ dmesg | grep ath
[    0.678757] device-mapper: multipath: version 1.1.0 loaded
[    0.678761] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.777779] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.777794] ath5k 0000:02:00.0: setting latency timer to 64
[   15.777848] ath5k 0000:02:00.0: registered as 'phy0'
[   16.407939] ath: EEPROM regdomain: 0x65
[   16.407943] ath: EEPROM indicates we should expect a direct regpair map
[   16.407948] ath: Country alpha2 being used: 00
[   16.407950] ath: Regpair used: 0x65
[   16.445278] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 3347.687261] ath5k phy0: noise floor calibration timeout (2417MHz)

---

### Post by josephmills on 2011-05-16
> **karlm said:**
> xxxx@xxxx-laptop:~$ rfkill unblock all
xxxx@xxxx-laptop:~$ lsmod | grep ath
ath5k                 121632  0 
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
xxxx@xxxx-laptop:~$ dmesg | grep ath
[    0.678757] device-mapper: multipath: version 1.1.0 loaded
[    0.678761] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.777779] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.777794] ath5k 0000:02:00.0: setting latency timer to 64
[   15.777848] ath5k 0000:02:00.0: registered as 'phy0'
[   16.407939] ath: EEPROM regdomain: 0x65
[   16.407943] ath: EEPROM indicates we should expect a direct regpair map
[   16.407948] ath: Country alpha2 being used: 00
[   16.407950] ath: Regpair used: 0x65
[   16.445278] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 3347.687261] ath5k phy0: noise floor calibration timeout (2417MHz)

ok lsmod looks good dmesg is different from mine ```
 dmesg | grep ath 
[    0.680490] device-mapper: multipath: version 1.1.1 loaded
[    0.680493] device-mapper: multipath round-robin: version 1.0.0 loaded
[   16.588508] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   16.588527] ath5k 0000:07:00.0: setting latency timer to 64
[   16.588591] ath5k 0000:07:00.0: registered as 'phy0'
[   17.170436] ath: EEPROM regdomain: 0x64
[   17.170438] ath: EEPROM indicates we should expect a direct regpair map
[   17.170444] ath: Country alpha2 being used: 00
[   17.170446] ath: Regpair used: 0x64
[   17.561844] Registered led device: ath5k-phy0::rx
[   17.561864] Registered led device: ath5k-phy0::tx
[   17.561869] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[18947.662081] ath5k 0000:07:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)

```
could we see all the mods ```
lsmod
``` are you sure you dont see networks? is enable wireless "greyed out" ?

---

### Post by josephmills on 2011-05-16
could we also see a ```
dmesg | grep wlan 
``` and ```
modinfo ath5k
``` thanks

---

### Post by karlm on 2011-05-16
> **josephmills said:**
> ok lsmod looks good dmesg is different from mine 

could we see all the mods ```
lsmod
``` are you sure you dont see networks? is enable wireless "greyed out" ?
I *do* see networks - and it claims to be trying to connect, but rejects it and moves onto (automatically) to my public/open wifi signal instead, which connects flawlessly (e.g. I'm using it now, but wish to have my full signal back as the open access is only 10% roughly of the full N rated router).

Networking is not greyed out - I live in a tower block and see my two connections (private & public) as well as about 5 others from surrounding homes.

If I boot this laptop into Windows XP, it connects to my private access without any issue and doesn't cut out or reject access.



lsmod - 
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39841  1 
aes_i586                7268  0 
aes_generic            26863  1 aes_i586
hidp                   11083  0 
binfmt_misc             6587  1 
rfcomm                 33421  8 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  17 hidp,rfcomm,bnep
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168753  2 vboxnetadp,vboxnetflt
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1631  4 
joydev                  8740  0 
arc4                    1153  2 
xt_state                1098  7 
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
snd_hda_codec_realtek   203408  1 
nf_nat_ftp              1836  0 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2271  1 
radeon                677027  3 
ttm                    49943  1 radeon
drm_kms_helper         29329  1 radeon
ip_tables               9991  1 iptable_filter
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121632  0 
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
drm                   162345  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
btusb                  10957  2 
bluetooth              49892  10 hidp,rfcomm,sco,bnep,l2cap,btusb
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  17375  0 
output                  1871  1 video
ati_agp                 5094  0 
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
i2c_piix4               8335  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
shpchp                 28835  0 
agpgart                31724  3 ttm,drm,ati_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  2 hidp,usbhid
sky2                   40807  0 
pata_atiixp             3148  0 
ahci                   32200  3 

```

> **josephmills said:**
> could we also see a ```
dmesg | grep wlan 
``` and ```
modinfo ath5k
``` thanks

dmesg | grep wlan - (this is LOOOOONG)
```
aid=1)
[  396.261720] wlan0: associated
[  396.389078] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  396.506529] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  397.911751] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  397.914572] wlan0: direct probe responded
[  397.914578] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  397.916484] wlan0: authenticated
[  397.916509] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  397.919649] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  397.919654] wlan0: associated
[  397.920611] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  408.800037] wlan0: no IPv6 routers present
[  442.809095] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  442.863120] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  442.865962] wlan0: direct probe responded
[  442.865971] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  442.867912] wlan0: authenticated
[  442.877614] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  442.877693] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  442.907953] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  443.104086] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 2)
[  443.106648] wlan0: direct probe responded
[  443.106659] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  443.108598] wlan0: authenticated
[  443.108653] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  443.111161] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[  443.111169] wlan0: associated
[  542.772092] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  542.830575] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  542.848619] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  542.874843] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  543.072059] wlan0: direct probe to AP my.ad.dr.es.s (try 2)
[  543.272055] wlan0: direct probe to AP my.ad.dr.es.s (try 3)
[  543.472049] wlan0: direct probe to AP my.ad.dr.es.s timed out
[  544.465959] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  544.697174] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  544.896061] wlan0: direct probe to AP my.ad.dr.es.s (try 2)
[  544.898896] wlan0: direct probe responded
[  544.898903] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  544.900783] wlan0: authenticated
[  544.900841] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  544.903022] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  544.903031] wlan0: associated
[  544.904476] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  555.005048] wlan0: no IPv6 routers present
[  622.844089] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  622.913302] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  622.913381] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  622.959501] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  622.963759] wlan0: direct probe responded
[  622.963767] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  622.965648] wlan0: authenticated
[  622.965680] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  622.968297] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[  622.968302] wlan0: associated
[  722.761119] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  722.823926] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  722.823960] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  722.848974] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  722.851807] wlan0: direct probe responded
[  722.851814] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  722.853758] wlan0: authenticated
[  722.853791] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  722.856808] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  722.856813] wlan0: associated
[  842.773099] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  842.834805] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  842.834843] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  842.862983] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  842.866884] wlan0: direct probe responded
[  842.866892] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  842.868763] wlan0: authenticated
[  842.868792] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  842.872959] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[  842.872964] wlan0: associated
[  962.768061] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  962.820987] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  962.821032] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  962.847698] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  962.850533] wlan0: direct probe responded
[  962.850540] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  962.852431] wlan0: authenticated
[  962.860724] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  962.863159] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  962.863167] wlan0: associated
[ 1082.789050] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1082.847163] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[ 1082.865357] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1082.893316] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1082.896155] wlan0: direct probe responded
[ 1082.896163] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1082.898233] wlan0: authenticated
[ 1082.898266] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1082.900861] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[ 1082.900867] wlan0: associated
[ 1322.740065] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 1322.804823] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1322.804885] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 1322.830351] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[ 1322.836323] wlan0: direct probe responded
[ 1322.836335] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[ 1322.837992] wlan0: authenticated
[ 1322.838037] wlan0: associate with AP my.ad.dr.es.s (try 1)
[ 1322.849561] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[ 1322.849566] wlan0: associated
[ 1562.744075] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1562.797284] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[ 1562.797320] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1562.826031] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1562.828562] wlan0: direct probe responded
[ 1562.828569] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1562.830575] wlan0: authenticated
[ 1562.840539] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1562.842880] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[ 1562.842890] wlan0: associated
[ 1954.713070] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 1954.945151] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 1955.179628] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 1955.182119] wlan0: direct probe responded
[ 1955.182128] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 1955.184204] wlan0: authenticated
[ 1955.184240] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 1955.186759] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 1955.186766] wlan0: associated
[ 2079.252107] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 2079.371564] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2079.591364] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2082.036595] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 2082.036655] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 2082.298739] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 2082.301336] wlan0: direct probe responded
[ 2082.301344] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 2082.303611] wlan0: authenticated
[ 2082.303647] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 2082.306286] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 2082.306295] wlan0: associated
[ 2082.307725] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2092.481463] wlan0: no IPv6 routers present
[ 2113.576088] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 2113.698896] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2114.023367] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2116.300566] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 2116.562786] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 2116.565268] wlan0: direct probe responded
[ 2116.565273] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 2116.567941] wlan0: authenticated
[ 2116.567963] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 2116.570573] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 2116.570577] wlan0: associated
[ 2116.571368] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2127.092034] wlan0: no IPv6 routers present
[ 7407.541123] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=12247 DF PROTO=TCP SPT=80 DPT=54309 WINDOW=333 RES=0x00 ACK RST URGP=0 
[ 7407.790228] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5509 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 7414.582770] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=12248 DF PROTO=TCP SPT=80 DPT=54309 WINDOW=333 RES=0x00 ACK RST URGP=0 
[ 7415.086125] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5510 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 7429.676483] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5511 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 7458.860312] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5512 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 8802.877092] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 8802.944115] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 8802.944140] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 8802.971081] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 8803.169059] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 2)
[ 8803.171830] wlan0: direct probe responded
[ 8803.171838] wlan0: authenticate with AP 02:24:17:cd:a4:ab (try 1)
[ 8803.173757] wlan0: authenticated
[ 8803.173809] wlan0: associate with AP 02:24:17:cd:a4:ab (try 1)
[ 8803.184613] wlan0: RX AssocResp from 02:24:17:cd:a4:ab (capab=0x401 status=0 aid=2)
[ 8803.184622] wlan0: associated
[ 8922.765058] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 8922.815840] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 8922.818605] wlan0: direct probe responded
[ 8922.818612] wlan0: authenticate with AP 02:24:17:cd:a4:ab (try 1)
[ 8922.820548] wlan0: authenticated
[ 8922.821453] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 8922.849077] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 8922.851568] wlan0: direct probe responded
[ 8922.851577] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 8922.853557] wlan0: authenticated
[ 8922.853593] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 8922.856305] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 8922.856310] wlan0: associated
[ 9180.881068] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 9185.158164] wlan0: deauthenticating from an.ot.he.ra.dd.re.ss by local choice (reason=3)
[ 9185.390468] wlan0: direct probe to AP an.ot.he.ra.dd.re.ss (try 1)
[ 9185.394858] wlan0: direct probe responded
[ 9185.394866] wlan0: authenticate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9185.396905] wlan0: authenticated
[ 9185.396950] wlan0: associate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9185.399852] wlan0: RX AssocResp from an.ot.he.ra.dd.re.ss (capab=0x431 status=0 aid=1)
[ 9185.399858] wlan0: associated
[ 9187.245154] wlan0: deauthenticating from an.ot.he.ra.dd.re.ss by local choice (reason=3)
[ 9187.371029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9188.753238] wlan0: direct probe to AP an.ot.he.ra.dd.re.ss (try 1)
[ 9188.756349] wlan0: direct probe responded
[ 9188.756358] wlan0: authenticate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9188.758639] wlan0: authenticated
[ 9188.758680] wlan0: associate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9188.761613] wlan0: RX AssocResp from an.ot.he.ra.dd.re.ss (capab=0x431 status=0 aid=1)
[ 9188.761619] wlan0: associated
[ 9188.762435] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9199.660035] wlan0: no IPv6 routers present
[ 9231.409131] wlan0: deauthenticating from an.ot.he.ra.dd.re.ss by local choice (reason=3)
[ 9344.898485] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 9345.131694] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 9345.134573] wlan0: direct probe responded
[ 9345.134582] wlan0: authenticate with AP 02:24:17:cd:a4:ab (try 1)
[ 9345.136519] wlan0: authenticated
[ 9345.136591] wlan0: associate with AP 02:24:17:cd:a4:ab (try 1)
[ 9345.140344] wlan0: RX AssocResp from 02:24:17:cd:a4:ab (capab=0x401 status=0 aid=2)
[ 9345.140351] wlan0: associated
[ 9442.760098] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 9442.822841] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 9442.822945] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 9442.850577] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 9442.853124] wlan0: direct probe responded
[ 9442.853131] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 9442.855008] wlan0: authenticated
[ 9442.855041] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 9442.857667] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 9442.857673] wlan0: associated
[ 9544.137080] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 9546.776321] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9551.667058] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 9551.898317] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 9551.902246] wlan0: direct probe responded
[ 9551.902253] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 9551.904230] wlan0: authenticated
[ 9551.904277] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 9551.907211] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[ 9551.907217] wlan0: associated
[ 9551.908090] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9562.397027] wlan0: no IPv6 routers present
[11495.909816] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=51 ID=41170 DF PROTO=TCP SPT=80 DPT=60917 WINDOW=248 RES=0x00 ACK URGP=0 
[11495.929999] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=51 ID=15099 DF PROTO=TCP SPT=80 DPT=60918 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.164355] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=33672 DF PROTO=TCP SPT=80 DPT=46915 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.174062] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.49 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=26437 DF PROTO=TCP SPT=80 DPT=42288 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.181825] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=5030 DF PROTO=TCP SPT=80 DPT=60761 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.188920] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.67 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=21947 DF PROTO=TCP SPT=80 DPT=37146 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.195536] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=23536 DF PROTO=TCP SPT=80 DPT=46487 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.201415] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=45108 DF PROTO=TCP SPT=80 DPT=60763 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.205547] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=9514 DF PROTO=TCP SPT=80 DPT=46488 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.244130] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=39163 DF PROTO=TCP SPT=80 DPT=46914 WINDOW=215 RES=0x00 ACK URGP=0 
[11516.747459] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=45112 DF PROTO=TCP SPT=80 DPT=60763 WINDOW=215 RES=0x00 ACK URGP=0 
[12195.910266] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=993 PROTO=TCP SPT=80 DPT=45498 WINDOW=234 RES=0x00 ACK FIN URGP=0 
[12196.265281] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32726 PROTO=TCP SPT=80 DPT=60266 WINDOW=163 RES=0x00 ACK FIN URGP=0 
[12196.382056] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=45614 PROTO=TCP SPT=80 DPT=55254 WINDOW=460 RES=0x00 ACK FIN URGP=0 
[12196.392381] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32727 PROTO=TCP SPT=80 DPT=60265 WINDOW=238 RES=0x00 ACK FIN URGP=0 
[12196.487749] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32728 PROTO=TCP SPT=80 DPT=60266 WINDOW=163 RES=0x00 ACK FIN URGP=0 
[12196.625076] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32729 PROTO=TCP SPT=80 DPT=60265 WINDOW=238 RES=0x00 ACK FIN URGP=0 
[12196.798696] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=994 PROTO=TCP SPT=80 DPT=45498 WINDOW=234 RES=0x00 ACK FIN URGP=0 
[12196.886056] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=53303 PROTO=TCP SPT=80 DPT=53571 WINDOW=106 RES=0x00 ACK FIN URGP=0 
[12196.931323] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32730 PROTO=TCP SPT=80 DPT=60266 WINDOW=163 RES=0x00 ACK FIN URGP=0 
[12197.090915] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32731 PROTO=TCP SPT=80 DPT=60265 WINDOW=238 RES=0x00 ACK FIN URGP=0 
[12219.230444] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=48082 PROTO=TCP SPT=80 DPT=45498 WINDOW=234 RES=0x00 ACK FIN URGP=0 
[12282.985546] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=182 TOS=0x00 PREC=0x00 TTL=48 ID=57753 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH URGP=0 
[12284.386307] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=4714 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[12285.498474] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=14597 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[12287.525202] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=33152 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[12305.994685] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=5917 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[13266.561873] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5407 DF PROTO=TCP SPT=80 DPT=51364 WINDOW=314 RES=0x00 ACK RST URGP=0 
[13266.979665] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35186 DF PROTO=TCP SPT=80 DPT=51363 WINDOW=110 RES=0x00 ACK RST URGP=0 

``` 

the above code seems to be too long to be fully included.

---

### Post by josephmills on 2011-05-16
is this a wep or a wpa/2 network that you are trying to connect too?

---

### Post by karlm on 2011-05-16
[  396.261720] wlan0: associated
[  396.389078] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  396.506529] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  397.911751] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  397.914572] wlan0: direct probe responded
[  397.914578] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  397.916484] wlan0: authenticated
[  397.916509] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  397.919649] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  397.919654] wlan0: associated
[  397.920611] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  408.800037] wlan0: no IPv6 routers present
[  442.809095] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  442.863120] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  442.865962] wlan0: direct probe responded
[  442.865971] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  442.867912] wlan0: authenticated
[  442.877614] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  442.877693] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  442.907953] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  443.104086] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 2)
[  443.106648] wlan0: direct probe responded
[  443.106659] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  443.108598] wlan0: authenticated
[  443.108653] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  443.111161] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[  443.111169] wlan0: associated
[  542.772092] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  542.830575] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  542.848619] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  542.874843] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  543.072059] wlan0: direct probe to AP my.ad.dr.es.s (try 2)
[  543.272055] wlan0: direct probe to AP my.ad.dr.es.s (try 3)
[  543.472049] wlan0: direct probe to AP my.ad.dr.es.s timed out
[  544.465959] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  544.697174] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  544.896061] wlan0: direct probe to AP my.ad.dr.es.s (try 2)
[  544.898896] wlan0: direct probe responded
[  544.898903] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  544.900783] wlan0: authenticated
[  544.900841] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  544.903022] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  544.903031] wlan0: associated
[  544.904476] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  555.005048] wlan0: no IPv6 routers present
[  622.844089] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  622.913302] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  622.913381] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  622.959501] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  622.963759] wlan0: direct probe responded
[  622.963767] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  622.965648] wlan0: authenticated
[  622.965680] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  622.968297] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[  622.968302] wlan0: associated
[  722.761119] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  722.823926] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  722.823960] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  722.848974] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  722.851807] wlan0: direct probe responded
[  722.851814] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  722.853758] wlan0: authenticated
[  722.853791] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  722.856808] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  722.856813] wlan0: associated
[  842.773099] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  842.834805] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  842.834843] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[  842.862983] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  842.866884] wlan0: direct probe responded
[  842.866892] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  842.868763] wlan0: authenticated
[  842.868792] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[  842.872959] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[  842.872964] wlan0: associated
[  962.768061] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  962.820987] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[  962.821032] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[  962.847698] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[  962.850533] wlan0: direct probe responded
[  962.850540] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[  962.852431] wlan0: authenticated
[  962.860724] wlan0: associate with AP my.ad.dr.es.s (try 1)
[  962.863159] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[  962.863167] wlan0: associated
[ 1082.789050] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1082.847163] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[ 1082.865357] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1082.893316] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1082.896155] wlan0: direct probe responded
[ 1082.896163] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1082.898233] wlan0: authenticated
[ 1082.898266] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1082.900861] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[ 1082.900867] wlan0: associated
[ 1322.740065] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 1322.804823] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1322.804885] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 1322.830351] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[ 1322.836323] wlan0: direct probe responded
[ 1322.836335] wlan0: authenticate with AP my.ad.dr.es.s (try 1)
[ 1322.837992] wlan0: authenticated
[ 1322.838037] wlan0: associate with AP my.ad.dr.es.s (try 1)
[ 1322.849561] wlan0: RX AssocResp from my.ad.dr.es.s (capab=0x401 status=0 aid=1)
[ 1322.849566] wlan0: associated
[ 1562.744075] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1562.797284] wlan0: direct probe to AP my.ad.dr.es.s (try 1)
[ 1562.797320] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 1562.826031] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1562.828562] wlan0: direct probe responded
[ 1562.828569] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1562.830575] wlan0: authenticated
[ 1562.840539] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 1562.842880] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[ 1562.842890] wlan0: associated
[ 1954.713070] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 1954.945151] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 1955.179628] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 1955.182119] wlan0: direct probe responded
[ 1955.182128] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 1955.184204] wlan0: authenticated
[ 1955.184240] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 1955.186759] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 1955.186766] wlan0: associated
[ 2079.252107] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 2079.371564] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2079.591364] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2082.036595] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 2082.036655] wlan0: deauthenticating from my.ad.dr.es.s by local choice (reason=3)
[ 2082.298739] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 2082.301336] wlan0: direct probe responded
[ 2082.301344] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 2082.303611] wlan0: authenticated
[ 2082.303647] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 2082.306286] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 2082.306295] wlan0: associated
[ 2082.307725] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2092.481463] wlan0: no IPv6 routers present
[ 2113.576088] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 2113.698896] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2114.023367] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2116.300566] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 2116.562786] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 2116.565268] wlan0: direct probe responded
[ 2116.565273] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 2116.567941] wlan0: authenticated
[ 2116.567963] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 2116.570573] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 2116.570577] wlan0: associated
[ 2116.571368] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2127.092034] wlan0: no IPv6 routers present
[ 7407.541123] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=12247 DF PROTO=TCP SPT=80 DPT=54309 WINDOW=333 RES=0x00 ACK RST URGP=0 
[ 7407.790228] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5509 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 7414.582770] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=12248 DF PROTO=TCP SPT=80 DPT=54309 WINDOW=333 RES=0x00 ACK RST URGP=0 
[ 7415.086125] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5510 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 7429.676483] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5511 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 7458.860312] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5512 DF PROTO=TCP SPT=80 DPT=50058 WINDOW=203 RES=0x00 ACK RST URGP=0 
[ 8802.877092] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 8802.944115] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 8802.944140] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 8802.971081] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 8803.169059] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 2)
[ 8803.171830] wlan0: direct probe responded
[ 8803.171838] wlan0: authenticate with AP 02:24:17:cd:a4:ab (try 1)
[ 8803.173757] wlan0: authenticated
[ 8803.173809] wlan0: associate with AP 02:24:17:cd:a4:ab (try 1)
[ 8803.184613] wlan0: RX AssocResp from 02:24:17:cd:a4:ab (capab=0x401 status=0 aid=2)
[ 8803.184622] wlan0: associated
[ 8922.765058] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 8922.815840] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 8922.818605] wlan0: direct probe responded
[ 8922.818612] wlan0: authenticate with AP 02:24:17:cd:a4:ab (try 1)
[ 8922.820548] wlan0: authenticated
[ 8922.821453] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 8922.849077] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 8922.851568] wlan0: direct probe responded
[ 8922.851577] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 8922.853557] wlan0: authenticated
[ 8922.853593] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 8922.856305] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 8922.856310] wlan0: associated
[ 9180.881068] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 9185.158164] wlan0: deauthenticating from an.ot.he.ra.dd.re.ss by local choice (reason=3)
[ 9185.390468] wlan0: direct probe to AP an.ot.he.ra.dd.re.ss (try 1)
[ 9185.394858] wlan0: direct probe responded
[ 9185.394866] wlan0: authenticate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9185.396905] wlan0: authenticated
[ 9185.396950] wlan0: associate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9185.399852] wlan0: RX AssocResp from an.ot.he.ra.dd.re.ss (capab=0x431 status=0 aid=1)
[ 9185.399858] wlan0: associated
[ 9187.245154] wlan0: deauthenticating from an.ot.he.ra.dd.re.ss by local choice (reason=3)
[ 9187.371029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9188.753238] wlan0: direct probe to AP an.ot.he.ra.dd.re.ss (try 1)
[ 9188.756349] wlan0: direct probe responded
[ 9188.756358] wlan0: authenticate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9188.758639] wlan0: authenticated
[ 9188.758680] wlan0: associate with AP an.ot.he.ra.dd.re.ss (try 1)
[ 9188.761613] wlan0: RX AssocResp from an.ot.he.ra.dd.re.ss (capab=0x431 status=0 aid=1)
[ 9188.761619] wlan0: associated
[ 9188.762435] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9199.660035] wlan0: no IPv6 routers present
[ 9231.409131] wlan0: deauthenticating from an.ot.he.ra.dd.re.ss by local choice (reason=3)
[ 9344.898485] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 9345.131694] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 9345.134573] wlan0: direct probe responded
[ 9345.134582] wlan0: authenticate with AP 02:24:17:cd:a4:ab (try 1)
[ 9345.136519] wlan0: authenticated
[ 9345.136591] wlan0: associate with AP 02:24:17:cd:a4:ab (try 1)
[ 9345.140344] wlan0: RX AssocResp from 02:24:17:cd:a4:ab (capab=0x401 status=0 aid=2)
[ 9345.140351] wlan0: associated
[ 9442.760098] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 9442.822841] wlan0: direct probe to AP 02:24:17:cd:a4:ab (try 1)
[ 9442.822945] wlan0: deauthenticating from 02:24:17:cd:a4:ab by local choice (reason=3)
[ 9442.850577] wlan0: direct probe to AP sh.or.tm.ac (try 1)
[ 9442.853124] wlan0: direct probe responded
[ 9442.853131] wlan0: authenticate with AP sh.or.tm.ac (try 1)
[ 9442.855008] wlan0: authenticated
[ 9442.855041] wlan0: associate with AP sh.or.tm.ac (try 1)
[ 9442.857667] wlan0: RX AssocResp from sh.or.tm.ac (capab=0x421 status=0 aid=1)
[ 9442.857673] wlan0: associated
[ 9544.137080] wlan0: deauthenticating from sh.or.tm.ac by local choice (reason=3)
[ 9546.776321] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9551.667058] wlan0: deauthenticating from di.ff.er.en.ta.dd.re.ss by local choice (reason=3)
[ 9551.898317] wlan0: direct probe to AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 9551.902246] wlan0: direct probe responded
[ 9551.902253] wlan0: authenticate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 9551.904230] wlan0: authenticated
[ 9551.904277] wlan0: associate with AP di.ff.er.en.ta.dd.re.ss (try 1)
[ 9551.907211] wlan0: RX AssocResp from di.ff.er.en.ta.dd.re.ss (capab=0x421 status=0 aid=1)
[ 9551.907217] wlan0: associated
[ 9551.908090] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9562.397027] wlan0: no IPv6 routers present
[11495.909816] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=51 ID=41170 DF PROTO=TCP SPT=80 DPT=60917 WINDOW=248 RES=0x00 ACK URGP=0 
[11495.929999] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=51 ID=15099 DF PROTO=TCP SPT=80 DPT=60918 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.164355] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=33672 DF PROTO=TCP SPT=80 DPT=46915 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.174062] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.49 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=26437 DF PROTO=TCP SPT=80 DPT=42288 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.181825] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=5030 DF PROTO=TCP SPT=80 DPT=60761 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.188920] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.67 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=21947 DF PROTO=TCP SPT=80 DPT=37146 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.195536] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=23536 DF PROTO=TCP SPT=80 DPT=46487 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.201415] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=45108 DF PROTO=TCP SPT=80 DPT=60763 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.205547] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=9514 DF PROTO=TCP SPT=80 DPT=46488 WINDOW=215 RES=0x00 ACK URGP=0 
[11515.244130] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=39163 DF PROTO=TCP SPT=80 DPT=46914 WINDOW=215 RES=0x00 ACK URGP=0 
[11516.747459] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=45112 DF PROTO=TCP SPT=80 DPT=60763 WINDOW=215 RES=0x00 ACK URGP=0 
[12195.910266] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=993 PROTO=TCP SPT=80 DPT=45498 WINDOW=234 RES=0x00 ACK FIN URGP=0 
[12196.265281] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32726 PROTO=TCP SPT=80 DPT=60266 WINDOW=163 RES=0x00 ACK FIN URGP=0 
[12196.382056] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=45614 PROTO=TCP SPT=80 DPT=55254 WINDOW=460 RES=0x00 ACK FIN URGP=0 
[12196.392381] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32727 PROTO=TCP SPT=80 DPT=60265 WINDOW=238 RES=0x00 ACK FIN URGP=0 
[12196.487749] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32728 PROTO=TCP SPT=80 DPT=60266 WINDOW=163 RES=0x00 ACK FIN URGP=0 
[12196.625076] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32729 PROTO=TCP SPT=80 DPT=60265 WINDOW=238 RES=0x00 ACK FIN URGP=0 
[12196.798696] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=994 PROTO=TCP SPT=80 DPT=45498 WINDOW=234 RES=0x00 ACK FIN URGP=0 
[12196.886056] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=53303 PROTO=TCP SPT=80 DPT=53571 WINDOW=106 RES=0x00 ACK FIN URGP=0 
[12196.931323] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32730 PROTO=TCP SPT=80 DPT=60266 WINDOW=163 RES=0x00 ACK FIN URGP=0 
[12197.090915] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=32731 PROTO=TCP SPT=80 DPT=60265 WINDOW=238 RES=0x00 ACK FIN URGP=0 
[12219.230444] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=48082 PROTO=TCP SPT=80 DPT=45498 WINDOW=234 RES=0x00 ACK FIN URGP=0 
[12282.985546] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=182 TOS=0x00 PREC=0x00 TTL=48 ID=57753 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH URGP=0 
[12284.386307] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=4714 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[12285.498474] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=14597 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[12287.525202] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=33152 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[12305.994685] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=318 TOS=0x00 PREC=0x00 TTL=48 ID=5917 DF PROTO=TCP SPT=5050 DPT=58564 WINDOW=8316 RES=0x00 ACK PSH FIN URGP=0 
[13266.561873] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5407 DF PROTO=TCP SPT=80 DPT=51364 WINDOW=314 RES=0x00 ACK RST URGP=0 
[13266.979665] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35186 DF PROTO=TCP SPT=80 DPT=51363 WINDOW=110 RES=0x00 ACK RST URGP=0 
[13267.011908] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35371 DF PROTO=TCP SPT=80 DPT=40409 WINDOW=240 RES=0x00 ACK RST URGP=0 
[13267.017876] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5408 DF PROTO=TCP SPT=80 DPT=51364 WINDOW=314 RES=0x00 ACK RST URGP=0 
[13267.846706] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35187 DF PROTO=TCP SPT=80 DPT=51363 WINDOW=110 RES=0x00 ACK RST URGP=0 
[13267.925487] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35372 DF PROTO=TCP SPT=80 DPT=40409 WINDOW=240 RES=0x00 ACK RST URGP=0 
[13267.929729] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5409 DF PROTO=TCP SPT=80 DPT=51364 WINDOW=314 RES=0x00 ACK RST URGP=0 
[13269.574253] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35188 DF PROTO=TCP SPT=80 DPT=51363 WINDOW=110 RES=0x00 ACK RST URGP=0 
[13269.750370] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35373 DF PROTO=TCP SPT=80 DPT=40409 WINDOW=240 RES=0x00 ACK RST URGP=0 
[13269.753656] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=5410 DF PROTO=TCP SPT=80 DPT=51364 WINDOW=314 RES=0x00 ACK RST URGP=0 
[13295.284441] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35376 DF PROTO=TCP SPT=80 DPT=40409 WINDOW=240 RES=0x00 ACK RST URGP=0 
[13324.469586] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=35377 DF PROTO=TCP SPT=80 DPT=40409 WINDOW=240 RES=0x00 ACK RST URGP=0 
[13339.063032] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=150.1.1.47 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=60 ID=3573 DF PROTO=TCP SPT=443 DPT=38131 WINDOW=1002 RES=0x00 ACK RST URGP=0 
[13704.664096] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=299.123.123.12 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=45043 DF PROTO=TCP SPT=80 DPT=47312 WINDOW=145 RES=0x00 ACK URGP=0 
[13704.672167] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=91.123.123.12 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=43341 DF PROTO=TCP SPT=80 DPT=47315 WINDOW=158 RES=0x00 ACK URGP=0 
[13704.778617] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=91.123.123.12 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=12318 DF PROTO=TCP SPT=80 DPT=47322 WINDOW=101 RES=0x00 ACK URGP=0 
[14337.104084] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=91.123.123.12 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=10393 DF PROTO=TCP SPT=80 DPT=40311 WINDOW=131 RES=0x00 ACK URGP=0 
[14337.149184] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.12.12.12 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=14699 DF PROTO=TCP SPT=80 DPT=40313 WINDOW=101 RES=0x00 ACK URGP=0 
[14371.815130] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.123.155 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=51 ID=10981 DF PROTO=TCP SPT=443 DPT=60612 WINDOW=317 RES=0x00 ACK URGP=0 
[14372.215539] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=111.222.333.67 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=52 ID=35807 DF PROTO=TCP SPT=80 DPT=59154 WINDOW=2636 RES=0x00 ACK URGP=0 
[14381.747022] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.123.95 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=51 ID=40384 PROTO=TCP SPT=80 DPT=53986 WINDOW=106 RES=0x00 ACK URGP=0 
[14382.339325] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.56 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=7723 DF PROTO=TCP SPT=80 DPT=57301 WINDOW=248 RES=0x00 ACK URGP=0 
[14876.615848] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.654.88.153 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=53 ID=60055 PROTO=TCP SPT=80 DPT=39732 WINDOW=126 RES=0x00 ACK URGP=0 
[14880.590825] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.243 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=54756 DF PROTO=TCP SPT=80 DPT=51244 WINDOW=840 RES=0x00 ACK URGP=0 
[14881.120535] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.243 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=44624 DF PROTO=TCP SPT=80 DPT=51249 WINDOW=907 RES=0x00 ACK URGP=0 
[14888.795126] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.243 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=44736 DF PROTO=TCP SPT=80 DPT=51249 WINDOW=1434 RES=0x00 ACK URGP=0 
[14889.993491] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.243 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=54858 DF PROTO=TCP SPT=80 DPT=51244 WINDOW=1236 RES=0x00 ACK URGP=0 
[14963.501012] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.224 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=52356 DF PROTO=TCP SPT=80 DPT=51399 WINDOW=296 RES=0x00 ACK RST URGP=0 
[14966.957432] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.224 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=52357 DF PROTO=TCP SPT=80 DPT=51399 WINDOW=296 RES=0x00 ACK RST URGP=0 
[14973.868954] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=12.34.55.224 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=52358 DF PROTO=TCP SPT=80 DPT=51399 WINDOW=296 RES=0x00 ACK RST URGP=0 
[15066.552781] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=20676 DF PROTO=TCP SPT=80 DPT=58536 WINDOW=240 RES=0x00 ACK RST URGP=0 
[15066.980776] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=11061 DF PROTO=TCP SPT=80 DPT=57786 WINDOW=110 RES=0x00 ACK RST URGP=0 
[15066.994553] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=20677 DF PROTO=TCP SPT=80 DPT=58536 WINDOW=240 RES=0x00 ACK RST URGP=0 
[15067.845037] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=11062 DF PROTO=TCP SPT=80 DPT=57786 WINDOW=110 RES=0x00 ACK RST URGP=0 
[15067.874840] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=20678 DF PROTO=TCP SPT=80 DPT=58536 WINDOW=240 RES=0x00 ACK RST URGP=0 
[15069.573506] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=11063 DF PROTO=TCP SPT=80 DPT=57786 WINDOW=110 RES=0x00 ACK RST URGP=0 
[15069.632948] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=20679 DF PROTO=TCP SPT=80 DPT=58536 WINDOW=240 RES=0x00 ACK RST URGP=0 
[15073.028180] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=11064 DF PROTO=TCP SPT=80 DPT=57786 WINDOW=110 RES=0x00 ACK RST URGP=0 
[15073.152688] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=20680 DF PROTO=TCP SPT=80 DPT=58536 WINDOW=240 RES=0x00 ACK RST URGP=0 
[15079.941296] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.456.789.10 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=11065 DF PROTO=TCP SPT=80 DPT=57786 WINDOW=110 RES=0x00 ACK RST URGP=0 
[15094.272971] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=123.123.456.456 DST=10.987.654.321 LEN=52 TOS=0x00 PREC=0x00 TTL=60 ID=20682 DF PROTO=TCP SPT=80 DPT=58536 WINDOW=240 RES=0x00 ACK RST URGP=0 
[15464.314809] [UFW BLOCK] IN=wlan0 OUT= MAC=bl.oo.dy.lo.ng.ma.ca.dd.re.ss SRC=91.123.123.12 DST=10.987.654.321 LEN=64 TOS=0x00 PREC=0x00 TTL=50 ID=36035 DF PROTO=TCP SPT=80 DPT=44918 WINDOW=60 RES=0x00 ACK URGP=0

---

### Post by karlm on 2011-05-16
> **josephmills said:**
> is this a wep or a wpa/2 network that you are trying to connect too?

WPA2 connection.

It's always worked flawlessly for ... ooh, since I installed ubuntu - then it died for no apparent reasons (but my other devices still connect without issue - so as far as I can tell, it is not the router, and as I can connect to the same router using my public access and via windows, i'm guessing it's not the wifi card)


ps - i had changed it around last night, the router suggested changing from WPA2 to WEP - so I changed the settings accordingly in my connection, having been reminded of this fact (by the above quote/question) I have put it back to WPA2 (on the router and in settings for this connection)

---

### Post by josephmills on 2011-05-16
> **karlm said:**
> WPA2 connection.

It's always worked flawlessly for ... ooh, since I installed ubuntu - then it died for no apparent reasons (but my other devices still connect without issue - so as far as I can tell, it is not the router, and as I can connect to the same router using my public access and via windows, i'm guessing it's not the wifi card)

no it is not the card this might be above my pay grade and you might have  to wait for some one else to come along and see this but i THINK that it has something to do with the wpa suppliant open synaptic and type in wpa in the search bar is wpa supplicant installed if not install if so remove reboot reinstall reboot try again any thing ?

---

### Post by josephmills on 2011-05-16
edit disregard

---

### Post by karlm on 2011-05-16
> **josephmills said:**
> edit disregard

Aye, sorry I got your hopes up there... 

It's frustrating.



I think I'll just wipe & reinstall - just like windoze daze.

---

### Post by josephmills on 2011-05-16
sorry when I put edit and diregarde it was fo the mods of this forum I asked them to delete it but they must have not gotten around to it yet try post # 14 again if works cool if not reinstall if you like sorry that I was not that much help

---

### Post by karlm on 2011-05-16
> **josephmills said:**
> sorry when I put edit and diregarde it was fo the mods of this forum I asked them to delete it but they must have not gotten around to it yet try post # 14 again if works cool if not reinstall if you like sorry that I was not that much help
OK, let me see.... 

reading post 14...

> **josephmills said:**
> no it is not the card this might be above my pay grade and you might have  to wait for some one else to come along and see this but i THINK that it has something to do with the wpa suppliant open synaptic and type in wpa in the search bar is wpa supplicant installed if not install if so remove reboot reinstall reboot try again any thing ?

Right - I've got NO idea what you just said! Sorry.



However, here's a small update that may shed some light on the situation.

As I said previously, I can use windows and all other devices to connect to the router without issue on the private connection. The only one that won't connect is Ubuntu - which uses the same hardware as Windows... And Windows connects, without issue, and retains the connection.

However, I've just put 11.04 Natty on a USB stick and booted from it (NOT installed, only using). This will not connect either, it's not telling me why - it just won't connect and then moves onto the open connection (public) instead...

This is getting verrrrrry confusing.

---

### Post by josephmills on 2011-05-16
in 10.04 go to system-->admin-->synaptic package manager now in the search bar type in wpa do you see the wpa supplicant? look at the pic  if it is installed try to to uninstall it to do this click on the green box and mark for removal then press the apply button then reboot then reinstall the wpa supplicant anything?

---

### Post by karlm on 2011-05-16
> **josephmills said:**
> in 10.04 go to system-->admin-->synaptic package manager now in the search bar type in wpa do you see the wpa supplicant? look at the pic  if it is installed try to to uninstall it to do this click on the green box and mark for removal then press the apply button then reboot then reinstall the wpa supplicant anything?

Gotchya!

Well, I went for a different - and successful - alternative...

It was so complicated, and required the nerves of steel next to the dexterity of a brain surgeon to get this job done.

Yes, you guessed it - I pressed the 'hard reset' button on the router - and 20 seconds later, my laptop connected!

I've got NO idea why some problem came from nowhere, I'd tried a standard reset but it did nothing... That Natty wouldn't work either gave me a niggling suspicion that for some reason the router was rejecting linux. Oddly, my phone is android (linux based) but that isn't rejected.

Anyway, all good now - sorry for the troubles :)

---

### Post by josephmills on 2011-05-16
> **karlm said:**
> Gotchya!

Well, I went for a different - and successful - alternative...

It was so complicated, and required the nerves of steel next to the dexterity of a brain surgeon to get this job done.

Yes, you guessed it - I pressed the 'hard reset' button on the router - and 20 seconds later, my laptop connected!

I've got NO idea why some problem came from nowhere, I'd tried a standard reset but it did nothing... That Natty wouldn't work either gave me a niggling suspicion that for some reason the router was rejecting linux. Oddly, my phone is android (linux based) but that isn't rejected.

Anyway, all good now - sorry for the troubles :)
arghhh I cant belive it glad you got it running ):P

---

