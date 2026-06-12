---
title: "HP 6570b ProBook Wireless"
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by mrbomb on 2013-03-30
Hi, I just installed ubuntu 12.10 on my HP ProBook 6570b. The wireless button stays orange and I have no wireless. When I press the button bluetooth toggles on and off but now wireless lan. I am relatively new to linux and ubuntu. Any suggestions. Thank you!

---

### Post by praseodym on 2013-03-31
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

### Post by mrbomb on 2013-03-31
praseodym,

Thanks much for the response here are the outputs:

```
root@newsome-HP-ProBook-6570b:/home/michael# lspci -nnk | grep -ia2 net
    Kernel driver in use: mei
    Kernel modules: mei
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:17ab]
    Kernel driver in use: e1000e
--
    Subsystem: Hewlett-Packard Company Device [103c:17ab]
    Kernel modules: sdhci-pci
24:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Hewlett-Packard Company BCM943228HM4L 802.11a/b/g/n 2x2 Wi-Fi Adapter [103c:182c]

root@newsome-HP-ProBook-6570b:/home/michael# lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 045e:0773 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. 
Bus 001 Device 004: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam
Bus 002 Device 003: ID 0a5c:21e1 Broadcom Corp.

root@newsome-HP-ProBook-6570b:/home/michael# lsmod
Module                  Size  Used by
nls_utf8               12558  1 
udf                    89521  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
coretemp               13401  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
tpm_infineon           17537  0 
ppdev                  17074  0 
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
rfcomm                 46620  12 
bnep                   18141  2 
microcode              22804  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                95595  0 
serio_raw              13216  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
parport_pc             32689  1 
joydev                 17458  0 
btusb                  22475  0 
bluetooth             209249  22 rfcomm,bnep,btusb
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
wmi                    19071  1 hp_wmi
tpm_tis                18681  0 
hp_accel               25977  0 
lis3lv02d              19830  1 hp_accel
input_polldev          13897  1 lis3lv02d
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                17062  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13206  0 
i915                  520615  3 
soundcore              15048  1 snd
drm_kms_helper         49113  1 i915
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
video                  19391  1 i915
mei                    40691  0 
lp                     17760  0 
parport                46346  3 ppdev,parport_pc,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  2 udf,firewire_core
ahci                   25721  2 
libahci                31192  1 ahci
e1000e                199273  0 
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
root@newsome-HP-ProBook-6570b:/home/michael# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

root@newsome-HP-ProBook-6570b:/home/michael# rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by wildmanne39 on 2013-03-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mrbomb on 2013-03-31
Code
Wildman, like so?
\code

---

### Post by wildmanne39 on 2013-03-31
Hi, please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```
Then
```
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

```
Reboot
Thanks

---

### Post by wildmanne39 on 2013-03-31
Like so:
```

```then paste the code in between them.
Thanks

---

### Post by mrbomb on 2013-03-31
Wildman,

I see. Sorry, new to forums posting. Thank you!

---

### Post by wildmanne39 on 2013-03-31
No worries we were all new once and we are still learning everyday.

If you follow the directions in my post above it should get your wireless working.
Thanks

---

### Post by mrbomb on 2013-03-31
[code]
root@newsome-HP-ProBook-6570b:/home/michael# sudo apt-get install bcmwl-kernal-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernal-source
[\code]

---

### Post by wildmanne39 on 2013-03-31
Just copy and paste the commands in the terminal, you have a typo.
You do have to be hardwired to the internet.
Thanks

---

### Post by mrbomb on 2013-03-31
Wildman, thank you very much for your patience. I entered the commands as indicated. I still don't have a wireless connection. I think this wireless button function may be suspect.

```

michael@newsome-HP-ProBook-6570b:~$ sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
broadcom-sta-common is already the newest version.
broadcom-sta-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by wildmanne39 on 2013-03-31
Please try:
```
sudo modprobe wl
```
Thanks

---

### Post by mrbomb on 2013-03-31
Here ya go:
```

michael@newsome-HP-ProBook-6570b:~$ sudo modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl

```

Thanks

---

### Post by wildmanne39 on 2013-03-31
I just tried it and it works on my computer so let's try the command this way:
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo modprobe wl
```
Thanks

---

### Post by praseodym on 2013-03-31
Did you install the kernel-headers and "build-essential"?

---

### Post by mrbomb on 2013-03-31
Here's what I get:

```

michael@newsome-HP-ProBook-6570b:~$ sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/3,150 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 148658 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace broadcom-sta-common 5.100.82.112-7 (using .../broadcom-sta-common_5.100.82.112-7_all.deb) ...
Unpacking replacement broadcom-sta-common ...
Preparing to replace broadcom-sta-source 5.100.82.112-7 (using .../broadcom-sta-source_5.100.82.112-7_all.deb) ...
Unpacking replacement broadcom-sta-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-26-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
FATAL: Error running install command for wl
update-initramfs: deferring update (trigger activated)
Setting up broadcom-sta-common (5.100.82.112-7) ...
update-initramfs: deferring update (trigger activated)
Setting up broadcom-sta-source (5.100.82.112-7) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic
michael@newsome-HP-ProBook-6570b:~$ sudo modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl

```

---

### Post by wildmanne39 on 2013-03-31
You need to install linux-kernel-headers and "build-essential as suggested by praseodym that is what is missing.

---

### Post by mrbomb on 2013-03-31
I am performing the build-essential and will reboot. Thanks.

```

michael@newsome-HP-ProBook-6570b:~$ sudo apt-get install --reinstall linux-headers-$(uname sudo-r) build-essential
uname: extra operand `sudo-r'
Try `uname --help' for more information.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'linux-headers' can't be removed
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/5,814 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 148658 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu3 (using .../build-essential_11.5ubuntu3_amd64.deb) ...
Unpacking replacement build-essential ...
Setting up build-essential (11.5ubuntu3) ...

```

---

### Post by wildmanne39 on 2013-03-31
Hold on a minute that last command when I copied and pasted it for you to install the headers and build essentials got messed up.

---

### Post by wildmanne39 on 2013-03-31
Try it like this:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```
Thanks

---

### Post by mrbomb on 2013-03-31
Okay. Thanks. Cool

---

### Post by mrbomb on 2013-03-31
This one performed some more steps. Should I run some other commands? It appears to have ended successfully. Will I need to do the broadcom steps again? Thanks

---

### Post by wildmanne39 on 2013-03-31
Try:
```
sudo modprobe wl
```
if it does not come on then post:
```
lsmod
```
Thanks

---

### Post by mrbomb on 2013-03-31
Here is the output:
```

michael@newsome-HP-ProBook-6570b:~$ sudo modprobe wl
michael@newsome-HP-ProBook-6570b:~$ lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17380  0 
wl                   2573608  0 
lib80211               14382  2 lib80211_crypt_tkip,wl
nls_utf8               12558  1 
udf                    89521  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
coretemp               13401  0 
tpm_infineon           17537  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  12 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
microcode              22804  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17458  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
btusb                  22475  0 
bluetooth             209249  22 bnep,rfcomm,btusb
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                18681  0 
lpc_ich                17062  0 
psmouse                95595  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
parport_pc             32689  1 
hp_accel               25977  0 
lis3lv02d              19830  1 hp_accel
input_polldev          13897  1 lis3lv02d
mei                    40691  0 
i915                  520615  3 
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
mac_hid                13206  0 
video                  19391  1 i915
wmi                    19071  1 hp_wmi
lp                     17760  0 
parport                46346  3 ppdev,parport_pc,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
ahci                   25721  2 
libahci                31192  1 ahci
e1000e                199273  0 
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  2 udf,firewire_core
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci

```

---

### Post by wildmanne39 on 2013-03-31
It should be working if not please copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

Also did you click on the network icon in the upper right corner of the screen and enable networking, do you see your wireless network?
Thanks

---

### Post by mrbomb on 2013-03-31
That did it! You are awesome! Thank you very much!!!

---

### Post by wildmanne39 on 2013-03-31
Your welcome!
Enjoy

---

### Post by frank40 on 2014-03-27
Sorry to dig up an old thread but I've tried the above steps and can't seem to get my wireless working. 

```

frank@frank-HP-ProBook-6570b:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:17ab]
	Kernel driver in use: e1000e
--
24:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
	Subsystem: Hewlett-Packard Company Device [103c:182c]
	Kernel modules: bcma
frank@frank-HP-ProBook-6570b:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. 
Bus 001 Device 004: ID 1bcf:2c03 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 0a5c:21e1 Broadcom Corp. 
frank@frank-HP-ProBook-6570b:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40279  1 
rfcomm                 47864  12 
bnep                   18258  2 
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_idt      71153  1 
snd_hda_intel          44339  3 
coretemp               13596  0 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
kvm                   455932  0 
uvcvideo               82214  0 
btusb                  22431  0 
bluetooth             247024  24 rfcomm,bnep,btusb
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_timer              29989  2 snd_pcm,snd_seq
ghash_clmulni_intel    13259  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
aesni_intel            55495  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i915                  620421  3 
tpm_infineon           17410  0 
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
hp_wmi                 18092  0 
gf128mul               14951  2 lrw,xts
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         49597  1 i915
joydev                 17613  0 
sparse_keymap          13890  1 hp_wmi
ppdev                  17113  0 
drm                   287564  4 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
wmi                    19256  1 hp_wmi
parport_pc             28284  1 
psmouse                97873  0 
i2c_algo_bit           13564  1 i915
hp_accel               26012  0 
tpm_tis                18761  0 
video                  19652  1 i915
lpc_ich                17144  0 
mei                    41820  0 
lis3lv02d              20200  1 hp_accel
mac_hid                13253  0 
serio_raw              13215  0 
microcode              23017  0 
lp                     17799  0 
input_polldev          13896  1 lis3lv02d
parport                46562  3 ppdev,parport_pc,lp
ahci                   25879  3 
libahci                31606  1 ahci
firewire_ohci          44864  0 
firewire_core          64836  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
e1000e                202313  0 
frank@frank-HP-ProBook-6570b:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

frank@frank-HP-ProBook-6570b:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
frank@frank-HP-ProBook-6570b:~$ 

```

---

### Post by praseodym on 2014-03-28
Hi,

is it 32 or 64bit? Does LAN work?

---

### Post by frank40 on 2014-03-29
> **praseodym said:**
> Hi,

is it 32 or 64bit? Does LAN work?


I managed to get it going. Thanks for your help.

---

