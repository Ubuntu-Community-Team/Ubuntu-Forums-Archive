---
title: "Acer 5630, Netgear N150, wifi problems since upgrade to 11.10"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by kaizen666 on 2011-11-11
Hi, 

I have been having problems with the internet connection on my netgear wifi and acer laptop setup.

Normally after a reset or two it managed to sort itself out, but now it appears to not want to play at all.

I have installed 10.04, 10.10, 11.04 without any problems, so just thought it might be the latest patch.
I sudo updated and upgraded just now and that didn't really do much either.

I have another laptop with xubuntu on and have had no problems.
The wifi constantly asks me for passwords to the router almost every 5 minutes which makes it pretty hard to do anything even with the ethernet on.

We also have 2 other computers and 2 mobile phones on the same router, so we know its not that.

Any help would be appreciated.:)

---

### Post by praseodym on 2011-11-11
Can you show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by kaizen666 on 2011-11-18
Hi, sorry it's not the whole thing, I can relog as my root and try again if you need it all.

Also, I have freezes quite a lot of the time from some of the other programmes, and sometimes just nothing happens when I try to run programmes, I seem to be resetting the system almost every couple of hours atm.

Sorry also for the delay in coming on, hopefully you can appreciate the trouble I'm having is giving me little motivation to use the internet as much as I was.

Here's what I got anyway:


user888@owner-Aspire-5630:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0090]
	Kernel driver in use: b44
user888@owner-Aspire-5630:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0627 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 046d:0896 Logitech, Inc. OrbiCam
user888@owner-Aspire-5630:~$ lsmod
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  7 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
joydev                 17393  0 
binfmt_misc            17292  1 
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
nvidia              10390874  33 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
acer_wmi               23302  0 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
sparse_keymap          13658  1 acer_wmi
arc4                   12473  2 
gspca_vc032x           31999  0 
gspca_main             27610  1 gspca_vc032x
snd_seq_midi           13132  0 
videodev               85626  1 gspca_main
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
iwl3945                73370  0 
snd_seq_midi_event     14475  1 snd_seq_midi
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
psmouse                63474  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
wmi                    18744  1 acer_wmi
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
b44                    31395  0 
ssb                    50682  1 b44
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
video                  18908  0 
user888@owner-Aspire-5630:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Orangeccb25e"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E0:46:9A:05:A6:C6   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-19 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:65   Missed beacon:0

user888@owner-Aspire-5630:~$ sudo iwlist scan

---

### Post by praseodym on 2011-11-18
Please show:

```
sudo iwlist scan
rfkill list
dmesg | grep iwl
ps aux | egrep 'Network|wicd|wpa'
```

---

### Post by kaizen666 on 2011-11-18
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

owner@owner-Aspire-5630:~$ 

it doesn't seem to work :(

---

### Post by praseodym on 2011-11-18
Please show the other outputs, too. I recommend uninstalling the firewall and removing the iptables:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by kaizen666 on 2011-11-18
how long do you think I will keep the firewall down?
Just for the duration of getting the information then re-apply it, or are you recommending that it could be the firewall causing the problem with connecting?

---

### Post by praseodym on 2011-11-18
I think it is caused by the firewall (just test it). In Ubuntu you normally dont need one, because all ports are closed by default and there are no services which need blocks.

You may want to translate this (little bit polemic ;-) ) part of that Wiki-article:

[http://wiki.ubuntuusers.de/Sicherheitskonzepte#Brauche-ich-einen-Virenscanner-und-oder-eine-Firewall](http://wiki.ubuntuusers.de/Sicherheitskonzepte#Brauche-ich-einen-Virenscanner-und-oder-eine-Firewall)

Only if you install server services you really need one. And if you use a hardware router, which should itself contain an activated firewall, you explicitly dont need one.

---

