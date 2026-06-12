---
title: "Dell Inspiron 17R SE 7720 / Intel 2230"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by Timur Ridjanovic on 2013-04-05
I just bought my self a new laptop: Dell Inspiron 17R SE 7720 and installed Ubuntu 12.04.1 LTS 64 bits. However, my wireless connection isnt working... Actually, sometimes it will connect for like a minute and disconnect after that, but that is a rare occurrence. My wireless card is an intel2230. Since I'm new to Ubuntu, I'm not sure how to download dell drivers on Ubuntu. It seems that a lot of people with the Dell 17r have had that problem with wireless, according to my searches, but I haven't found a solution. Can somebody help me please?

Thanks!

---

### Post by praseodym on 2013-04-05
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by tannurishu on 2013-04-06
root@ubuntu:~# lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0564]
    Kernel driver in use: r8169
root@ubuntu:~# lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:644b Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 
root@ubuntu:~# lsmod
Module                  Size  Used by
pppoe                  17511  2 
pppox                  13158  1 pppoe
ipt_MASQUERADE         12663  1 
iptable_filter         12706  1 
iptable_nat            12977  1 
nf_nat                 20316  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      14080  3 iptable_nat,nf_nat
nf_conntrack           66307  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              17791  2 iptable_filter,iptable_nat
x_tables               21898  4 ipt_MASQUERADE,iptable_filter,iptable_nat,ip_tables
bridge                 79264  0 
stp                    12811  1 bridge
llc                    14160  2 bridge,stp
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_idt      59761  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
dell_laptop            17161  0 
dcdbas                 14054  1 dell_laptop
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
microcode              18209  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rts5139               281367  0 
btusb                  17950  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               71277  0 
psmouse                84843  0 
videobuf2_core         32070  1 uvcvideo
serio_raw              13031  0 
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16925  0 
i915                  457161  3 
mei                    35796  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
wmi                    18590  1 dell_wmi
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  16 
bnep                   17707  2 
bluetooth             183228  22 btusb,rfcomm,bnep
binfmt_misc            17260  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
r8169                  55976  0 
root@ubuntu:~# iwconfig
ppp0      no wireless extensions.

pan1      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:~# rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by Timur Ridjanovic on 2013-04-06
timur@timur:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4462]
	Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0578]
	Kernel driver in use: r8169




timur@timur:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:58bf Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 8087:07da Intel Corp.



timur@timur:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:58bf Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 8087:07da Intel Corp. 





timur@timur:~$ lsmod
Module                  Size  Used by
btusb                  18332  2 
nls_utf8               12557  0 
udf                    94613  0 
crc_itu_t              12707  1 udf
bnep                   18281  2 
rfcomm                 47604  12 
bluetooth             180153  23 btusb,bnep,rfcomm
parport_pc             32866  0 
nvidia               9367655  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
uvcvideo               72627  0 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rts5139               351188  0 
videodev               98259  1 uvcvideo
snd_seq_midi           13324  0 
i915                  477626  2 
v4l2_compat_ioctl32    17128  1 videodev
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            18119  0 
psmouse                97485  0 
iwlwifi               401140  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14490  1 dell_laptop
i2c_algo_bit           13423  1 i915
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi               12681  0 
serio_raw              13211  0 
sparse_keymap          13890  1 dell_wmi
video                  19651  1 i915
mei                    41616  0 
soundcore              15091  1 snd
mac80211              506862  1 iwlwifi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205774  2 iwlwifi,mac80211
wmi                    19256  1 dell_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0 





timur@timur:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ThomsonB0AFE0"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:98:35:B0:AF:E0   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:21   Missed beacon:0


eth0      no wireless extensions.




timur@timur:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2013-04-07
@ tannurishu:

You need to install a patched driver version for this card:
```

sudo mkdir /usr/src/hybrid-portsrc_x86_64-5.100.82.112
wget http://media.cdn.ubuntu-de.org/forum/attachments/10/06/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz
sudo tar xvf 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-5.100.82.112 
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112
sudo dkms build -m hybrid-portsrc_x86_64 -v 5.100.82.112
sudo dkms install -m hybrid-portsrc_x86_64 -v 5.100.82.112 
```
From here: [http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)
Do not activate the Broadcom-STA driver in "additional drivers"!!!

@Timur Ridjanovic 

Deactivate the N-mode of your driver (bug)
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

