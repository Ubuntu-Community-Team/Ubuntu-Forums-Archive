---
title: "Got wireless working, but really slow"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by wolfmanyoda on 2009-07-11
I used to run Ubuntu 8.? on my laptop and the wireless was very fast. I reformatted the drive and put on 9.4. I had a rough time getting the wireless working but I finally did using a combination of ideas from several posts on this site. 
I don't know what finally made it work, I just know it works.
The problem is that now it's really slow....worse than dial-up slow and I'm on DSL. It's nice and fast if I plug the wire in, but wireless is painful.
I hope someone on here can give me some info on how to speed it up. I haven't changed any hardware so I know it can be faster, it just isn't.

gnusci said to include this info when asking for help, so here it is:

> 
1 ) Machine Brand and Model (PC/Laptop):

Gateway MA3 laptop

> 
2 ) Wireless Brand, Model and Wireless Chipset:
$ lspci


Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

> 
3 ) check interface:

$ iwconfig wlan0

wlan0     IEEE 802.11bg  ESSID:"Yup"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:AE:D5:76   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=73/100  Signal level:0 dBm  Noise level=-11 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> 
4 ) Check for modules:

$ lsmod


Module                  Size  Used by
rfkill_input           12800  0 
binfmt_misc            16776  1 
radeon                342816  2 
ppdev                  15620  0 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_atiixp             24204  3 
snd_atiixp_modem       20360  0 
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_ac97_codec        112292  2 snd_atiixp,snd_atiixp_modem
snd_seq_oss            37760  0 
b43                   131484  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_midi           14336  0 
snd_pcm                82948  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 b43
pcmcia                 44748  0 
cfg80211               38032  1 mac80211
snd                    62628  17 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
tifm_7xx1              13824  0 
psmouse                61972  0 
k8temp                 12416  0 
led_class              12036  1 b43
snd_page_alloc         16904  3 snd_atiixp,snd_atiixp_modem,snd_pcm
ati_agp                14988  0 
tifm_core              15900  1 tifm_7xx1
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
serio_raw              13316  0 
pcspkr                 10496  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
input_polldev          11912  1 b43
i2c_piix4              18448  0 
agpgart                42696  2 drm,ati_agp
video                  25360  0 
shpchp                 40212  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
ssb                    41220  1 b43
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

> 
5 ) Kernel boot messages

$ dmesg


[   24.576338] wlan0: direct probe to AP 00:1c:f0:b8:77:7b try 1
[   24.776059] wlan0: direct probe to AP 00:1c:f0:b8:77:7b try 2
[   24.976030] wlan0: direct probe to AP 00:1c:f0:b8:77:7b try 3
[   25.176052] wlan0: direct probe to AP 00:1c:f0:b8:77:7b timed out
[   46.348371] wlan0: authenticate with AP 00:11:50:ae:d5:76
[   46.548064] wlan0: authenticate with AP 00:11:50:ae:d5:76
[   46.549514] wlan0: authenticated
[   46.549517] wlan0: associate with AP 00:11:50:ae:d5:76
[   46.551801] wlan0: RX AssocResp from 00:11:50:ae:d5:76 (capab=0x431 status=0 aid=1)
[   46.551804] wlan0: associated
[   46.554700] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.661737] b43-phy0 ERROR: PHY transmission error
[   57.176027] wlan0: no IPv6 routers present
[   64.793854] wlan0 direct probe responded
[   64.793864] wlan0: authenticate with AP 00:11:50:ae:d5:76
[   64.795498] wlan0: authenticated
[   64.795502] wlan0: associate with AP 00:11:50:ae:d5:76
[   64.798052] wlan0: RX ReassocResp from 00:11:50:ae:d5:76 (capab=0x431 status=0 aid=1)
[   64.798055] wlan0: associated
[   65.273214] b43-phy0 ERROR: PHY transmission error
[   65.275065] b43-phy0 ERROR: PHY transmission error
[   65.308178] b43-phy0 ERROR: PHY transmission error
[   65.310142] b43-phy0 ERROR: PHY transmission error
[   65.313032] b43-phy0 ERROR: PHY transmission error
[   65.356510] b43-phy0 ERROR: PHY transmission error
[   65.358188] b43-phy0 ERROR: PHY transmission error
[   65.495162] b43-phy0 ERROR: PHY transmission error
[   80.556067] Clocksource tsc unstable (delta = -163382832 ns)
[  527.800069] wlan0: No ProbeResp from current AP 00:11:50:ae:d5:76 - assume out of range
[  529.409035] wlan0: authenticate with AP 00:11:50:ae:d5:76
[  529.416759] wlan0: authenticate with AP 00:11:50:ae:d5:76
[  529.418304] wlan0: authenticated
[  529.418312] wlan0: associate with AP 00:11:50:ae:d5:76
[  529.420957] wlan0: RX ReassocResp from 00:11:50:ae:d5:76 (capab=0x431 status=0 aid=1)
[  529.420963] wlan0: associated
[  531.468124] b43-phy0 ERROR: PHY transmission error
[  587.436069] wlan0: No ProbeResp from current AP 00:11:50:ae:d5:76 - assume out of range
[  589.081017] wlan0: authenticate with AP 00:11:50:ae:d5:76
[  589.081260] wlan0: authenticate with AP 00:11:50:ae:d5:76
[  589.085657] wlan0: authenticated
[  589.085666] wlan0: associate with AP 00:11:50:ae:d5:76
[  589.089692] wlan0: RX ReassocResp from 00:11:50:ae:d5:76 (capab=0x431 status=0 aid=1)
[  589.089701] wlan0: associated
[  591.866416] b43-phy0 ERROR: PHY transmission error
[  591.872537] b43-phy0 ERROR: PHY transmission error

> 
6 ) Network configuration

$ sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: (really? I don't think I should post that)
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=xxx.xxx.x.x multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

> 
7 ) Scan for networks:

$ iwlist scan


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address:  
                    ESSID:"Yup"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level:0 dBm  Noise level=-11 dBm
                    Encryption key:on
                    IE: Unknown: 00054173756B61
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000008ab868917e
                    Extra: Last beacon: 20ms ago

pan0      Interface doesn't support scanning.
> 
8 ) Ubuntu Version:

$ lsb_release -d

Ubuntu 9.04
> 
9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

$ uname -mr

2.6.28-11-generic i686


Thanks for taking the time to check this out.

---

### Post by RavanH on 2009-07-12
Hi, this might be unrelated since I have seen other threads about speed issues in AirForce One cards but I noticed > Bit Rate=1 Mb/s in your post... This is exactly what I ran into with a RT2500 based card. I posted a solution on [http://ubuntuforums.org/showthread.php?p=7605785]("http://ubuntuforums.org/showthread.php?p=7605785") that you might try out. It basically is a switch from Network Manager to Wicd with an added pre-connection script to force higher connection speed...

---

### Post by wolfmanyoda on 2009-07-12
Thank you, I will try this when I get back to my laptop and let you know how it went.

EDIT: it was even easier than you said!

All I did was install wicd, reboot, and connected through wicd. The speed was fantastic without any scripting. 
You rock, thank you.

EDIT II: does anyone know how I can change the title to include [SOLVED]? Thanks!

---

### Post by RavanH on 2009-07-20
> **wolfmanyoda said:**
> ...
EDIT II: does anyone know how I can change the title to include [SOLVED]? Thanks!
Glad it worked. Wicd rulez ;)

You should be able to edit the original post, choose advanced edit (at the bottom) and you can change the title too.

---

