---
title: "USB Wireless Borked"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by dostumai on 2011-10-07
OHAI~
I've gone through everything I could think of - and then some - but my wireless is still hard blocked. Here's a copy/pasta of my system info and st00f™.
Results:
```

dostumai@dossie-cq-craptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux dossie-cq-craptop 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux
dostumai@dossie-cq-craptop:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth
dostumai@dossie-cq-craptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan2     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dostumai@dossie-cq-craptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
dostumai@dossie-cq-craptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
ipt_REJECT             12512  1 
ipt_LOG                12784  5 
xt_limit               12541  7 
parport_pc             32111  0 
xt_tcpudp              12531  8 
ppdev                  12849  0 
vesafb                 13449  1 
ipt_addrtype           12535  4 
xt_state               12514  7 
ip6table_filter        12711  1 
snd_hda_codec_hdmi     27535  1 
ip6_tables             22545  1 ip6table_filter
snd_hda_codec_conexant    43782  1 
nvidia               9766978  42 
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19024  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_hwdep              13274  1 snd_hda_codec
nf_conntrack_ftp       13106  1 nf_nat_ftp
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
iptable_filter         12706  1 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
arc4                   12473  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ip_tables              18125  1 iptable_filter
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
x_tables               21907  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
rtl8187                56206  0 
mac80211              257001  1 rtl8187
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 rtl8187,mac80211
r8712u                281937  0 
soundcore              12600  1 snd
i2c_nforce2            12906  0 
k10temp                12951  0 
psmouse                73312  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
hp_wmi                 13418  0 
uvcvideo               66851  0 
shpchp                 32345  0 
lp                     13349  0 
sparse_keymap          13666  1 hp_wmi
serio_raw              12990  0 
videodev               75143  1 uvcvideo
video                  18951  0 
eeprom_93cx6           12653  1 rtl8187
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
usb_storage            43946  0 
uas                    17676  0 
pata_amd               13762  0 
libahci                25548  1 ahci
forcedeth              58190  0 

```Then I did this after rebooting and seeing the wireless is still hard blocked:
```

dostumai@dossie-cq-craptop:~$ gksudo gedit /etc/rc.local

(gksudo:3404): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",


```And added:
```

rmmod -f ath5k
rfkill unblock all
modprobe ath5k

```to rc.local hoping that would halp, rebooted, pouted, then pondered how many parts my laptop would fragment into if it had a sudden deceleration against a wall. I saw sense eventually; can't afford a new frankentop or laptop for that matter.

So now I'm stuck, not sure how to proceed.
I can has halp plox?
xiexie ni x3

---

### Post by pdc on 2011-10-07
my netbook wireless was hard blocked when I pushed the wrong button ..on the netbook........

---

### Post by wildmanne39 on 2011-10-07
Hi, remove this please:
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Then save and exit.

Then post the results of these commands here please:
```
lspci -nnk | grep -iA2 net
```
```
sudo iwlist scan
```
```
nm-tool
```
```
lsmod | grep rtl
```
```
ndiswrapper -l
```
Thank you

---

