---
title: "No wifi on easynote TE, ubuntu 12.04"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by Nidding on 2013-08-02
Hey.
I have a packard bell easynote TE where the wifi doesn't work. I've tried a few things suggested here and other places, but none of them with succes. Any suggestions as to what to do to make it work?

---

### Post by Nidding on 2013-08-02
Woops. Forgot o say that I'm running ubuntu 12.04. Also I have been able to connect to wifi through a trendnet N150 wifi adaptor, but as there is onboard wifi, I'd much prefer to use that :)

---

### Post by praseodym on 2013-08-02
Please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```
without the stick being plugged.

---

### Post by Nidding on 2013-08-02
> **praseodym said:**
> Please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```
without the stick being plugged.
Here we go :)
```
nidding@nidlap:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:10a1] (rev 13)
	Subsystem: Acer Incorporated [ALI] Device [1025:076b]
	Kernel driver in use: alx
--
05:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:0632]
nidding@nidlap:~$ lsusb
Bus 002 Device 002: ID 064e:e330 Suyin Corp. 
Bus 004 Device 002: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
nidding@nidlap:~$ lsmod
Module                  Size  Used by
psmouse               102506  0 
vesafb                 13846  1 
kvm                   422160  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
joydev                 17694  0 
snd_hda_codec_realtek    79855  1 
snd_hda_codec_hdmi     32476  1 
r8712u                189715  0 
microcode              23030  0 
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
serio_raw              13216  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
fam15h_power           13167  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i2c_piix4              13302  0 
btusb                  22432  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 47562  12 
parport_pc             32867  0 
bnep                   18240  2 
bluetooth             211860  24 btusb,rfcomm,bnep
ppdev                  17114  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
alx                    73500  0 
mdio                   13808  1 alx
snd                    83674  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19653  0 
soundcore              15092  1 snd
wmi                    19257  0 
mac_hid                13254  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ahci                   25869  2 
libahci                27338  1 ahci
sdhci_pci              18749  0 
sdhci                  33145  1 sdhci_pci
nidding@nidlap:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

nidding@nidlap:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
nidding@nidlap:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
nidding@nidlap:~$ sudo iwlist scan
[sudo] password for nidding: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.
```
Thanks for the reply :)

---

### Post by praseodym on 2013-08-02
Check, which driver supports your card (if any):

```
modprobe -c | grep -i "168C:*0036"
```
If there is no output install the backport modules:
```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic linux-backports-modules-cw-3.6-$(uname -r) build-essential dkms
```

---

### Post by Nidding on 2013-08-02
modprobe gives no output, and there seem to be some error when I try to install the backport module
```
nidding@nidlap:~$ modprobe -c | grep -i "168C:*0036"
nidding@nidlap:~$ sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic linux-backports-modules-cw-3.6-$(uname -r) build-essential dkms
[sudo] password for nidding: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.6-quantal-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-quantal-generic'
E: Unable to locate package linux-backports-modules-cw-3.6-3.5.0-37-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-3.5.0-37-generic'

```

---

### Post by praseodym on 2013-08-02
Please show
```

uname -a
```

---

### Post by Nidding on 2013-08-02
nidding@nidlap:~$ uname -a
Linux nidlap 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:48:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Nidding on 2013-08-02
Double post

---

### Post by praseodym on 2013-08-03
[http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-37-generic_3.5.0-37.26_amd64.deb](http://ppa.launchpad.net/canonical-kernel-team/ppa/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-37-generic_3.5.0-37.26_amd64.deb)

Install this package via:
```

sudo dpkg -i *.deb
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
Load the driver and check:
```

sudo modprobe -v ath9k
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep ath
```

---

### Post by Nidding on 2013-08-03
I did that, and WIFI is now working. Thanks a lot for the help :)

---

