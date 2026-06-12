---
title: "Wireless on Ubuntu 11.10 - by using TL-WN722N"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by lee_can on 2011-12-15
Hi,

I had problem before with the wireless on my ubuntu 11.10.
So i bought wireless USB TP-Link TL-WN722N, install ath9k_htc-installer and run it.
If i move the mouse over network icon on top right side, i can see 
Wireless network (atheros USB2.0 WLAN)
and
Wireless network (atheros AR9285 wireless network adaptor).
But both of them are disable.

I just follow [http://blog.y3xz.com/post/11811814837/installing-tl-wn722n-on-ubuntu-11-10](http://blog.y3xz.com/post/11811814837/installing-tl-wn722n-on-ubuntu-11-10)
but i got error when i run sudo make, please see below output
```
e33@e33-G560:~/Downloads/compat-wireless-2.6.38.2-2$ sudo make
[: 1: -gt: argument expected
test: 1: -ge: unexpected operator
make -C /lib/modules/3.0.0-14-generic/build M=/home/e33/Downloads/compat-wireless-2.6.38.2-2 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-14-generic'
  CC [M]  /home/e33/Downloads/compat-wireless-2.6.38.2-2/net/wireless/util.o
/home/e33/Downloads/compat-wireless-2.6.38.2-2/net/wireless/util.c: In function ‘cfg80211_change_iface’:
/home/e33/Downloads/compat-wireless-2.6.38.2-2/net/wireless/util.c:788:2: error: implicit declaration of function ‘br_port_exists’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors

make[3]: *** [/home/e33/Downloads/compat-wireless-2.6.38.2-2/net/wireless/util.o] Error 1
make[2]: *** [/home/e33/Downloads/compat-wireless-2.6.38.2-2/net/wireless] Error 2
make[1]: *** [_module_/home/e33/Downloads/compat-wireless-2.6.38.2-2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-14-generic'
make: *** [modules] Error 2
e33@e33-G560:~/Downloads/compat-wireless-2.6.38.2-2$ 

```
Can anyone advise please?
Regards

---

### Post by lee_can on 2011-12-18
any advise guys?

---

### Post by praseodym on 2011-12-18
Did you install the needed tools?

```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
After that try the latest driver:

```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```
You should also install the latest firmware:
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz
sudo tar xvf ath_htc_firmware-1-1.tar.gz -C /lib/firmware 
```
Reboot after that

---

### Post by lee_can on 2011-12-19
> **praseodym said:**
> Did you install the needed tools?

```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
After that try the latest driver:

```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```
You should also install the latest firmware:
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz
sudo tar xvf ath_htc_firmware-1-1.tar.gz -C /lib/firmware 
```
Reboot after that

I did everything mentioned above and still not working, i hope someone will help me to sort this out.

i use this version of compat wireless
```
compat-wireless-3.2-rc1-1

```
i use also this
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz
```

Can anyone give me an advise how to solve this issue?

Best regards

---

### Post by praseodym on 2011-12-19
> sudo tar xvf ath_htc_firmware-1-1.tar.gz -C /lib/firmware
Did you unpack the firmware as described? Rebooted?

---

### Post by cornelis spronk on 2011-12-19
Buy a TL-WN727N on Ebay and sell your TL-WN722N.  They have about the same value.  You might solve your problem for the cost of postage.

A TL-WN727N works just fine with Ubuntu.

---

### Post by lee_can on 2011-12-21
> **praseodym said:**
> Did you unpack the firmware as described? Rebooted?

Let me show you please what steps i did:
- From [http://www.orbit-lab.org/kernel](http://www.orbit-lab.org/kernel), i have download compat-wireless-3.2-rc1-1.
- extract compat-wireless-3.2-rc1-1.
- cd compat-wireless-3.2-rc1-1
- sudo ./scripts/driver-select atheros 
- sudo make
- sudo make install

- sudo make unload 
- sudo make wlunload
- sudo make btunload
- sudo modprobe ath9k_htc

- wget [http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz)
- sudo tar xvf ath_htc_firmware-1-1.tar.gz -C /lib/firmware

-reboot
But unfortunately the wireless on right top still disable.

thanks in advance.
regards

---

### Post by praseodym on 2011-12-21
Checks, please:

```
iwconfig
dmesg | grep ath
lsmod
sudo iwlist scan
iwlist chan
rfkill list
```

---

### Post by lee_can on 2011-12-21
> **praseodym said:**
> Checks, please:

```
iwconfig
dmesg | grep ath
lsmod
sudo iwlist scan
iwlist chan
rfkill list
```
```
e33@e33-G560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
e33@e33-G560:~$ 


```
```
e33@e33-G560:~$ dmesg | grep ath
[   17.902793] ath9k 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.902805] ath9k 0000:05:00.0: setting latency timer to 64
[   17.954096] ath: EEPROM regdomain: 0x6a
[   17.954098] ath: EEPROM indicates we should expect a direct regpair map
[   17.954101] ath: Country alpha2 being used: 00
[   17.954102] ath: Regpair used: 0x6a
[   17.958667] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.959345] Registered led device: ath9k-phy0
[   18.524975] type=1400 audit(1324516344.243:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1024 comm="apparmor_parser"
[ 5791.578419] usb 2-1.1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 5791.813154] ath9k_htc 2-1.1:1.0: ath9k_htc: HTC initialized with 33 credits
[ 5792.011340] ath9k_htc 2-1.1:1.0: ath9k_htc: FW Version: 1.3
[ 5792.011347] ath: EEPROM regdomain: 0x809c
[ 5792.011350] ath: EEPROM indicates we should expect a country code
[ 5792.011354] ath: doing EEPROM country->regdmn map search
[ 5792.011358] ath: country maps to regdmn code: 0x52
[ 5792.011365] ath: Country alpha2 being used: CN
[ 5792.011369] ath: Regpair used: 0x52
[ 5792.016878] Registered led device: ath9k_htc-phy1
[ 5792.016887] usb 2-1.1: ath9k_htc: USB layer initialized
[ 5792.016931] usbcore: registered new interface driver ath9k_htc
e33@e33-G560:~$ 


```
```
e33@e33-G560:~$ lsmod
Module                  Size  Used by
ath9k_htc              91167  0 
bnep                   18294  2 
rfcomm                 47004  4 
bluetooth             159177  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  1 
vboxdrv               282739  4 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  4 
ath9k                 121335  0 
mac80211              448163  2 ath9k_htc,ath9k
ath9k_common           13839  2 ath9k_htc,ath9k
joydev                 17693  0 
ath9k_hw              304840  3 ath9k_htc,ath9k,ath9k_common
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
ath                    23780  3 ath9k_htc,ath9k,ath9k_hw
cfg80211              198044  4 ath9k_htc,ath9k,mac80211,ath
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
snd_hda_intel          33390  4 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
xt_limit               12711  12 
xt_tcpudp              12603  18 
snd_seq_midi           13324  0 
xt_addrtype            12713  4 
snd_rawmidi            30547  1 snd_seq_midi
xt_state               12578  14 
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ip6table_filter        12815  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25890  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           82342  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
intel_ips              18089  0 
iptable_filter         12810  1 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              27473  1 iptable_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
i915                  566827  7 
wmi                    19256  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
ahci                   26002  2 
libahci                26861  1 ahci
e33@e33-G560:~$ 


```
```
e33@e33-G560:~$ sudo iwlist scan
[sudo] password for e33: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

wlan1     Interface doesn't support scanning : Network is down

e33@e33-G560:~$ 
 

```
```
e33@e33-G560:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
wlan1     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
e33@e33-G560:~$ 


```
```
e33@e33-G560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
3: phy1: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
e33@e33-G560:~$ 


```

---

### Post by praseodym on 2011-12-21
Try

```
sudo rfkill unblock all
```
Check:
```
rfkill list
iwconfig
```
"Hard blocked: yes" and "Tx-Power = off" mean there is a button, switch, etc. Check the BIOS settings and/or reset it.

What kind of computer is that?

---

### Post by lee_can on 2011-12-21
```
e33@e33-G560:~$ sudo rfkill unblock all
e33@e33-G560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
e33@e33-G560:~$ 
```

```
e33@e33-G560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
e33@e33-G560:~$ 

```
From the icon on top - right side, it shows the following:
Wireless network (Atheros USB2.0 WLAN)
Wireless is disables by hardware switch

Wireless network (Atheros AR9285 Wireless network adaptor PCI-express)
Wireless is disables by hardware switch

My laptop is Lenovo G560.

Thank you for all your replies.

---

### Post by praseodym on 2011-12-21
Try:

```
sudo modprobe -rfv ath9k ath9k_htc
sudo rfkill unblock all
sudo modprobe -v ath9k ath9k_htc
```
and replug the stick.

---

### Post by lee_can on 2011-12-22
> **praseodym said:**
> Try:

```
sudo modprobe -rfv ath9k ath9k_htc
sudo rfkill unblock all
sudo modprobe -v ath9k ath9k_htc
```
and replug the stick.

Ohhhhhhhhhhhhhhhh My God,
Finally it works, Really I don't know how to thank you...

You are so kind to assist me till the end.
I really appreciate your help, may god bless you.

Best Regards

---

### Post by praseodym on 2011-12-22
Great :popcorn:

Do you want to use both devices in parallel? If not you can setup an UDEV-rule which unloads the driver of the internal card when the stick is plugged in. On a laptop it can help saving battery...

---

### Post by lee_can on 2011-12-22
> **praseodym said:**
> Great :popcorn:

Do you want to use both devices in parallel? If not you can setup an UDEV-rule which unloads the driver of the internal card when the stick is plugged in. On a laptop it can help saving battery...

I don't know what is preferable?
Is better to setup an UDEV-rule?

---

### Post by praseodym on 2011-12-22
Maybe both devices want to connect in parallel. You can check, which one works better:

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

Replace in the file **10-wlan-stick.rules** _twice_ **b43** with **ath9k**

If it makes no difference, you can easily remove the file via:

```
sudo rm /etc/udev/rules.d/10-wlan-stick.rules
```

---

### Post by lee_can on 2011-12-22
> **praseodym said:**
> Maybe both devices want to connect in parallel. You can check, which one works better:

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

Replace in the file **10-wlan-stick.rules** _twice_ **b43** with **ath9k**

If it makes no difference, you can easily remove the file via:

```
sudo rm /etc/udev/rules.d/10-wlan-stick.rules
```

I will try, thanks a lot again and again :)

---

### Post by capfuturo on 2012-03-25
Hello There,

I am installing drivers for TP Link TL-WN821N v2 for Ubuntu 11.10 running on Parallels desktop on iMac Os X Lion.

I can't download latest firmware Atheros according to instructions on this and a few other post. The file seems be not available for download through the terminal from Ubuntu website. Any help on this matter would be most appreciated. Below is the message I get on Gnome-Terminal:

************************************************************************************
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz)
--2012-03-25 16:40:59--  [http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz)
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-03-25 16:41:00 ERROR 404: Not Found.
***********************************************************************************

Thanks,

Capitan Futuro

---

### Post by praseodym on 2012-03-25
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/44/10/2640681-15888a2-Atheros_Firmware.tar.gz
sudo tar xvf 2640681-15888a2-Atheros_Firmware.tar.gz -C /lib/firmware 
```This should work.
Due to a software upgrade the links changed.

---

### Post by capfuturo on 2012-03-25
Thank you Praseodym! It worked and I installed them already. However I am having difficulties trying to activate the USB stick in order for it to be seen by Ubuntu. Ubuntu seems not to recognise it. This is what I have done so far and the results:

I have run the following:
sudo rfkill unblock all
rfkill list
iwconfig
sudo modprobe -rfv ath9k ath9k_htc
sudo rfkill unblock all
sudo modprobe -v ath9k ath9k_htc

In the last sudo mod probe the terminal says:

FATAL: Error inserting ath9k (/lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Extract below. Thanks in advance,

Cap Futuro


**********************************************************************************************
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ dmesg | grep ath
[  334.881381] ath9k: Unknown parameter `ath9k_htc'
[  570.978427] usbcore: registered new interface driver ath9k_htc
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo dmesg | grep ath
[  334.881381] ath9k: Unknown parameter `ath9k_htc'
[  570.978427] usbcore: registered new interface driver ath9k_htc
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ lsmod
Module                  Size  Used by
ath9k_htc              91273  0 
ath9k_common           14053  1 ath9k_htc
ath9k_hw              390898  2 ath9k_htc,ath9k_common
nls_utf8               12557  1 
isofs                  40253  1 
prl_pv                 55891  0 
prl_fs_freeze          13061  0 
prl_eth                13272  0 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
carl9170               81754  0 
mac80211              519885  2 ath9k_htc,carl9170
ath                    23827  4 ath9k_htc,ath9k_common,ath9k_hw,carl9170
cfg80211              209982  4 ath9k_htc,carl9170,mac80211,ath
compat                 14228  6 ath9k_htc,ath9k_common,ath9k_hw,carl9170,mac80211,cfg80211
snd_intel8x0           38401  2 
snd_ac97_codec        134826  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96714  2 snd_intel8x0,snd_ac97_codec
uvcvideo               72711  0 
snd_seq_midi           13324  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
binfmt_misc            17540  1 
prl_fs                 27707  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
virtio_balloon         13108  0 
psmouse                73882  0 
serio_raw              13166  0 
snd                    68266  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
prl_tg                 17850  1 prl_fs
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_intel8x0,snd_pcm
shpchp                 37345  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
floppy                 70365  0 
ahci                   26002  3 
libahci                26861  1 ahci
virtio_pci             17630  0 
virtio_ring            14776  2 virtio_balloon,virtio_pci
virtio                 14141  2 virtio_balloon,virtio_pci
e1000                 108573  0 
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ rfkill list
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo rfkill unblock all
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ rfkill list
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo modprobe -rfv ath9k ath9k_htc
rmmod /lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
rmmod /lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo rfkill unblock all
capfuturo@capfuturo-Parallels-Virtual-Platform:~/compat-wireless-2012-03-18$ sudo modprobe -v ath9k ath9k_htc
insmod /lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko ath9k_htc
FATAL: Error inserting ath9k (/lib/modules/3.0.0-16-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
*********************************************************************************************

---

### Post by Mastr Splyntr on 2012-10-20
[praseodym]("http://ubuntuforums.org/member.php?u=1411497") Please can you like repost what to do in an ORDERLY manner. I have a TP-LINK TL-WN722N and Ubuntu 12.04
I tried everything posted in this thread to no avail. 
"iwconfig" still says no wireless extensions without any mention of wlan0 :(Please... it would be so nice of you !

---

### Post by danbo1221 on 2013-01-01
lee_can those actions worked for me, and I downloaded the latest version of compat-wireless (3.6.8-1) and the 1.3 firmware.

---

