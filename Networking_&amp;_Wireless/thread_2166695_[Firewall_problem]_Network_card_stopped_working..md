---
title: "[Firewall problem] Network card stopped working."
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by Jonathan Precise on 2013-08-10
Hello all!

I have an HP 2000 notebook PC. I installed ubuntu 13.04 Raring Ringtail (dual-booting with windows 8) on it and it worked flawlessly.:)

However one day, when I was checking for updates, I got an error message, saying to check my internet connection.:shock: My network status icon said it was connected. I tried going on to Google, and it said something like "not available". Every site I went to had the same error message. Restarting the computer didn't fix the problem. I reset the router, connected an Ethernet cable, reconnected the cable, disconnected the cable, checked the modem, and reconnected my wireless connection to the internet. _**Nothing worked!!!**_

Oddly enough, the other computers did have an internet connection. Also, when booting the Windows side of the HP notebook, the problem disappeared. The problem reappeared when booting back into ubuntu.

I'm so confused!!!:confused: Does anyone know what's going on!!?

---

### Post by praseodym on 2013-08-10
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Checked the BIOS?

---

### Post by wildmanne39 on 2013-08-10
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Jonathan Precise on 2013-08-10
Hello praseodym!

This is the result of all the commands (the user and computer-name have been blanked out on purpose):

```
-@-:~$ lspci -nnk | grep -iA2 net03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:188b]
	Kernel driver in use: r8169
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1Ã—1 Wi-Fi Adapter [103c:1838]
	Kernel driver in use: ath9k
owner@ubuntu-hp-2000-notebook:~$ lsusb
Bus 001 Device 003: ID 048d:1167 Integrated Technology Express, Inc. 
Bus 002 Device 002: ID 0bda:58de Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
-@-:~$ lsmod
Module                  Size  Used by
usb_storage            57204  1 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228667  10 bnep,rfcomm
dm_crypt               22820  0 
binfmt_misc            17500  1 
nls_iso8859_1          12713  2 
nf_conntrack_ipv6      18335  5 
nf_defrag_ipv6         13201  1 nf_conntrack_ipv6
xt_hl                  12521  6 
ip6t_rt                12529  3 
ip6t_REJECT            12545  3 
xt_LOG                 17400  12 
xt_multiport           12597  12 
xt_limit               12711  15 
xt_tcpudp              12603  46 
nf_conntrack_ipv4      14487  5 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  10 
xt_addrtype            12635  4 
ipt_REJECT             12541  3 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12620  0 
nf_nat                 25867  1 nf_nat_ftp
nf_conntrack_ftp       13342  1 nf_nat_ftp
nf_conntrack           83275  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_state,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
ip_tables              26995  1 iptable_filter
videobuf2_memops       13202  1 videobuf2_vmalloc
kvm_amd                59717  0 
videobuf2_core         40513  1 uvcvideo
x_tables               29803  14 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_state,xt_LOG,xt_multiport,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
videodev              129260  2 uvcvideo,videobuf2_core
kvm                   443165  1 kvm_amd
joydev                 17377  0 
arc4                   12615  2 
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413629  2 ath9k_common,ath9k
microcode              22881  0 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
rtsx_pci_ms            13011  0 
psmouse                95870  0 
memstick               16554  1 rtsx_pci_ms
k10temp                13126  0 
cfg80211              510937  3 ath,ath9k,mac80211
snd_hda_codec_realtek    78399  1 
serio_raw              13215  0 
snd_hda_codec_hdmi     36913  1 
i2c_piix4              13266  0 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
rtsx_pci_sdmmc         17475  0 
wmi                    19070  1 hp_wmi
video                  19390  0 
radeon                942029  3 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67466  0 
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
drm                   286028  5 ttm,drm_kms_helper,radeon
ahci                   25731  3 
libahci                31364  1 ahci
-@-:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Casa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:90:9B:B7   
          Bit Rate=11 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


-@-:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
-@-:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search cfl.rr.com
```

---

### Post by Jonathan Precise on 2013-08-10
Hello Mr. Wild Man!

Unfortunately, ./wireless_script has an output of:

```
bash: ./wireless_script: No such file or directory
```

Running it by double-clicking, and then clicking on "Run" does nothing.

---

### Post by Jonathan Precise on 2013-08-10
Disabled firewall. Now Internet works!

Thread marked as solved.

---

