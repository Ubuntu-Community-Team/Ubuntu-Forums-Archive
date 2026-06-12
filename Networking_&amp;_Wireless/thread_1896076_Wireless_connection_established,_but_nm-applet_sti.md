---
title: "Wireless connection established, but nm-applet still shows disconnected"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by mudong on 2011-12-16
Hello, guys, 

I am using Xubuntu 11.10 on an Eee PC t91mt. My system is up to date. On the machine, the network manager applet isn't showing any connections(always show the red "X") even though a previous configured wireless network will always connect automatically.

This really bothers me because Ubuntu One also thinks it's not connected. It's been going on for at least several weeks and I've spend a lot of time searching for solutions without any luck. 

Please help, many thanks.

Ron

---

### Post by praseodym on 2011-12-16
Hi,

please show the terminal (CTRL+ALT+T) outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
sudo iwlist scan
```

---

### Post by mudong on 2011-12-16
thanks, I will check

---

### Post by praseodym on 2011-12-16
The driver iwlagn is buggy, you need to deactivate the N-mode:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
Check:
```
iwlist chan
iwconfig
dmesg | egrep 'iwl|country'
```

---

### Post by mudong on 2011-12-16
praseodym: I am very sorry. The output in my last reply was from another ubuntu desktop, not the one I am having problem with. Really sorry about that.

Please check out the output below. It's from my EeePC t91mt. thanks.

```
ron@t91mt:$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave Device [1a3b:1089]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
ron@t91mt:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:509b IMC Networks 
Bus 004 Device 002: ID 0486:0185 ASUS Computers, Inc. EeePC T91MT HID Touch Panel
ron@t91mt:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
dm_crypt               22565  1 
ppdev                  12849  0 
joydev                 17393  0 
sch_gpio               12960  0 
i2c_isch               12662  0 
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  0 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
hid_multitouch         12851  0 
serio_raw              12990  0 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
snd_seq_midi_event     14475  1 snd_seq_midi
lpc_sch                12653  0 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
arc4                   12473  2 
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
xt_limit               12541  12 
ath9k                 112711  0 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
mac80211              393459  1 ath9k
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
snd_timer              28932  2 snd_pcm,snd_seq
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
cfg80211              172427  3 ath9k,mac80211,ath
snd                    55902  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13489  2 
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
pata_sch               12703  2 
atl1c                  36638  0 
poulsbo                12552  0 
video                  18908  1 poulsbo
wmi                    18744  1 asus_wmi
ron@t91mt:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
ron@t91mt:~$ sudo iwlist scan
[sudo] password for ron: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 40:16:9F:D6:88:8C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"MERCURY_D6888C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a005b8ee9
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000E4D4552435552595F443638383843
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331A6E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606051700000000000000000000000000000000000000
                    IE: Unknown: 341606051700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700100000000000001000000040169FD6888C1021000754502D4C494E4B10230009544C2D57523734304E10240003312E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101
          Cell 02 - Address: 00:23:CD:A6:92:62
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_A69262"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019e3513aa6
                    Extra: Last beacon: 428ms ago
                    IE: Unknown: 000E54502D4C494E4B5F413639323632
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000023CDA692620223CDA6926264002C010808
          Cell 03 - Address: E0:05:C5:64:15:CE
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_Jessica"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000031a71bc0b
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000F54502D4C494E4B5F4A657373696361
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000E005C56415CEE205C56415CE64002C010808

```

---

### Post by praseodym on 2011-12-16
Ok,

for the Atheros driver you should deactivate the hardware encryption:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Do you need a firewall? If not deactivate/uninstall it:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by mudong on 2011-12-16
I executed the code below
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

I do need a firewall, so I didn't disable it. 

But after I reboot, nothing changed. I can still connect to the wireless network, but network manager applet and Ubuntu One still show disconnected. I forgot to mention that wicd network manager applet works well.

---

### Post by praseodym on 2011-12-16
Both network-managers dont normally work well in parallel. Choose one and uninstall the other completely.

---

### Post by mudong on 2011-12-16
I deleted wicd a while ago, now only the default network manager is in place.

---

### Post by praseodym on 2011-12-16
So why not using Wicd instead?

---

### Post by mudong on 2011-12-16
Without wicd, I can still connect to the default wireless network which I setup before, even though the default network manager applet doesn't recognise it and shows disconnected (the red "X"). 

The thing that really bothers me is that Ubuntu One doesn't think it's connected to the Internet either. I cannot sync data using Ubuntu One with other machines. 

I figured the default network manager and Ubuntu One must share the same error since they both don't recognised connected wireless connection. If I make one work, the other should work as well.

That's why I am trying to fix the default network manager applet.

---

### Post by fdrake on 2011-12-16
> **mudong said:**
> Without wicd, I can still connect to the default wireless network which I setup before, even though the default network manager applet doesn't recognise it and shows disconnected (the red "X"). 

The thing that really bothers me is that Ubuntu One doesn't think it's connected to the Internet either. I cannot sync data using Ubuntu One with other machines. 

I figured the default network manager and Ubuntu One must share the same error since they both don't recognised connected wireless connection. If I make one work, the other should work as well.

That's why I am trying to fix the default network manager applet.

how did you verify you are connected? can you ping?
```

ping google.com

```

---

### Post by mudong on 2011-12-16
I can post to this forum, that's one clue. :)

---

### Post by fdrake on 2011-12-16
> **mudong said:**
> I can post to this forum, that's one clue. :)
i guess that's good enough to prove it! :D

---

### Post by mudong on 2011-12-17
Guys, are there more inputs on this? thanks

---

