---
title: "Lenovo Ideapad s10-3 Wireless not working"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by jonessoda219 on 2013-03-15
Hi
I have a Lenovo ideapad s10-3 running ubuntu 12.10. I have a atheros 9285 wireless card in it. In rfkill it says it is hardblocked. I have the switch for the wireless on and the light is on. Please help with this issue I have been working on it for over a week. Thank you so much.

---

### Post by jonessoda219 on 2013-03-15
Bump. I somehow knocked Wifi off of my network options. Someone also please help with that..

---

### Post by praseodym on 2013-03-16
Did you try to reset the BIOS? If you are **not** having (U)EFI only!

---

### Post by jonessoda219 on 2013-03-16
Yes, I have tried to reset it in BIOS. I will try again. I know of alot of people in these forums having the same or a similar problem with this wireless adapter.

---

### Post by praseodym on 2013-03-16
Check the outputs of:
```

lsmod
rfkill list
```
If it shows "yes" for blocked, try
```

sudo rfkill unblock all
```
Any other button/switch on the outside?

---

### Post by jonessoda219 on 2013-03-16
Lsmod:
randy@randy-Lenovo:~$ sudo modprobe wl
\[sudo] password for randy: 
Sorry, try again.
[sudo] password for randy: 
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save.1, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ath9k.conf.save line 2: ignoring bad line starting with 'save'
WARNING: /etc/modprobe.d/ath9k.conf.save.1 line 4: ignoring bad line starting with 'rfkill'
randy@randy-Lenovo:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
09:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
randy@randy-Lenovo:~$ sudo modrobe wl
sudo: modrobe: command not found
randy@randy-Lenovo:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save.1, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ath9k.conf.save line 2: ignoring bad line starting with 'save'
WARNING: /etc/modprobe.d/ath9k.conf.save.1 line 4: ignoring bad line starting with 'rfkill'
randy@randy-Lenovo:~$ lsmod |grep mac80211mac80211              461261  0 
cfg80211              175574  2 mac80211,ath
randy@randy-Lenovo:~$ lsmod |grep mac80211
mac80211              461261  0 
cfg80211              175574  2 mac80211,ath
randy@randy-Lenovo:~$ sudo modrobe wl
sudo: modrobe: command not found
randy@randy-Lenovo:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save.1, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ath9k.conf.save line 2: ignoring bad line starting with 'save'
WARNING: /etc/modprobe.d/ath9k.conf.save.1 line 4: ignoring bad line starting with 'rfkill'
randy@randy-Lenovo:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
09:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
randy@randy-Lenovo:~$ enable wireless
bash: enable: wireless: not a shell builtin
randy@randy-Lenovo:~$ wlan0 up
wlan0: command not found
randy@randy-Lenovo:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
randy@randy-Lenovo:~$ iwconfigbnep0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

randy@randy-Lenovo:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
randy@randy-Lenovo:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia k3b k3b-data k3b-i18n kdevelop-l10n
  kdevelop-php-docs-l10n kdevelop-php-l10n language-pack-kde-en libflac++6
  libk3b6 libkcddb4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,150 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 221880 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-25-generic
Building for architecture i686
Building initial module for 3.5.0-25-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-25-generic/updates/dkms/

depmod....

DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ath9k.conf.save.1, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ath9k.conf.save line 2: ignoring bad line starting with 'save'
WARNING: /etc/modprobe.d/ath9k.conf.save.1 line 4: ignoring bad line starting with 'rfkill'
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
randy@randy-Lenovo:~$ CLEAR
CLEAR: command not found
randy@randy-Lenovo:~$ cler
No command 'cler' found, did you mean:
 Command 'clear' from package 'ncurses-bin' (main)
 Command 'clex' from package 'clex' (universe)
 Command 'cver' from package 'gplcver' (universe)
cler: command not found
randy@randy-Lenovo:~$ clear

randy@randy-Lenovo:~$ lsmod
Module                  Size  Used by
wl                   2442880  0 
lib80211               14041  1 wl
rfcomm                 37277  12 
parport_pc             31969  0 
bnep                   17708  3 
ppdev                  12818  0 
binfmt_misc            17261  1 
coretemp               13169  0 
joydev                 17162  0 
snd_hda_codec_realtek    63579  1 
microcode              18210  0 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
psmouse                84878  0 
serio_raw              13032  0 
ideapad_laptop         13671  0 
sparse_keymap          13659  1 ideapad_laptop
lpc_ich                16926  0 
uvcvideo               71278  0 
snd_seq_midi           13133  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
btusb                  17987  0 
snd_timer              24412  2 snd_pcm,snd_seq
bluetooth             183270  24 rfcomm,bnep,btusb
mac80211              461261  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13784  0 
ath9k_hw              376228  1 ath9k_common
ath                    19188  2 ath9k_common,ath9k_hw
wmi                    18591  0 
i915                  457241  3 
cfg80211              175574  2 mac80211,ath
mac_hid                13038  0 
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
soundcore              14600  1 snd
video                  18895  1 i915
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
ums_realtek            17670  0 
r8169                  55977  0 
usb_storage            39351  1 ums_realtek
randy@randy-Lenovo:~$ clear

randy@randy-Lenovo:~$ lsmod
Module                  Size  Used by
wl                   2442880  0 
lib80211               14041  1 wl
rfcomm                 37277  12 
parport_pc             31969  0 
bnep                   17708  3 
ppdev                  12818  0 
binfmt_misc            17261  1 
coretemp               13169  0 
joydev                 17162  0 
snd_hda_codec_realtek    63579  1 
microcode              18210  0 
snd_hda_intel          32516  3 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
psmouse                84878  0 
serio_raw              13032  0 
ideapad_laptop         13671  0 
sparse_keymap          13659  1 ideapad_laptop
lpc_ich                16926  0 
uvcvideo               71278  0 
snd_seq_midi           13133  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
btusb                  17987  0 
snd_timer              24412  2 snd_pcm,snd_seq
bluetooth             183270  24 rfcomm,bnep,btusb
mac80211              461261  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13784  0 
ath9k_hw              376228  1 ath9k_common
ath                    19188  2 ath9k_common,ath9k_hw
wmi                    18591  0 
i915                  457241  3 
cfg80211              175574  2 mac80211,ath
mac_hid                13038  0 
snd                    62146  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
soundcore              14600  1 snd
video                  18895  1 i915
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
ums_realtek            17670  0 
r8169                  55977  0 
usb_storage            39351  1 ums_realtek
randy@randy-Lenovo:~$ 


rfkill
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
randy@randy-Lenovo:~$ 

I had my atheros adapter under phy0 but I did a command now it doesnt recognize it..

---

