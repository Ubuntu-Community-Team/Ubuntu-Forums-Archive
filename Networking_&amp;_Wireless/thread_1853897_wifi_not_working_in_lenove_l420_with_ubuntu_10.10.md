---
title: "wifi not working in lenove l420 with ubuntu 10.10"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by moneeshk on 2011-10-03
Hi,

I am also using lenove l420 and but wireless on the ubuntu 10.10 is not working please help.

Output of the commands 

[COLOR=#000000][FONT=Times New Roman][FONT=arial]lspci -nnk | grep -iA2 net

[/FONT][/FONT][/COLOR]  ```

     03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Lenovo Device [17aa:21dd]
    Kernel driver in use: r8169 
 
```second command: iwconfig
 ```

     lo        no wireless extensions.

eth0      no wireless extensions. 

 
```third command: lsmod
 ```
 
     Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
rfcomm                 33843  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
joydev                  8767  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_realtek   218460  1 
i915                  295819  3 
drm_kms_helper         30136  1 i915
drm                   168092  3 i915,drm_kms_helper
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
uvcvideo               55911  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
btusb                  11001  2 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
intel_agp              26566  2 i915
i2c_algo_bit            5168  1 i915
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32011  2 drm,intel_agp
thinkpad_acpi          67627  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49102  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
led_class               2633  1 thinkpad_acpi
nvram                   6342  1 thinkpad_acpi
tpm_tis                 7658  0 
tpm                    13803  1 tpm_tis
tpm_bios                5310  1 tpm
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19326  2 
r8169                  36553  0 
mii                     4425  1 r8169
libahci                21728  1 ahci
 
```

---

### Post by praseodym on 2011-10-03
Hi,

install the driver manually via cable:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
cd Downloads
wget http://media.cdn.ubuntu-de.org/forum/attachments/2785845/rtl8192ce_linux_2.6.0005.1116.2010.tar.gz
tar xvf rtl8192ce_linux_2.6.0005.1116.2010.tar.gz
cd rtl8192ce_linux_2.6.0005.1116.2010
make
sudo make install 
```
If there is an error with "sudo make install" then move the module by hand:
```
cd HAL/rtl8192
sudo cp r8192ce_pci.ko /lib/modules/$(uname -r)/kernel/net/wireless/
sudo depmod -a
sudo update-initramfs -u 
```
and reboot.

---

