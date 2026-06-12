---
title: "Ubuntu 12.04 Slow Wireless"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by vDub2000 on 2012-04-26
I've been having some issues with my wireless network adapter. I've noticed that my download speeds are incredibly slow compared to what I'm used to seeing in Windows. 

I've done some Google searches to try to determine and fix the problem, but nothing has worked thus far. I've ignored IPv6 with no change, and my adapter is currently using the RTL8192CU driver. I've had this issue in previous versions of Ubuntu as well.

Help?

---

### Post by robgraves on 2012-04-26
If you're downloading via Ubuntu Software Center, apt, synaptic, etc. it is probably due to the fact that today is new release date, so everyone is downloading software, doing updates, etc.  The servers are probably overloaded...

---

### Post by vDub2000 on 2012-04-26
This issue has been going on for the past few days, not just today.

---

### Post by cromat on 2012-04-26
For the past few weeks I have had horribly slow speeds connecting to the software center as well. My connection is fine to my router, I think the servers have been bogged down for weeks now and especially today.

I also saw somewhere else they suggested making sure that the main source of packages is in the closest location to you it may have chosen the west coast or something when you will benefit from the east coast being in MI.

---

### Post by wildmanne39 on 2012-04-26
Hi, most people have not gotten that driver to work at all I believe, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by vDub2000 on 2012-04-26
cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169

```

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 004 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 002: ID 03f0:3b11 Hewlett-Packard PSC 1300 series
Bus 004 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 004 Device 004: ID 0e6f:0301 Logic3 
Bus 004 Device 005: ID 0461:4d0f Primax Electronics, Ltd 
```

iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"(Removed from view)"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:3F:2B:04   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10208   Missed beacon:0

eth0      no wireless extensions.

```

rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod
```
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
vesafb                 13844  1 
nvidia              12319264  30 
usblp                  18307  0 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
rtl8192cu             103297  0 
snd_hda_intel          33773  3 
rtl8192c_common        75767  1 rtl8192cu
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
rtlwifi               111202  1 rtl8192cu
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
mac80211              506816  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
cfg80211              205544  2 rtlwifi,mac80211
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
usbhid                 47199  0 
xpad                   18179  0 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    99559  1 usbhid
ff_memless             13097  1 xpad
sp5100_tco             13791  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
i2c_piix4              13301  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
mac_hid                13253  0 
k10temp                13166  0 
ppdev                  17113  0 
wmi                    19256  0 
parport_pc             32866  1 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            49198  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13204  0 
r8169                  62099  0  
```

nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [(Removed from view)] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        00:23:13:00:6F:C4

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *(Removed from view):        Infra, 00:12:17:3F:2B:04, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2

  IPv4 Settings:
    Address:         192.168.2.90
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             208.67.220.220
    DNS:             208.67.222.222


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:1D:8B:15:8A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
 
```

---

### Post by wildmanne39 on 2012-04-26
Hi, please try:
```
sudo modprobe -r rtl8192cu

sudo modprobe rtl8192cu swenc=1
```
do not reboot, if it works we will need to make it permanent.
Thanks

---

### Post by vDub2000 on 2012-04-26
> **wildmanne39 said:**
> Hi, please try:
```
sudo modprobe -r rtl8192cu

sudo modprobe rtl8192cu swenc=1
```
do not reboot, if it works we will need to make it permanent.
Thanks

Didn't work for me. Downloads are still as slow as ever.

---

### Post by wildmanne39 on 2012-04-26
Hi, leave that setting in and set your wireless setting to match the sreenshots.

Also some people have had to change the speed of there connection in the router to just g speed I believe.
Thanks

---

### Post by skompier on 2012-04-26
Try this...

[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/]("http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/")

---

### Post by vDub2000 on 2012-04-26
> **skompier said:**
> Try this...

[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/]("http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/")

Thanks, but I've already tried those solutions and none worked.

---

### Post by vDub2000 on 2012-04-26
> **wildmanne39 said:**
> Hi, leave that setting in and set your wireless setting to match the sreenshots.

Also some people have had to change the speed of there connection in the router to just g speed I believe.
Thanks

Still no difference. :(

It's a bummer, because I'd like to finally ditch Windows and use Ubuntu (especially when the Linux version of Steam comes out) but I don't wanna have to go back to a wired connection.

---

### Post by comet on 2012-04-29
I'm having a similar issue with my Broadcom BCM4322 wifi adapter. I'm using an HP dv4 laptop with this particular wireless chipset, and I'm getting speeds at about .25Mbit/sec. It is ridiculously slow and I'm not quite sure what can be done to resolve it. Oddly enough, I've used different versions of Ubuntu, Windows and even FreeBSD on this laptop without these types of wireless issues.

---

### Post by mickey946 on 2012-04-29
> **wildmanne39 said:**
> Hi, please try:
```
sudo modprobe -r rtl8192cu

sudo modprobe rtl8192cu swenc=1
```
do not reboot, if it works we will need to make it permanent.
Thanks

I have the same problem, but the wireless connection is slow on other sites too (checked on speedtest.net and got only 0.9 MB/s when I usually get 3.5 MB/s in Windows and in 11.10)

I run those two commands you suggested and the connection suddenly got great! 
How do I keep it permanent?

---

### Post by wildmanne39 on 2012-04-29
Hi comet, have you changed your settings to match the screenshots in post 9? if so please start your own thread and post a link to it here because it gets confusing working on more then one persons issue while the OP's issue has not been resolved.
Thanks

---

### Post by KYSL on 2012-05-02
open terminal and type:
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1

if it works make it permanent by:
opening/creating /etc/modprobe.d/options.conf and adding the following line
options iwlwifi 11n_disable=1

it resolved my issue. In my case in 11.10 the iwlwifi was defined as wilagn.

it sucks as this issue was known in the previous release and did not get resolved out of the box. Shame on you Ubuntu. Anyway, hope it helps.

---

### Post by vDub2000 on 2012-05-02
> **KYSL said:**
> open terminal and type:
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1

if it works make it permanent by:
opening/creating /etc/modprobe.d/options.conf and adding the following line
options iwlwifi 11n_disable=1

it resolved my issue. In my case in 11.10 the iwlwifi was defined as wilagn.

it sucks as this issue was known in the previous release and did not get resolved out of the box. Shame on you Ubuntu. Anyway, hope it helps.

Tried it... says ERROR: Module iwlwifi does not exist in /proc/modules

---

### Post by KYSL on 2012-05-02
> **vDub2000 said:**
> Tried it... says ERROR: Module iwlwifi does not exist in /proc/modules

please check the driver name from the "connection information" menu and match it to the above command.

---

### Post by vDub2000 on 2012-05-02
> **KYSL said:**
> please check the driver name from the "connection information" menu and match it to the above command.

I ended up doing that too, except I got some sort of fatal error as I did so.

---

### Post by TheNessus on 2012-05-02
in 11.10 I had really slow internet connection when using wifi, but only at my home. I have broadcom 4431. 


It's ONLY broadcom that does these issues. Anyway, the conclusion is that my adapter is in conflict with my wireless router, as it does not do this slow connection bug when I am at campus or a cafe, for instance. 

For a good connection I had to re-connect to the wireless network, but then it slowed down again after a while.

The issue is resolved for me in 12.04. Don't ask me why. But I still have a very slow download when using torrents when it is working fast if I do it on Windows.

---

### Post by TheNessus on 2012-05-02
> **KYSL said:**
> open terminal and type:
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1

if it works make it permanent by:
opening/creating /etc/modprobe.d/options.conf and adding the following line
options iwlwifi 11n_disable=1

it resolved my issue. In my case in 11.10 the iwlwifi was defined as wilagn.

it sucks as this issue was known in the previous release and did not get resolved out of the box. Shame on you Ubuntu. Anyway, hope it helps.


I did this now (with "rmmod brcmsmac" instead")
it resulted in no wifi anymore, and I cannot load Ubuntu anymore, it stalls in the purple Ubuntu screen. Ubuntu only loads if I disable wifi in the BIOS.

damn.

how do I undo this?

---

### Post by chamber on 2012-05-02
@ OP

I use that usb device as well.

Did it detect it automatically for you or did you have to install drivers?

I found that when it detected the device automatically for me it was very slow, I used the drivers from here which helped.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772)

There is an install shell script included in the zip folder.

---

### Post by KYSL on 2012-05-02
> **TheNessus said:**
> I did this now (with "rmmod brcmsmac" instead")
it resulted in no wifi anymore, and I cannot load Ubuntu anymore, it stalls in the purple Ubuntu screen. Ubuntu only loads if I disable wifi in the BIOS.

damn.

how do I undo this?

Sorry for the driver conflict that resulted. I am not an expert in these wifi driver but googling the issue i found this post that may help.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875892](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875892)

---

### Post by TheNessus on 2012-05-03
> **KYSL said:**
> Sorry for the driver conflict that resulted. I am not an expert in these wifi driver but googling the issue i found this post that may help.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875892](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875892)

It's ok, I solved it. my adapter got blacklisted and I removed it from the list.

thanks though!

---

### Post by vDub2000 on 2012-05-09
> **chamber said:**
> @ OP

I use that usb device as well.

Did it detect it automatically for you or did you have to install drivers?

I found that when it detected the device automatically for me it was very slow, I used the drivers from here which helped.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772)

There is an install shell script included in the zip folder.

they were automatically detected and installed.

How do I go about installing the drivers from that website?

---

### Post by chamber on 2012-05-09
Download the linux drivers from the website I linked to.

Extract the drivers and then open a terminal and cd to the extracted folder.

Once in the extracted folder run 

```
bash install.sh
```

This will compile the drivers for you.

You will be prompted for your root password while it is working.

---

### Post by garrychnca on 2012-07-02
> **wildmanne39 said:**
> Hi, most people have not gotten that driver to work at all I believe, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
```here by clicking on new reply and click # and paste the information between the brackets.
Thank you

```
cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux GarryHP 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

```
lspci -nnk | grep -iA2 net

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:146a]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi
```

```
lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 004: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 002 Device 004: ID 10f1:1a28 Importek
```

```
iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"(hide from view)"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 68:7F:74:2C:08:46   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1304  Invalid misc:122   Missed beacon:0

eth0      no wireless extensions.
```

```
rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
lsmod

Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
joydev                 17693  0 
uvcvideo               72627  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
psmouse                87603  0 
videodev               98259  1 uvcvideo
snd_hwdep              13668  1 snd_hda_codec
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_seq_midi           13324  0 
wmi                    19256  1 hp_wmi
snd_rawmidi            30748  1 snd_seq_midi
iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
mac_hid                13253  0 
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              205544  2 iwlwifi,mac80211
intel_ips              18089  0 
snd_timer              29990  2 snd_pcm,snd_seq
i915                  468651  3 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
mei                    41616  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
soundcore              15091  1 snd
lp                     17799  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0
```

```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [(hide from view)] --------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:26:C7:8C:1A:E8

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    
    *(hide from view): Infra, 68:7F:74:2C:08:46, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WEP
    

  IPv4 Settings:
    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             64.71.255.198

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        (hide from view)

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

Thanks!

---

### Post by wildmanne39 on 2012-07-02
Hi, please copy and paste the commands one line at a time:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```
Thanks

---

### Post by garrychnca on 2012-07-03
THANKS!

it works!! this problem bothered me for quite a long time!

In addition, why removing iwlwifi module would make it work?

Thank you again!

---

### Post by wildmanne39 on 2012-07-03
Hi, your welcome! you removed the module but loaded it again with a parameter that turned off N speed because N speed does not work well in linux with intel drivers.
Thanks

---

### Post by anipet on 2012-07-08
Thanks Wildmanne39, I think you might have solved the problem for me too.. I tried that method to disable n configuration and so far so good, wifi is much more responsive. :)

---

### Post by Hanine on 2012-07-14
> **vDub2000 said:**
> Tried it... says ERROR: Module iwlwifi does not exist in /proc/modules

This works perfectly for me.
I am running Ubuntu 12.04 on Dell XPS 15 L502X with Intel Centrino Wireless (driver is iwlwifi and wifi security is WEP).

[http://askubuntu.com/questions/81156/wireless-with-wep-extremely-slow-on-an-acer-timeline-4810t-with-a-centrino-wirel?rq=1](http://askubuntu.com/questions/81156/wireless-with-wep-extremely-slow-on-an-acer-timeline-4810t-with-a-centrino-wirel?rq=1)

---

### Post by leoxis on 2013-04-08
I am having the same problem and couldnt solve it...

Please, help me to fix it! :)


my computer datas:

leo@leo-note:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux leo-note 3.2.0-39-generic-pae #62-Ubuntu SMP Wed Feb 27 22:25:11 UTC 2013 i686 i686 i386 GNU/Linux


leo@leo-note:~$ lspci -nnk | grep -iA2 net
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e044]
    Kernel driver in use: ath9k
--
09:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  07)
    Subsystem: Sony Corporation Device [104d:90ab]
    Kernel driver in use: r8169

leo@leo-note:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 04f2:b32f Chicony Electronics Co., Ltd 
leo@leo-note:~$ 

leo@leo-note:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"apartamento33"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:D2:4D:B9:A0   
          Bit Rate=39 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:209  Invalid misc:1   Missed beacon:0

eth0      no wireless extensions.


leo@leo-note:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: sony-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
leo@leo-note:~$ 

leo@leo-note:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13516  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
ath3k                  12825  0 
btusb                  17948  0 
bluetooth             158479  12 rfcomm,bnep,ath3k,btusb
psmouse                86520  0 
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_hda_intel          32719  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sony_laptop            39681  0 
ath9k                 117356  0 
mac80211              436493  1 ath9k
fglrx                2909978  155 
snd_timer              28931  2 snd_seq,snd_pcm
snd                     62218  20  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
video                  19115  0 
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178877  3 ath9k,mac80211,ath
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
rts_pstor             353252  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 
leo@leo-note:~$ 


leo@leo-note:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        30:F9:ED:DC:63:13

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [apartamento33] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        84:4B:F5:DC:BB:A5

  Capabilities:
    Speed:           52 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    minero_m:        Infra, E8:6D:52:B2:21:D4, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Cris:            Infra, 64:87:D7:F5:E1:E6, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Lazar2:          Infra, F8:D1:11:33:95:AE, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    DN4-NET:         Infra, F4:EC:38:AE:CD:1C, Freq 2427 MHz, Rate 54 Mb/s, Strength 24 WPA2
    netvirtuaapt24:  Infra, E8:6D:52:94:6E:1C, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    Cristal House:   Infra, 98:FC:11:C1:9E:3E, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Didi:            Infra, 94:0C:6D:AE:92:9A, Freq 2427 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    TW 41:           Infra, 1C:7E:E5:FF:BE:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Apto1202:        Infra, 00:1D:0F:F5:85:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WEP
    Almir:           Infra, 00:23:CD:D7:6F:BC, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WEP
    NET-VIRTUA-WIFI: Infra, C4:0A:CB:69:68:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    *apartamento33:  Infra, 00:1D:D2:4D:B9:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA2
    Privado:         Infra, 00:1C:DF:98:DB:54, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Cacau:           Infra, 98:FC:11:CE:BB:DA, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Embratel-Wi-Fi:  Infra, B8:BE:BF:3B:91:A1, Freq 2412 MHz, Rate 54 Mb/s, Strength 22

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             201.6.2.85
    DNS:             201.6.2.175


> **Wild Man said:**
> Hi, most people have not gotten that driver to work at all I believe, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by pinballwizard on 2013-04-08
Dunno if it's relevant, but I'm using a RT3090 network card, and ever since I used it, I had very slow speed if using the laptop on battery power. Last month or two, it's ben fine though, I assume an update fixed that?

---

### Post by wildmanne39 on 2013-04-08
Hi, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Change your wireless settings in network manager to match the screenshots.
Thanks

---

### Post by leoxis on 2013-04-08
I did this and the connection got worst :(

Any other  idea?

thankssss


> **Wild Man said:**
> Hi, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Change your wireless settings in network manager to match the screenshots.
Thanks

---

### Post by wildmanne39 on 2013-04-08
Hi, it does not help that there are so many networks next to yours, please set your channel to 1 or 11.

Post the contents of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Please post screenshots of your wireless settings like I did in my previous post so we can make sure they are the same.
Thanks

---

### Post by leoxis on 2013-04-08
when I type the code it appears:
**"options ath9k nohwcrypt=1"**

**I changed the channel to 11...**

I am trying to send the printscreens but the connection really doesnt help.. I cant upload them :(

The wifi connection is istill really bad... I can understand why in windows it is ok...



> **Wild Man said:**
> Hi, it does not help that there are so many networks next to yours, please set your channel to 1 or 11.

Post the contents of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Please post screenshots of your wireless settings like I did in my previous post so we can make sure they are the same.
Thanks

---

### Post by wildmanne39 on 2013-04-08
Hi, you can try what I posted in this thread.
[http://ubuntuforums.org/showthread.php?t=2133296&page=2](http://ubuntuforums.org/showthread.php?t=2133296&page=2) Post 16.
and read the following posts because you will still likely need the other settings as well.
Thanks

---

### Post by leoxis on 2013-04-08
I'll try it but what others settings are u talking about? thanks!!!!!


> **Wild Man said:**
> Hi, you can try what I posted in this thread.
[http://ubuntuforums.org/showthread.php?t=2133296&page=2](http://ubuntuforums.org/showthread.php?t=2133296&page=2) Post 16.
and read the following posts because you will still likely need the other settings as well.
Thanks

---

### Post by wildmanne39 on 2013-04-08
What was posted in post 35 of this thread.

But try the new driver without them first.
Thanks

---

### Post by Bucky Ball on 2013-04-08
*Thread moved to **Networking & Wireless**.*

---

### Post by leoxis on 2013-04-08
I am sorry to ask that, but where I found my kernel version?



> **Wild Man said:**
> What was posted in post 35 of this thread.

But try the new driver without then first.
Thanks

---

### Post by leoxis on 2013-04-08
I found it!
leo@leo-note:~$ uname -a
Linux leo-note 3.2.0-39-generic-pae #62-Ubuntu SMP Wed Feb 27 22:25:11 UTC 2013 i686 i686 i386 GNU/Linux


But in this list ([http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases))  there isnt this version..which one I download?
> **leoxis said:**
> I am sorry to ask that, but where I found my kernel version?

---

### Post by wildmanne39 on 2013-04-08
The first on in that link you posted just like the one in the thread I referred you too,
Thanks

---

### Post by leoxis on 2013-04-08
I couldnt finish it..

I got this message

leo@leo-note:~$ cd Área\ de\ Trabalho/
leo@leo-note:~/Área de Trabalho$ cd compat-wireless-3.6.8-1/
leo@leo-note:~/Área de Trabalho/compat-wireless-3.6.8-1$ sudo su
[sudo] password for leo: 
root@leo-note:/home/leo/Área de Trabalho/compat-wireless-3.6.8-1# ./scripts/driver-select ath9k
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backing up makefile: drivers/net/wireless/ath/Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/bcma/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@leo-note:/home/leo/Área de Trabalho/compat-wireless-3.6.8-1# make
Makefile:61: *** "The path to this compat-wireless directory has spaces in it." "Please put it somewhere where there is no space".  Pare.
root@leo-note:/home/leo/Área de Trabalho/compat-wireless-3.6.8-1# make install
Makefile:61: *** "The path to this compat-wireless directory has spaces in it." "Please put it somewhere where there is no space".  Pare.
root@leo-note:/home/leo/Área de Trabalho/compat-wireless-3.6.8-1# 

"Pare" is stop in portuguese.


> **Wild Man said:**
> The first on in that link you posted just like the one in the thread I referred you too,
Thanks

---

### Post by wildmanne39 on 2013-04-08
This is the space it is referring too.> Área de Trabalho
you can not have spacing in between the words.

You may have to start a post about taking the spaces out.
Thanks

---

### Post by leoxis on 2013-04-09
I extract the package in my home and it worked!!!

now my wifi is working ok!!! It is not as fast as windows but it is so much better!

Thank u so much and I'm sorry to bother u with so many questions...


> **Wild Man said:**
> This is the space it is referring too.
you can not have spacing in between the words.

You may have to start a post about taking the spaces out.
Thanks

---

### Post by wildmanne39 on 2013-04-10
Your welcome!
Enjoy!

---

### Post by Pieman15 on 2013-05-16
Hello - Within the last week, I've started to experience a slow down in my wifi connection, and I was hoping to get some sage advice. Thank you in advance for your assistance. Here's some info that I've seen others post:

```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux Pieman 3.2.0-40-generic-pae #64-Ubuntu SMP Mon Mar 25 21:44:41 UTC 2013 i686 i686 i386 GNU/Linux

```

```
lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
```

```

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
iwconfig 
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"the house"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:38:A1:A9   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:27  Invalid misc:5   Missed beacon:0

eth0      no wireless extensions.
```



 ```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


```
lsmod
Module                  Size  Used by
iwlwifi               366509  0 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
btrfs                 638248  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83544  0 
hfs                    49479  0 
minix                  31453  0 
ntfs                  100206  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230928  0 
ext2                   67987  0 
pci_stub               12550  1 
vesafb                 13516  1 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13175  1 nf_conntrack_ipv6
snd_hda_codec_idt      60251  1 
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
snd_hda_intel          32719  3 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
xt_limit               12541  12 
xt_tcpudp              12531  26 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
xt_addrtype            12596  4 
snd_hwdep              13276  1 snd_hda_codec
xt_state               12514  14 
nvidia              10286823  44 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
r852                   17901  0 
sm_common              16772  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21784  1 nand_bch
psmouse                86520  0 
serio_raw              13027  0 
r592                   17808  0 
snd_rawmidi            25424  1 snd_seq_midi
nand_ecc               13105  1 nand
memstick               15857  1 r592
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13077  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 dell_wmi
video                  19115  0 
binfmt_misc            17292  1 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
arc4                   12473  2 
b43                   342669  0 
mac80211              436493  2 iwlwifi,b43
cfg80211              178877  3 iwlwifi,b43,mac80211
bcma                   25651  1 b43
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b44                    31364  0 
firewire_ohci          40172  0 
sdhci_pci              18324  0 
firewire_core          56940  1 firewire_ohci
sdhci                  28241  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ssb                    50691  2 b43,b44
```
```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:1C:23:97:33:C6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [the house] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:1C:26:97:80:17

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    herbchillin:     Infra, C4:3D:C7:59:00:5C, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2
    donaylor:        Infra, 00:25:9C:EA:B3:E4, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    MONARCH:         Infra, 00:1E:2A:54:3B:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    *the house:      Infra, 00:14:BF:38:A1:A9, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    Team Jacob:      Infra, 94:44:52:07:B6:AF, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ATT8980:         Infra, 20:E5:2A:81:C9:7F, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Raymond Rawls's Network: Infra, 00:25:4B:02:DE:25, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    d10b46:          Infra, 4C:72:B9:D1:0B:46, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    GetOffMahPoach:  Infra, 98:FC:11:7F:6D:F2, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NETGEAR02:       Infra, 4C:60:DE:3A:C9:6A, Freq 2442 MHz, Rate 54 Mb/s, Strength 32 WPA2

  IPv4 Settings:

```

---

### Post by wildmanne39 on 2013-05-16
Please do:
```
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot, let us know if that helps.

Your signal and link quality are low so that causes issues, hopefully once you remove the second driver it will help that issue as well.

I am not on much right now because I am ill, but I will check on your progress as soon as I can.
Thanks

---

### Post by Pieman15 on 2013-05-18
Thanks Wild Man. That seemed to help. I can at least listen to Pandora now. I've noticed other applications are getting a little sluggish of late, and this laptop is going on 7 or 8 years old, so it may just be time for a new one :).

Get Well

---

### Post by Pieman15 on 2013-05-19
I'm starting to think my issues are more related to something like Flash Player or Java. Most of the slowness I'm experiencing occurs when streaming music or trying to watch videos (mostly on youtube or embedded youtube videos). I've also noticed a delay on gmail when typing emails. When I type, there is a delay between when I press the button on the keboard, and when the type is posted to the screen; the delay is sometimes several seconds long. I'll look into this, but any ideas are appreciated.

---

### Post by blumagic66 on 2013-11-06
I have recently upgraded my cable package to 50MB down/25MB up. I had to receive a new wireless router from my cable provider. My speeds on my Windows machines were instantly upgraded. My Ubuntu 12.04 were lacking. I have spent the past several days researching and trying every fix listed in this forum and elsewhere online, with no improvement. Finally I changed my channel on my router from automatic to channel 1 and now I am getting windows comparable speeds. I hope that this helps someone else with the same problem.

thanks,

blu.....

---

