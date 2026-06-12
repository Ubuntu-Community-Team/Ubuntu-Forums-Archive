---
title: "No wireless only Auto eth0"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by yaielectro on 2011-10-15
Hi! I have a compaq presario V5000 (amd turion 64) and I just turned to linux operating system evrything is working fine but we been fightihg whit FIRE FOX web browser, the wireless conecction it seems like is  working but when we try to load firefox it takes longer to show the page, whatever google or yahoo even as start page and it says no server connection found, like not having  wireless conection,but I have it on, but if you grab the LAN cable directly from the router (D LINK brand I think)and plugged in,the Auto eth0 conection is detect and firefox is able to go any site and works wonderfull,but you now that this a problem,that is why I am posting this,this is extrange because we been fixing several computers and now we are stuck, so if some one can help us i will be great.

---

### Post by wildmanne39 on 2011-10-15
Hi, welcome to the forum! Please open a terminal ctrl+alt+t then copy and paste the commands into the terminal then paste the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by yaielectro on 2011-10-17
Thanks unlimited for your help, we, i and my son are  new, beguiners on terminal and comads..we swiched up to ubunto one year ago and recomend everybody computer user to change for linux ubunto...the best fron Costa Rica Central America for All of You...hope we did the task you asked rigth..yaielectro...

anan@anan-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux anan-laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
anan@anan-laptop:~$ sudo lshw -C network
[sudo] password for anan: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:07:46:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:a1:f6:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
anan@anan-laptop:~$ lspci -nnk | grep -iA2 net
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
anan@anan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
anan@anan-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
anan@anan-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
ipt_REJECT              1928  1 
ipt_LOG                 4542  4 
xt_limit                1382  6 
xt_tcpudp               2011  7 
ipt_addrtype            1599  4 
binfmt_misc             6587  1 
xt_state                1098  9 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ip6table_filter         1248  1 
ip6_tables             11102  1 ip6table_filter
nf_nat_irc              1124  0 
joydev                  8740  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
snd_atiixp_modem        9103  0 
nf_conntrack_ipv4      10346  11 nf_nat
snd_atiixp             12446  2 
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_ac97_codec        100646  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
nf_conntrack           60943  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
snd_seq_dummy           1338  0 
ip_tables               9899  1 iptable_filter
snd_seq_oss            26722  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
radeon                678735  3 
b43                   163556  0 
x_tables               14175  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ttm                    49847  1 radeon
mac80211              205402  1 b43
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 radeon
cfg80211              126112  2 b43,mac80211
ati_agp                 5094  0 
drm                   163651  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
led_class               2864  1 b43
video                  17375  0 
output                  1871  1 video
snd                    54244  15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
agpgart                31724  3 ttm,ati_agp,drm
k8temp                  3152  0 
shpchp                 28835  0 
i2c_piix4               8335  0 
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_atiixp_modem,snd_atiixp,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
8139too                18545  0 
hid                    67288  1 usbhid
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
pata_atiixp             3148  2 
ssb                    38934  1 b43
usb_storage            39841  1 
anan@anan-laptop:~$ lsmod

---

### Post by pdc on 2011-10-17
from this post

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I think you need the b43 driver and I believe the command is

> sudo apt-get install b43-fwcutter firmware-b43-installer

I think it will be near midnight in New Mexico and wildemann may well be asleep; you may wish to wait a few hours to check with him if he would agree with the above

---

### Post by yaielectro on 2011-10-17
Thanks friends we installed the bradcom driver, before this no was possible wireless conection, not the blue ligth on icon like anttena and no indication of wireless conection...the only problem is no navegate, mean no firefox.. only in wireless conection, with lan wire  pluged directly from router all is ok,,we tried  with two different routers...in wireless... of course we unplug Lan cable to switch to wireless..inmediately the machine beguing conecting  to 100% to the router...gracias mil yaielectro Costa Rica CA

---

### Post by wildmanne39 on 2011-10-17
HI, so you can connect with wireless now? if so would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

