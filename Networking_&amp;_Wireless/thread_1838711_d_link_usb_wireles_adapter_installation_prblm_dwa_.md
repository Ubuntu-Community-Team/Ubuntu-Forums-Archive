---
title: "d link usb wireles adapter installation prblm dwa 125 n 150"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by sandeepch on 2011-09-04
Not able to install DWA 125 USB ADAPTOR N 150 On ubuntu 10.04 . is any package available for this device ?? .. 
some case It  work IF we upgrade all the packages from net . but the actual problem is that we can only able to upgrade the package after card work. can we download and install actual tar or deb package for this device?

---

### Post by praseodym on 2011-09-04
Hello,

this device may have different chipsets. Please post the following terminal outputs:

```
lsusb
lsmod
rfkill list
iwconfig
```

---

### Post by mym2f on 2011-09-18
Hi ..... 
The same problem here but with DWA-126 Wireless N 150 USB adapter

My Output
lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3a10 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod
Module                  Size  Used by
ndiswrapper           249811  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
snd_ens1371            25634  2 
gameport               19652  1 snd_ens1371
snd_ac97_codec        134270  1 snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ppdev                  17113  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
vmw_balloon            12841  0 
psmouse                73535  0 
parport_pc             36959  1 
serio_raw              13166  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  1 snd_pcm
i2c_piix4              13303  0 
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
floppy                 74120  0 
mptspi                 22738  2 
mptscsih               44457  1 mptspi
e1000                 111862  0 
mptbase               102904  2 mptspi,mptscsih
scsi_transport_spi     30630  1 mptspi

rfkill list

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I hope the reply as soon as possible ...... Thanks for help

---

### Post by praseodym on 2011-09-18
Hi mym2f,

your device obviously contains an Atheros Chipset, not Realtek:

> Bus 001 Device 002: ID 07d1:3a10 D-Link System 
hint from [here]("http://www.backtrack-linux.org/forums/beginners-forum/39303-tp-link-tl-wn721n-help-pleaseeeeeeee.html#post193396")

Please show the outputs of:

```
uname -a
modinfo ar9170usb | grep 3A10
modinfo carl9170 | grep 3A10
modinfo ath9k_htc | grep 3A10

```

---

### Post by mym2f on 2011-09-18
Thank you very much for ur fast reply [praseodym]("http://ubuntuforums.org/member.php?u=1411497") ^_^
Here is the output u asked me to try :
uname -a
Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

modinfo ar9170 | grep 3A10
ERROR: modinfo: could not find module ar9170

modinfo car9710 | grep 3a10
ERROR: modinfo: could not find module car9710

modinfo ath9k_htc | grep 3A10
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*

Waiting for the solution from an expert like u ^_^

---

### Post by praseodym on 2011-09-19
Uninstall Ndiswrapper completely and update/install the firmware for the native driver:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz
sudo tar xvf ath_htc_firmware-1.tar.gz -C /lib/firmware 
sudo modprobe -v ath9k_htc
sudo service network-manager restart
```
replug the stick.

Controls:

```
iwconfig
rfkill list
lsmod
dmesg | grep ath
sudo iwlist scan
```

---

### Post by mym2f on 2011-09-19
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rfkill list

lsmod
Module                  Size  Used by
ath9k_htc              91084  0 
mac80211              302021  1 ath9k_htc
ath9k_common           13839  1 ath9k_htc
ath9k_hw              313028  2 ath9k_htc,ath9k_common
ath                    23782  2 ath9k_htc,ath9k_hw
cfg80211              192234  3 ath9k_htc,mac80211,ath
vesafb                 13761  1 
binfmt_misc            17565  1 
snd_ens1371            25634  2 
gameport               19652  1 snd_ens1371
snd_ac97_codec        134270  1 snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ppdev                  17113  0 
snd_timer              29602  2 snd_pcm,snd_seq
vmw_balloon            12841  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
serio_raw              13166  0 
parport_pc             36959  1 
snd                    67382  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  1 snd_pcm
i2c_piix4              13303  0 
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
mptspi                 22738  2 
mptscsih               44457  1 mptspi
e1000                 111862  0 
mptbase               102904  2 mptspi,mptscsih
scsi_transport_spi     30630  1 mptspi
floppy                 74120  0 

dmesg | grep ath
[    2.180361] device-mapper: multipath: version 1.2.0 loaded
[    2.180364] device-mapper: multipath round-robin: version 1.0.0 loaded
[  701.928477] usbcore: registered new interface driver ath9k_htc
[  735.957241] usb 1-1: ath9k_htc: Firmware - htc_9271.fw download failed
[  735.957285] ath9k_htc: probe of 1-1:1.0 failed with error -22

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Sorry , that did not work properly. ^_^ ??????

---

### Post by praseodym on 2011-09-19
> [ 735.957241] usb 1-1: ath9k_htc: Firmware - htc_9271.fw download failed

Here the link with the missing firmware package:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/3005772/htc_9271_V13_Firmware.tar.gz
sudo tar xvf htc_9271_V13_Firmware.tar.gz -C /lib/firmware
```

---

### Post by mym2f on 2011-09-19
Hi again ........

The same problem with the same error

Could the problem be something else besides the firmware ???

---

### Post by praseodym on 2011-09-19
Try to upgrade the driver:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2        
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install 
```
Reboot.

---

### Post by mym2f on 2011-09-19
Thank you for not giving up !!!!!!!!!

tar -jxvf compat-wireless-2.6.tar.bz2

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now

---

### Post by praseodym on 2011-09-19
Richt-click on the tar.bz2 file->"Unpack here" and continue with the "cd" command.

---

### Post by mym2f on 2011-09-19
The same hint above appeared .... seems that the file is really corrupted

---

### Post by praseodym on 2011-09-19
Try this one:

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

---

### Post by mym2f on 2011-09-19
I think that your codes are all perfect but it seems that my system is somehow rejecting this normal way of updating firmware and driver.

Could the problem be in my VMware player software or in the version of Ubuntu 64-bit that I am using ??

( Note : I have tried BackTrack5 genome 32-bit with VMware player and the problem is the same .... the drive appear in the lsusb but it does not function as wlan0 or ath0 when I use iwconfig or airmon-ng nither the interface nor the chipset or drive is detected)  ^_^

Can you recommend me any Linux OS torrent image which will work with my DWA-126 usb card ? ( I mean one that you already tried successfully ):)

---

### Post by mym2f on 2011-09-19
Thanxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Very Very Very Very Very Much

It seems that you helped me to solve the problem with my own idea !!!!

There are small icons at the bottom of VMware player

I just right-click on d-link 11n adapter and chosen Connect (Disconnect from host) and it works as wlan0

^_^ ^_^ ^_^ 

Thank you very much again praseodym and I hope other members will get use of this thread

:D:D:D:D:D

---

### Post by mym2f on 2011-09-19
^_^

---

