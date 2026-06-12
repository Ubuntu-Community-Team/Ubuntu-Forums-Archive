---
title: "Additional Drivers Broadcom STA Wireless Driver problem"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by VCTR on 2013-07-16
Hello.

When I open the Additional Drivers, select the driver and click in activate this message appears: "Sorry, installation of this driver failed. Please take a look at the log file for details: / var / log / jockey.log"

Already tried several ways to fix this error only is useless. Would you like to help me rezolver this problem.

Thanks.

---

### Post by praseodym on 2013-07-16
Do you really need the driver? Pleas show the terminal (CTRL+ALT+T) outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
What kind of computer is it?

---

### Post by VCTR on 2013-07-17
victor@victor-HP-Pavilion-g4-Notebook-PC:~$ uname -a
Linux victor-HP-Pavilion-g4-Notebook-PC 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
victor@victor-HP-Pavilion-g4-Notebook-PC:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1483]
	Kernel driver in use: wl
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:183d]
	Kernel driver in use: r8169
victor@victor-HP-Pavilion-g4-Notebook-PC:~$ lsmod
Module                  Size  Used by
snd_seq_dummy          12798  0 
nls_iso8859_1          12713  0 
michael_mic            12612  0 
arc4                   12615  0 
lib80211_crypt_tkip    17379  0 
wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  12 
binfmt_misc            17500  1 
ext2                   72837  1 
joydev                 17377  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
coretemp               13355  0 
snd_seq                61554  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
kvm                   443165  0 
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  19 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
hp_accel               26012  0 
lis3lv02d              20111  1 hp_accel
uvcvideo               80847  0 
input_polldev          13896  1 lis3lv02d
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
mac_hid                13205  0 
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
mac80211              606457  0 
btusb                  22474  0 
mei                    41158  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
bluetooth             228667  22 bnep,btusb,rfcomm
soundcore              12680  1 snd
cfg80211              510937  2 wl,mac80211
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
lpc_ich                17061  0 
psmouse                95870  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
serio_raw              13215  0 
xts                    12885  1 
gf128mul               14951  1 xts
dm_crypt               22820  2 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  0 
rtsx_pci_sdmmc         17475  0 
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
i915                  600396  3 
wmi                    19070  1 hp_wmi
video                  19390  1 i915
i2c_algo_bit           13413  1 i915
ahci                   25731  2 
libahci                31364  1 ahci
drm_kms_helper         49394  1 i915
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67466  0 
drm                   286028  4 i915,drm_kms_helper
victor@victor-HP-Pavilion-g4-Notebook-PC:~$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

victor@victor-HP-Pavilion-g4-Notebook-PC:~$ rfkill list

---

### Post by praseodym on 2013-07-18
The STA driver is not necessary for this device. Deactivate the driver there, uninstall it and install the missing firmware for the native driver:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```
Reboot.

---

