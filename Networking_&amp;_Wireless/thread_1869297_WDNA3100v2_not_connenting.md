---
title: "WDNA3100v2 not connenting"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by mohali26 on 2011-10-25
I need help to connect my WDNA3100v 2 to ubuntu.

---

### Post by praseodym on 2011-10-25
Hello,

for this stick with broadcom chipset you need "ndiswrapper" and a windows driver. With a wired connection just copy/paste the following lines into a terminal (open it with CTRL+ALT+T):

```
sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2955302/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2955302/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)
tar xvf Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz
```
For a 32bit system:
```
sudo ndiswrapper -i bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
```
For 64bit:
```
sudo ndiswrapper -i bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
```
Continue: Check, if the driver is present with
```
ndiswrapper -l
```
and load the module:
```
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
```
Replug the stick and check:

```
lsmod
dmesg | grep ndis
lsusb
iwconfig
sudo iwlist scan
cat /etc/modprobe.d/ndiswrapper.conf
```
There is no Draft-N/Dualband with this driver (blame Broadcom for that ;-) )

---

### Post by mohali26 on 2011-10-27
thank you for your help i will try it out.:D

---

### Post by Steve54 on 2011-10-27
I am also new to this so don't shout if I'm wrong :P.
 
As you are using the ndis wrapper is there any reason why you couldn't use the netgear driver instead which would potentially give draft 'n' connectivity too.

---

### Post by praseodym on 2011-10-27
> **Steve54 said:**
> I am also new to this so don't shout if I'm wrong :P.
 
As you are using the ndis wrapper is there any reason why you couldn't use the netgear driver instead which would potentially give draft 'n' connectivity too.

Its possible, that it works. Still the Netgear stick uses a Broadcom chipset, I dont think they are quite different.

---

### Post by mohali26 on 2011-10-28
i can't get it to work!! here what it's says to me

root@skule11:/home/mohammad# sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndisgtk is already the newest version.
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 131 not upgraded.

root@skule11:/home/mohammad# wget [http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz)
--2011-10-28 08:28:53--  [http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz)
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-10-28 08:28:53 ERROR 404: Not Found.

root@skule11:/home/mohammad# tar xvf Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz
tar: Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

what should i do now!!!!

---

### Post by praseodym on 2011-10-28
Driver attached. Save it in /home and continue with the "tar"-command

---

### Post by mohali26 on 2011-10-28
i have every doen as you want, after that i connected my wdna3100v2 but it still not seeing it what should i do after that.

here is what all the info:

mohammad@skule11:~$ ndiswrapper -l
bcmn43xx64 : driver installed
mohammad@skule11:~$ sudo modprobe -v ndiswrapper
[sudo] password for mohammad: 
insmod /lib/modules/3.0.0-12-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko 
mohammad@skule11:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modules.conf
mohammad@skule11:~$ lsmod
Module                  Size  Used by
ndiswrapper           254773  0 
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
option                 25477  2 
usb_wwan               20491  1 option
usbserial              47107  7 option,usb_wwan
ipt_MASQUERADE         12759  1 
xt_state               12578  1 
ipt_REJECT             12576  2 
xt_tcpudp              12603  4 
iptable_filter         12810  1 
nf_nat_h323            17002  0 
nf_conntrack_h323      62913  1 nf_nat_h323
nf_nat_pptp            12629  0 
nf_conntrack_pptp      13830  1 nf_nat_pptp
nf_conntrack_proto_gre    13656  1 nf_conntrack_pptp
nf_nat_proto_gre       12767  1 nf_nat_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             17086  0 
nf_conntrack_sip       29730  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12704  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
iptable_nat            13229  1 
nf_nat                 25890  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  4 iptable_nat,nf_nat
nf_conntrack           82342  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
radeon               1015995  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29991  2 snd_pcm,snd_seq
ath9k                 127538  0 
mac80211              310872  1 ath9k
ttm                    76805  1 radeon
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 radeon
ath9k_common           13839  1 ath9k
drm                   236330  5 radeon,ttm,drm_kms_helper
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
ath9k_hw              312866  2 ath9k,ath9k_common
psmouse                73882  0 
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
i2c_algo_bit           13423  1 radeon
mei                    41480  0 
mxm_wmi                12979  0 
wmi                    19256  2 acer_wmi,mxm_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  5 
uas                    18027  0 
tg3                   147729  0 
ahci                   26002  0 
libahci                26861  1 ahci

---

### Post by mohali26 on 2011-10-28
mohammad@skule11:~$ dmesg | grep ndis
[ 1133.118791] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1133.171830] usbcore: registered new interface driver ndiswrapper
mohammad@skule11:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 002 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 002 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n [Broadcom BCM4323]
Bus 002 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

---

### Post by mohali26 on 2011-10-28
mohammad@skule11:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mohammad" 
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 2A:E2:31:D0:DB:C5  
          Tx-Power=13 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
mon0      IEEE 802.11bgn  Mode:Monitor  Tx-Power=13 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
         
ppp0      no wireless extensions.

mohammad@skule11:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:FF:F6:FA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm 
                    Encryption key:on
                    ESSID:"ciscoF6FA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005e528a11c3
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0009636973636F46364641
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0406000100000000
                    IE: Unknown: 050400010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101
          Cell 02 - Address: 58:6D:8F:51:28:CF
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm 
                    Encryption key:on
                    ESSID:"PandaBrun"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009eb82d8a40
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 000950616E64614272756E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD270050F204104A0001101044000102104700103DFFF827AC52DAF012A28EAD756E06EC103C000103
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 2A:E2:31:D0:DB:C5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm 
                    Encryption key:on
                    ESSID:"mohammad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000001f546f1b
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00086D6F68616D6D6164
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 0706474249010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F

mon0      Interface doesn't support scanning : Operation not supported

ppp0      Interface doesn't support scanning.

mohammad@skule11:~$ cat /etc/modprobe.d/ndiswrapper.conf
cat: /etc/modprobe.d/ndiswrapper.conf: No such file or directory

i can't see any network, what i did wrong?????

---

### Post by praseodym on 2011-10-28
You created an "Ad-Hoc"-network, which means Internet-Connection-Sharing. Remove (not edit!) your current wireless profile and create a new one in "Infrastructure" modus.

---

### Post by mohali26 on 2011-10-28
i still can't  see the any network with this adapter.

as you see  have two adapters one the came with my computer and the another one is wdna3100v2 the one is build is out of the range so that's way i want to use netgear adapter.

and then i want to check my internet so i want to use airodump-ng
and the other command, so will this make my adapter make my usb able to get inject and package and will be seen in airmon-ng and airodump-ng????????????????

---

### Post by haqking on 2011-10-28
> **mohali26 said:**
> i still can't  see the any network with this adapter.

as you see  have two adapters one the came with my computer and the another one is wdna3100v2 the one is build is out of the range so that's way i want to use netgear adapter.

and then i want to check my internet so i want to use airodump-ng
and the other command, so will this make my adapter make my usb able to get inject and package and will be seen in airmon-ng and airodump-ng????????????????

If this relates to aircrack and the use of/or backtrack then i would suggest using the BT forums or Aircrack wiki.

Good luck

---

### Post by Elfy on 2011-10-28
Closed = please see - [http://ubuntuforums.org/showthread.php?t=1869252#post11391962](http://ubuntuforums.org/showthread.php?t=1869252#post11391962)

---

