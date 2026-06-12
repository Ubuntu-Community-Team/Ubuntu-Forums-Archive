---
title: "Dell WiFi not working in clean 12.04 LTS"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by godleader on 2013-07-11
My Dell Inspiron 3421 came pre-installed with Ubuntu 12.04 LTS.
Everything was working including WiFi and Bluetooth.
Then I made a clean install of Ubuntu 12.04 64bit version.
And to my surprise, WiFi was not working. However Bluetooth was working.


Network properties shows the device as 'UNCLAIMED'. And I can't even enable it using 'eth1 up' command.
I searched through the forums and tried few tricks which were marked as SOLVED, but they didn't work for me.
and it is not work on Windows 7 64 bit too , i tried download from dell website , after installed it have no respone at all it show a question mark in the device manager

Device: Dell Wireless 1704 802.11b/g/n (2.4GHz)
Manufacturer: Atheros AR9485 


This system is of my daily use and really need the WiFi to work. Please help me with solutions.

---

### Post by wildmanne39 on 2013-07-11
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by godleader on 2013-07-11
thanks for reply , please help me out this 

i facing this in win7 64 bit too , got no wifi to use :( :(

---

### Post by godleader on 2013-07-11
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux dunno-Inspiron-3421 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
dunno@dunno-Inspiron-3421:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel modules: wl
09:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)
    Subsystem: Dell Device [1028:0591]
    Kernel driver in use: r8169
dunno@dunno-Inspiron-3421:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1058:1010 Western Digital Technologies, Inc. 
Bus 003 Device 003: ID 046d:c058 Logitech, Inc. M115 Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:812c Suyin Corp. 
dunno@dunno-Inspiron-3421:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

dunno@dunno-Inspiron-3421:~$ rfkill list all
dunno@dunno-Inspiron-3421:~$ lsmod
Module                  Size  Used by
nls_utf8               12558  1 
udf                    94613  1 
crc_itu_t              12708  1 udf
dm_crypt               23126  1 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79756  1 
joydev                 17694  0 
parport_pc             32867  0 
ppdev                  17114  0 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
bnep                   18240  2 
rfcomm                 47562  0 
bluetooth             211812  10 bnep,rfcomm
snd_seq_midi_event     14900  1 snd_seq_midi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
microcode              23030  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               78117  0 
psmouse               102075  0 
serio_raw              13216  0 
mei                    41410  0 
snd                     83674  16  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
cfg80211              524435  0 
lpc_ich                17145  0 
lib80211               14382  0 
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
uas                    18073  0 
usb_storage            49288  1 
ghash_clmulni_intel    13221  0 
aesni_intel            51134  189 
cryptd                 20531  6 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
i915                  599946  3 
nouveau               941415  0 
ttm                    83224  1 nouveau
drm_kms_helper         49197  2 i915,nouveau
drm                   276721  6 i915,nouveau,ttm,drm_kms_helper
r8169                  62766  0 
i2c_algo_bit           13565  2 i915,nouveau
mxm_wmi                13022  1 nouveau
video                  19598  2 i915,nouveau
compat                 19346  5 cfg80211,i915,nouveau,ttm,drm
wmi                    19257  3 dell_wmi,nouveau,mxm_wmi

```

---

### Post by wildmanne39 on 2013-07-11
Okay your device is not supported in 12.04 but we can add it.

First let's get rid of the wrong driver that you have loaded.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Then follow the directions in post 26 of this link.
[http://ubuntuforums.org/showthread.php?t=2103062&page=3](http://ubuntuforums.org/showthread.php?t=2103062&page=3)
Thanks

---

### Post by godleader on 2013-07-11
> **Wild Man said:**
> Okay your device is not supported in 12.04 but we can add it.

First let's get rid of the wrong driver that you have loaded.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Then follow the directions in post 26 of this link.
[http://ubuntuforums.org/showthread.php?t=2103062&page=3](http://ubuntuforums.org/showthread.php?t=2103062&page=3)
Thanks

sorry , i cant view the post 26 , it show until 20 only in page 2 

[COLOR=#000000]Results 11 to 20 of 29[/COLOR]

---

### Post by godleader on 2013-07-11
thanks so much , its can show page 3 right now ... i am trying :) hope it will work

---

### Post by godleader on 2013-07-11
> **Wild Man said:**
> Okay your device is not supported in 12.04 but we can add it.

First let's get rid of the wrong driver that you have loaded.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Then follow the directions in post 26 of this link.
[http://ubuntuforums.org/showthread.php?t=2103062&page=3](http://ubuntuforums.org/showthread.php?t=2103062&page=3)
Thanks

i've try still cant get it working and got error when trying to key in " sudo modprobe -r ath9k && sudo modprobe ath 9k" 
below are the msg show 

```
WARNING: Error inserting ath (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_hw (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/3.5.0-23-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```

---

### Post by wildmanne39 on 2013-07-11
The link I provided is to page three when you click on it you should be taken to page three not two.
What directions did you use to install the driver if you can not get to page three?
thanks

---

### Post by godleader on 2013-07-11
> **Wild Man said:**
> The link I provided is to page three when you click on it you should be taken to page three not two.
What directions did you use to install the driver if you can not get to page three?
thanks

sorry about that just now , it's my fault ,i am still new here .. hehe 

i've follow the posts 26 
download [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.7.9/compat-drivers-3.7.9-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.7.9/compat-drivers-3.7.9-1.tar.bz2)
and extract

```

cd Desktop/compat-drivers-3.7.9-1
./scripts/driver-select ath
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k

```

the last command i got error 
```
WARNING: Error inserting ath (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath.ko): Unknown symbol in module, or unknown parameter (see dmesg)WARNING: Error inserting ath9k_hw (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/3.5.0-23-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
``` 

after reboot it still same cant get it work ... please help this out 

thanks

---

### Post by wildmanne39 on 2013-07-11
Copy and paste for accuracy:
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Did you get any errors when you compiled the driver?
Thanks

---

### Post by godleader on 2013-07-11
> **Wild Man said:**
> Copy and paste for accuracy:
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Did you get any errors when you compiled the driver?
Thanks

there is no any error when complied just now 
this is what i get after copy paste 

```

dunno@dunno-Inspiron-3421:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath9k.ko
rmmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/mac80211.ko
rmmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath9k_common.ko
rmmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath9k_hw.ko
rmmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath.ko
rmmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/cfg80211.ko
dunno@dunno-Inspiron-3421:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/cfg80211.ko 
insmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath.ko 
insmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath9k_hw.ko 
insmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath9k_common.ko 
insmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/mac80211.ko 
insmod /lib/modules/3.2.0-49-generic/updates/cw-3.6/ath9k.ko nohwcrypt=1



```

---

### Post by wildmanne39 on 2013-07-11
Please copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.

[COLOR="#FF0000"]Did you also install linux-backports-modules-cw-3.6-precise-generic linux-backports-modules-cw-3.6?[/COLOR]
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by godleader on 2013-07-11
here is the txt file i get after copy paste the command

---

### Post by wildmanne39 on 2013-07-11
Please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
watch for errors, the wl driver is still causing trouble.
Thanks

---

### Post by godleader on 2013-07-11
> **Wild Man said:**
> Please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
watch for errors, the wl driver is still causing trouble.
Thanks


```
 
dunno@dunno-Inspiron-3421:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
Package bcmwl-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
]
```

thanks

---

### Post by wildmanne39 on 2013-07-11
Please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Reboot
Then post the output of:
```
dmesg | grep -e wl -e ath
```
Thanks

---

### Post by godleader on 2013-07-11
> **Wild Man said:**
> Please do:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Reboot
Then post the output of:
```
dmesg | grep -e wl -e ath
```
Thanks

after reboot 
```

dunno@dunno-Inspiron-3421:~$ dmesg | grep -e wl -e ath
[   16.789043] type=1400 audit(1373583506.518:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=979 comm="apparmor_parser"
[   16.790977] type=1400 audit(1373583506.518:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=979 comm="apparmor_parser"



```

---

### Post by wildmanne39 on 2013-07-11
That looks good.

Have you went to the top right corner of the screen and enabled networking and wireless?
If so double check please and if it does not connect remove the netinfo text file from the home folder and run the script again if it is scanning the file may be larger so it might be converted to a tar file then attach the file here.
Thanks

---

### Post by godleader on 2013-07-11
> **Wild Man said:**
> That looks good.

Have you went to the top right corner of the screen and enabled networking and wireless?
If so double check please and if it does not connect remove the netinfo text file from the home folder and run the script again if it is scanning the file may be larger so it might be converted to a tar file then attach the file here.
Thanks

has been double check on the top right corner , there is still no wireless network found , only have wired connection 
when i try to do iwconfig in terminal it still show 

```

dunno@dunno-Inspiron-3421:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

```

thanks so much bro for helping this trouble

---

### Post by wildmanne39 on 2013-07-11
Please do:
```
sudo modprobe -v ath9k
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n45
modinfo ath9k
```
Post the output of the last two commands.
Do not reboot.
Thanks

---

### Post by godleader on 2013-07-12
> **Wild Man said:**
> Please do:
```
sudo modprobe -v ath9k
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n45
modinfo ath9k
```
Post the output of the last two commands.
Do not reboot.
Thanks

```
dunno@dunno-Inspiron-3421:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.5.0-23-generic/updates/net/wireless/cfg80211.ko 
WARNING: Error inserting cfg80211 (/lib/modules/3.5.0-23-generic/updates/net/wireless/cfg80211.ko): Invalid argument
WARNING: Error inserting ath (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath.ko): Invalid argument
WARNING: Error inserting ath9k_hw (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Invalid argument
WARNING: Error inserting ath9k_common (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Invalid argument
WARNING: Error inserting mac80211 (/lib/modules/3.5.0-23-generic/updates/net/mac80211/mac80211.ko): Invalid argument
FATAL: Error inserting ath9k (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument
dunno@dunno-Inspiron-3421:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n45
Jul 12 06:58:26 dunno-Inspiron-3421 NetworkManager[917]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 12 06:58:26 dunno-Inspiron-3421 NetworkManager[917]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 12 06:58:26 dunno-Inspiron-3421 NetworkManager[917]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 12 06:58:26 dunno-Inspiron-3421 kernel: [   16.789043] type=1400 audit(1373583506.518:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=979 comm="apparmor_parser"
Jul 12 06:58:26 dunno-Inspiron-3421 kernel: [   16.790977] type=1400 audit(1373583506.518:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=979 comm="apparmor_parser"
Jul 12 06:58:26 dunno-Inspiron-3421 NetworkManager[917]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 12 06:58:28 dunno-Inspiron-3421 bluetoothd[908]: Endpoint registered: sender=:1.31 path=/MediaEndpoint/HFPAG
Jul 12 06:58:28 dunno-Inspiron-3421 bluetoothd[908]: Endpoint registered: sender=:1.31 path=/MediaEndpoint/A2DPSource
Jul 12 06:58:28 dunno-Inspiron-3421 bluetoothd[908]: Endpoint registered: sender=:1.31 path=/MediaEndpoint/A2DPSink
Jul 12 06:58:33 dunno-Inspiron-3421 bluetoothd[908]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/HFPAG
Jul 12 06:58:33 dunno-Inspiron-3421 bluetoothd[908]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSource
Jul 12 06:58:33 dunno-Inspiron-3421 bluetoothd[908]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSink
Jul 12 06:58:52 dunno-Inspiron-3421 bluetoothd[908]: Endpoint unregistered: sender=:1.31 path=/MediaEndpoint/HFPAG
Jul 12 06:58:52 dunno-Inspiron-3421 bluetoothd[908]: Endpoint unregistered: sender=:1.31 path=/MediaEndpoint/A2DPSource
Jul 12 06:58:52 dunno-Inspiron-3421 bluetoothd[908]: Endpoint unregistered: sender=:1.31 path=/MediaEndpoint/A2DPSink
Jul 12 07:11:59 dunno-Inspiron-3421 NetworkManager[905]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0)
Jul 12 07:11:59 dunno-Inspiron-3421 NetworkManager[905]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 12 07:11:59 dunno-Inspiron-3421 NetworkManager[905]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 12 07:11:59 dunno-Inspiron-3421 NetworkManager[905]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 12 07:11:59 dunno-Inspiron-3421 NetworkManager[905]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 12 07:11:59 dunno-Inspiron-3421 kernel: [   16.673026] type=1400 audit(1373584319.402:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=965 comm="apparmor_parser"
Jul 12 07:11:59 dunno-Inspiron-3421 kernel: [   16.673514] type=1400 audit(1373584319.402:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=965 comm="apparmor_parser"
Jul 12 07:12:01 dunno-Inspiron-3421 bluetoothd[895]: Endpoint registered: sender=:1.30 path=/MediaEndpoint/HFPAG
Jul 12 07:12:01 dunno-Inspiron-3421 bluetoothd[895]: Endpoint registered: sender=:1.30 path=/MediaEndpoint/A2DPSource
Jul 12 07:12:01 dunno-Inspiron-3421 bluetoothd[895]: Endpoint registered: sender=:1.30 path=/MediaEndpoint/A2DPSink
Jul 12 07:12:06 dunno-Inspiron-3421 bluetoothd[895]: Endpoint registered: sender=:1.41 path=/MediaEndpoint/HFPAG
Jul 12 07:12:06 dunno-Inspiron-3421 bluetoothd[895]: Endpoint registered: sender=:1.41 path=/MediaEndpoint/A2DPSource
Jul 12 07:12:06 dunno-Inspiron-3421 bluetoothd[895]: Endpoint registered: sender=:1.41 path=/MediaEndpoint/A2DPSink
Jul 12 07:12:25 dunno-Inspiron-3421 bluetoothd[895]: Endpoint unregistered: sender=:1.30 path=/MediaEndpoint/HFPAG
Jul 12 07:12:25 dunno-Inspiron-3421 bluetoothd[895]: Endpoint unregistered: sender=:1.30 path=/MediaEndpoint/A2DPSource
Jul 12 07:12:25 dunno-Inspiron-3421 bluetoothd[895]: Endpoint unregistered: sender=:1.30 path=/MediaEndpoint/A2DPSink
Jul 12 16:19:40 dunno-Inspiron-3421 NetworkManager[915]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0)
Jul 12 16:19:40 dunno-Inspiron-3421 NetworkManager[915]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 12 16:19:40 dunno-Inspiron-3421 NetworkManager[915]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 12 16:19:40 dunno-Inspiron-3421 NetworkManager[915]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 12 16:19:40 dunno-Inspiron-3421 NetworkManager[915]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 12 16:19:43 dunno-Inspiron-3421 bluetoothd[893]: Endpoint registered: sender=:1.30 path=/MediaEndpoint/HFPAG
Jul 12 16:19:43 dunno-Inspiron-3421 bluetoothd[893]: Endpoint registered: sender=:1.30 path=/MediaEndpoint/A2DPSource
Jul 12 16:19:43 dunno-Inspiron-3421 bluetoothd[893]: Endpoint registered: sender=:1.30 path=/MediaEndpoint/A2DPSink
Jul 12 16:19:48 dunno-Inspiron-3421 bluetoothd[893]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/HFPAG
Jul 12 16:19:48 dunno-Inspiron-3421 bluetoothd[893]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/A2DPSource
Jul 12 16:19:48 dunno-Inspiron-3421 bluetoothd[893]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/A2DPSink
Jul 12 16:20:07 dunno-Inspiron-3421 bluetoothd[893]: Endpoint unregistered: sender=:1.30 path=/MediaEndpoint/HFPAG
Jul 12 16:20:07 dunno-Inspiron-3421 bluetoothd[893]: Endpoint unregistered: sender=:1.30 path=/MediaEndpoint/A2DPSource
Jul 12 16:20:07 dunno-Inspiron-3421 bluetoothd[893]: Endpoint unregistered: sender=:1.30 path=/MediaEndpoint/A2DPSink
dunno@dunno-Inspiron-3421:~$ modinfo ath9k
filename:       /lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1691E5C96B2D3E27BB5227E
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,compat,cfg80211
vermagic:       3.5.0-23-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)
```

---

### Post by wildmanne39 on 2013-07-12
Hi, how come you are running some of the commands with the 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18 17:39:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux kernel and some with 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux kernel ?

You started with the first one I believe so that  maybe why we are getting an invalid arguement when trying to insert the module. 

How many drivers have you installed? and from where? 

I ask this earlier and you did not answer.

[COLOR="#FF0000"]**Did you also install linux-backports-modules-cw-3.6-precise-generic linux-backports-modules-cw-3.6? **[/COLOR]

Please post the results of:
```
cat /etc/modules
```
Thanks

---

