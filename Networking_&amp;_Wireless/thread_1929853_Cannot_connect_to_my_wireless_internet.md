---
title: "Cannot connect to my wireless internet"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by rozelle25 on 2012-02-22
I'm a newbie, just dual installed last night. I'm not able to connect to the internet. My password is entered correctly. It just looks like it's connecting and then stops. I tired searchin the internet as this seems to be a common problem. However, it looks like there are a million different solutions and for someone coming from windows it made me dizzy. Every other device can connect to my network (PC, aptop, phone, tablet, etc.). Any help would be appreciated.

---

### Post by Lee_Bo on 2012-02-22
If you have security enabled, turn it off and see if you can connect.  If you can then it may be a security type Ubuntu doesn't work well with.

---

### Post by ajgreeny on 2012-02-22
What is your wireless adapter make?  Let's see the output of the command ```
lspci
``` in terminal if you don't know what make it is.

---

### Post by rozelle25 on 2012-02-22
Thanks for responding. I got home from work and logged on and it connected automatically. Unfortunately it is painfully slow to the point where I can't really do anything.

---

### Post by rozelle25 on 2012-02-22
Crap. Just read up some more (because my wireless network is not connecting)...should someone inexperienced like me be on 10.04? I just want to try to learn. Is this going to be a pain if I already have 11.10 installed on my D drive in Windows 7? Thanks for your patience.

---

### Post by ajgreeny on 2012-02-23
I can't comment on your 11.10 wubi install inside windows as I have never used it and don't have windows.  Wubi is only really intended as a test installation of ubuntu to see if you wish to run a proper installation, and was never meant as a long term OS installation.

You still did not tell us your wireless card make.

---

### Post by rozelle25 on 2012-02-23
> **ajgreeny said:**
> I can't comment on your 11.10 wubi install inside windows as I have never used it and don't have windows. Wubi is only really intended as a test installation of ubuntu to see if you wish to run a proper installation, and was never meant as a long term OS installation.
 
You still did not tell us your wireless card make.
 
Would it be Intel Corp 5 series/3400 series?

---

### Post by wildmanne39 on 2012-02-23
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by rozelle25 on 2012-02-23
> **wildmanne39 said:**
> Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
 
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you
 
I have the output. And now for the dumb question: I'm on a laptop now while ubuntu is on my PC (without internet) how am I supposed to post here?

---

### Post by wildmanne39 on 2012-02-23
Hi paste it to a flash drive then use the computer with internet to post here.
Thanks

---

### Post by rozelle25 on 2012-02-23
```
rozelle25@ubuntu:~$ cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS" 
Linux ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux 
rozelle25@ubuntu:~$ lspci -nnk | grep -A2 net 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03) 
	Kernel driver in use: r8169 
	Kernel modules: r8169 
rozelle25@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:"spcrozelle"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 94:44:52:5A:2B:40   
          Bit Rate=1 Mb/s   Tx-Power=21 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

rozelle25@ubuntu:~$ rfkill list all 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
rozelle25@ubuntu:~$ lsmod 
Module                  Size  Used by 
aes_i586                7268  2 
aes_generic            26863  1 aes_i586 
ipt_MASQUERADE          1407  0 
xt_state                1098  0 
ipt_REJECT              1928  0 
xt_tcpudp               2011  0 
iptable_filter          2271  0 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323 
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp 
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp 
nf_nat_proto_gre        1259  1 nf_nat_pptp 
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp 
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip 
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc 
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp 
iptable_nat             4414  0 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat 
nf_conntrack_ipv4      10672  3 iptable_nat,nf_nat 
nf_conntrack           61615  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4 
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4 
ip_tables               9991  2 iptable_filter,iptable_nat 
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel 
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
i915                  289715  3 
snd_timer              19130  2 snd_pcm,snd_seq 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
drm_kms_helper         29329  1 i915 
rt2500usb              18173  0 
rt2x00usb               9639  1 rt2500usb 
rt2x00lib              27573  2 rt2500usb,rt2x00usb 
led_class               2864  1 rt2x00lib 
mac80211              205434  2 rt2x00usb,rt2x00lib 
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
joydev                  8740  0 
psmouse                63677  0 
drm                   163747  4 i915,drm_kms_helper 
i2c_algo_bit            5028  1 i915 
cfg80211              126528  2 rt2x00lib,mac80211 
serio_raw               3978  0 
intel_agp              24375  2 i915 
soundcore               6620  1 snd 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
agpgart                31724  2 drm,intel_agp 
asus_atk0110            9017  0 
video                  17375  1 i915 
output                  1871  1 video 
lp                      7028  0 
parport                32635  2 ppdev,lp 
usbhid                 36110  0 
hid                    67288  1 usbhid 
ohci1394               26950  0 
usb_storage            40033  0 
ieee1394               81181  1 ohci1394 
r8169                  34140  0 
mii                     4381  1 r8169 
rozelle25@ubuntu:~$ 
```

---

### Post by rozelle25 on 2012-02-23
Also, I'm on 10.04 now

---

### Post by wildmanne39 on 2012-02-23
Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2500usb
sudo modprobe rt2500usb nohwcrypt=1
sudo ifconfig wlan0 up

```
unplug your wired connection before you run the commands and do not reboot after, if it works we will need to make it permanent.
Thanks

---

### Post by rozelle25 on 2012-02-23
> **wildmanne39 said:**
> Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2500usb
sudo modprobe rt2500usb nohwcrypt=1
sudo ifconfig wlan0 up

```
unplug your wired connection before you run the commands and do not reboot after, if it works we will need to make it permanent.
Thanks

Sorry, are you talking about my router in the basement?? I'm connected wireless on all devices.

---

### Post by wildmanne39 on 2012-02-23
Hi, no run the commands one line at a time in the terminal and follow the directions in my previous post.
Thanks

---

### Post by rozelle25 on 2012-02-23
> **wildmanne39 said:**
> Hi, no run the commands one line at a time in the terminal and follow the directions in my previous post.
Thanks

What do you mean by unplug wired connection? I got an error when running the first command: no such device

---

### Post by wildmanne39 on 2012-02-23
Hi, > What do you mean by unplug wired connection?never mind you do not have a wired connection, all commands should work so please copy and paste for accuracy.
Thanks

---

### Post by rozelle25 on 2012-02-23
Sorry, fat fingers-I ran the four commands, nothing happened

---

### Post by wildmanne39 on 2012-02-23
Hi, please run this code but copy and paste.
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
add above exit 0.
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
save gedit, close and reboot.
Thanks

---

### Post by rozelle25 on 2012-02-23
I followed the instructions. It says I'm connected to my wireless network but I can't do anything on the internet.

---

### Post by rozelle25 on 2012-02-23
OK-now I'm in-but I've been connected for a few minutes before and dropped. Fingers crossed...

---

### Post by wildmanne39 on 2012-02-23
Hi, ok I will cross my toes too.
Thanks

---

### Post by rozelle25 on 2012-02-23
> **wildmanne39 said:**
> Hi, ok I will cross my toes too.
Thanks

Looks like I can be marked "solved". Thank you very much for your time and patience. I've since rebooted and connected automatically and even downloaded a bunch of stuff some website told me to download. Now I gotta figure out what all the stuff does. Thanks again.

---

### Post by wildmanne39 on 2012-02-23
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Enjoy

---

### Post by rozelle25 on 2012-02-25
> **wildmanne39 said:**
> Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Enjoy

I made my way to 11.04 and I can't connect again. I was able to connect on 10.10. Thoughts?

---

### Post by wildmanne39 on 2012-02-25
Hi, please post the output from the commands in post 8 again since you switched to 11.04 and add:
```
modinfo rt2500usb
lsusb
```
Thanks

---

### Post by rozelle25 on 2012-02-26
```
rozelle25@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-13-generic-pae #55-Ubuntu SMP Tue Jan 24 15:54:51 UTC 2012 i686 i686 i386 GNU/Linux
rozelle25@ubuntu:~$ lspci -nnk | grep -A2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169
rozelle25@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
rozelle25@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
rozelle25@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1
parport_pc             32111  0
ppdev                  12849  0
snd_hda_codec_hdmi     27535  1
snd_hda_codec_realtek   255882  1
arc4                   12473  2
snd_hda_intel          28209  2
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13666  0
rt2500usb              22621  0
rt2x00usb              19693  1 rt2500usb
rt2x00lib              39075  2 rt2500usb,rt2x00usb
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  2 rt2x00usb,rt2x00lib
i915                  451088  3
joydev                 17322  0
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                59039  0
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0
drm_kms_helper         40971  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
asus_atk0110           17664  0
drm                   184164  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0
hid                    77084  1 usbhid
usb_storage            43946  1
uas                    17676  0
firewire_ohci          31504  0
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  46630  0
rozelle25@ubuntu:~$ modinfo rt2500usb
filename:       /lib/modules/2.6.38-13-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
license:        GPL
description:    Ralink RT2500 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     A3F96D630A58E6940AE263F
alias:          usb:v5A57p0260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F88p3012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p11F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0681p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v079Bp004Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0097d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p008Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p005Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1706d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb
vermagic:       2.6.38-13-generic-pae SMP mod_unload modversions 686
parm:           nohwcrypt:Disable hardware encryption. (bool)
rozelle25@ubuntu:~$ lsusb
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 13b1:000d Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]
Bus 001 Device 004: ID 0bc2:2101 Seagate RSS LLC
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rozelle25@ubuntu:~$

```

---

### Post by wildmanne39 on 2012-02-26
Hi, first do what is in post 19 of this thread then please do:
```
gksudo gedit /etc/modprobe.d/rt2500usb.conf
```
Add a one line:
```
options rt2500usb nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by rozelle25 on 2012-02-26
I still can't connect. By following the instructions I edited 2 documents.

---

### Post by wildmanne39 on 2012-02-26
Hi, post the out put of those 2 files so we can make sure they held the configuration, plus these commands as well.
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by rozelle25 on 2012-02-26
```
rozelle25@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500usb
  State:             disconnected
  Default:           no
  HW Address:        00:12:17:A3:C2:94

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
    cfgmfsf:         Infra, 00:22:75:5C:D4:32, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    spcrozelle:      Infra, 94:44:52:5A:2B:40, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2
    07FX12013160:    Infra, 00:12:0E:93:04:14, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WEP
    Ron Network:     Infra, 00:22:6B:A7:E1:0D, Freq 2457 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    NETGEAR-24-G:    Infra, C0:3F:0E:7D:CF:D1, Freq 2417 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        48:5B:39:F2:78:76

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


rozelle25@ubuntu:~$ sudo iwlist scan
[sudo] password for rozelle25:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 94:44:52:5A:2B:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"spcrozelle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dc4a4a81e
                    Extra: Last beacon: 836ms ago
                    IE: Unknown: 000A737063726F7A656C6C65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
          Cell 02 - Address: 00:22:75:5C:D4:32
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"cfgmfsf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000035fbda09299
                    Extra: Last beacon: 13696ms ago
                    IE: Unknown: 00076366676D667366
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0113FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EC0113FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: DDA90050F204104A0001101044000101103B00010310470010775B6680BFDE11D38D2F0022755CD4321021001442656C6B696E20496E7465726E6174696F6E616C102300114E20576972656C65737320526F757465721024000C463544383233362D342076331042000E32303931353832333630333530311054000800060050F20400011011001842656C6B696E204E20576972656C65737320526F75746572100800020084103C000101
          Cell 03 - Address: 00:26:F2:C2:B8:58
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"GSI45613218"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000043338d61db2
                    Extra: Last beacon: 1164ms ago
                    IE: Unknown: 000B4753493435363133323138
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD810050F204104A000110104400010210570001011041000100103B000103104700104B31F83B5657B06B652287A3A772AD2F1021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
          Cell 04 - Address: C0:3F:0E:7D:CF:D1
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR-24-G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b69f594c0
                    Extra: Last beacon: 1112ms ago
                    IE: Unknown: 000C4E4554474541522D32342D47
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD890050F204104A0001101044000102103B0001031047001000000000000010000000C03F0E7DCFD11021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F20400011011001A574E44523337303028576972656C6573732041502D322E344729100800020086103C000103
          Cell 05 - Address: 00:22:6B:88:FA:B8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"dsaw"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001170dceeb51
                    Extra: Last beacon: 836ms ago
                    IE: Unknown: 000464736177
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 06 - Address: 58:6D:8F:6F:0C:9C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Beaches"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b79488897d
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 000742656163686573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001027A0D48ACA51878AECC0BA99C904D57210210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:12:0E:93:04:14
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"07FX12013160"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000055eb5239
                    Extra: Last beacon: 872ms ago
                    IE: Unknown: 000C303746583132303133313630
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 08 - Address: 00:22:6B:A7:E1:0D
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Ron Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004f446e110b1
                    Extra: Last beacon: 568ms ago

rozelle25@ubuntu:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
rozelle25@ubuntu:~$ sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
Feb 26 14:31:12 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Feb 26 14:31:12 ubuntu NetworkManager[854]: <info> (wlan0): supplicant interface state:  starting -> ready
Feb 26 14:31:12 ubuntu wpa_supplicant[1015]: Failed to initiate AP scan.
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) starting connection 'Auto spcrozelle'
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0/wireless): access point 'Auto spcrozelle' has security, but secrets are required.
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0/wireless): connection 'Auto spcrozelle' has security, and secrets exist.  No new secrets needed.
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 26 14:31:28 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Feb 26 14:31:29 ubuntu wpa_supplicant[1015]: Trying to associate with 94:44:52:5a:2b:40 (SSID='spcrozelle' freq=2437 MHz)
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  scanning -> associating
Feb 26 14:31:29 ubuntu kernel: [   27.991164] wlan0: authenticate with 94:44:52:5a:2b:40 (try 1)
Feb 26 14:31:29 ubuntu kernel: [   27.992763] wlan0: authenticated
Feb 26 14:31:29 ubuntu kernel: [   28.006784] wlan0: associate with 94:44:52:5a:2b:40 (try 1)
Feb 26 14:31:29 ubuntu kernel: [   28.011802] wlan0: RX AssocResp from 94:44:52:5a:2b:40 (capab=0x411 status=0 aid=5)
Feb 26 14:31:29 ubuntu kernel: [   28.011808] wlan0: associated
Feb 26 14:31:29 ubuntu wpa_supplicant[1015]: Associated with 94:44:52:5a:2b:40
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  associating -> associated
Feb 26 14:31:29 ubuntu kernel: [   28.015488] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Feb 26 14:31:29 ubuntu wpa_supplicant[1015]: WPA: Key negotiation completed with 94:44:52:5a:2b:40 [PTK=CCMP GTK=CCMP]
Feb 26 14:31:29 ubuntu wpa_supplicant[1015]: CTRL-EVENT-CONNECTED - Connection to 94:44:52:5a:2b:40 completed (auth) [id=0 id_str=]
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'spcrozelle'.
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 26 14:31:29 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Feb 26 14:31:30 ubuntu NetworkManager[854]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Feb 26 14:31:30 ubuntu dhclient: Listening on LPF/wlan0/00:12:17:a3:c2:94
Feb 26 14:31:30 ubuntu dhclient: Sending on   LPF/wlan0/00:12:17:a3:c2:94
Feb 26 14:31:30 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Feb 26 14:31:30 ubuntu avahi-daemon[852]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::212:17ff:fea3:c294.
Feb 26 14:31:30 ubuntu avahi-daemon[852]: New relevant interface wlan0.IPv6 for mDNS.
Feb 26 14:31:30 ubuntu avahi-daemon[852]: Registering new address record for fe80::212:17ff:fea3:c294 on wlan0.*.
Feb 26 14:31:33 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Feb 26 14:31:36 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Feb 26 14:31:39 ubuntu kernel: [   38.473857] wlan0: no IPv6 routers present
Feb 26 14:31:40 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Feb 26 14:31:44 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Feb 26 14:31:51 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Feb 26 14:31:54 ubuntu wpa_supplicant[1015]: WPA: Group rekeying completed with 94:44:52:5a:2b:40 [GTK=CCMP]
Feb 26 14:31:54 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  completed -> group handshake
Feb 26 14:31:54 ubuntu NetworkManager[854]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Feb 26 14:32:00 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Feb 26 14:32:13 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Feb 26 14:32:15 ubuntu NetworkManager[854]: <warn> (wlan0): DHCPv4 request timed out.
Feb 26 14:32:15 ubuntu NetworkManager[854]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1531
Feb 26 14:32:15 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Feb 26 14:32:15 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Feb 26 14:32:15 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Feb 26 14:32:15 ubuntu NetworkManager[854]: <warn> Activation (wlan0) failed for access point (spcrozelle)
Feb 26 14:32:15 ubuntu NetworkManager[854]: <warn> Activation (wlan0) failed.
Feb 26 14:32:15 ubuntu NetworkManager[854]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Feb 26 14:32:15 ubuntu NetworkManager[854]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Feb 26 14:32:15 ubuntu NetworkManager[854]: <info> (wlan0): deactivating device (reason: 0).
Feb 26 14:32:15 ubuntu kernel: [   74.387753] wlan0: deauthenticating from 94:44:52:5a:2b:40 by local choice (reason=3)
Feb 26 14:32:15 ubuntu wpa_supplicant[1015]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
rozelle25@ubuntu:~$

```

---

### Post by wildmanne39 on 2012-02-26
Hi, is spcrozelle the network you are trying to connect too?

I still need to to what is in the 2 files I asked you to modify please.
Thanks

---

### Post by rozelle25 on 2012-02-26
> **wildmanne39 said:**
> Hi, is spcrozelle the network you are trying to connect too?

I still need to to what is in the 2 files I asked you to modify please.
Thanks

spcrozelle=yes

I modified the two files-are you asking me to post them here to check out?

---

### Post by wildmanne39 on 2012-02-26
Hi, yes please post them here I want to make sure nothing weird happened when you changed the files because sometimes things do not go as planned.
Thanks

---

### Post by rozelle25 on 2012-02-26
#!/bin/sh
/sbin/iwconfig wlan0 power off


options rt2500usb nohwcrypt=1

---

### Post by wildmanne39 on 2012-02-27
Hi, those lines are correct but I just want to make sure they are in two different files correct and not the same one? 

If so then I recommend installing wicd from software center, just know that it will not show up in the top panel like network manager does, then remove network manager with this command:
```
sudo apt-get purge network-manager network-manager-gnome
```
Then reboot and setup your connection in wicd.
Thanks

---

### Post by rozelle25 on 2012-02-28
How can I download anything when ubuntu is not connecting to the internet?

---

### Post by wildmanne39 on 2012-02-28
Hi, the title says you can not connect to wireless internet, so use a wired connection or tether your cell phone to your computer. 
Thanks

---

