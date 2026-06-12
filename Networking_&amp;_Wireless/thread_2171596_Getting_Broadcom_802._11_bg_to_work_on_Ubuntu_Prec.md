---
title: "Getting Broadcom 802. 11 b/g to work on Ubuntu Precise/Elementary 12.4"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by Purnish_Dave on 2013-08-31
I am new to Ubuntu and am trying to set up my Broadcom wireless to work. When I run lspci it specifies the driver installed. It can identify the device. But under System Settings > Wireless, it says no firmware installed. Also, I can't find any drivers under 'Additional Drivers'. What should I do in this case?

---

### Post by ibjsb4 on 2013-08-31
There are three firmware packages, depends on which BCM you have.

[ATTACH=CONFIG]245869[/ATTACH]

You can find them in the software center.

---

### Post by Hadaka on 2013-08-31
Hi, please open a terminal...ctrl/alt/t then Copy
and paste the following..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list
```
post the output..thanks.

---

### Post by Purnish_Dave on 2013-08-31
> **ibjsb4 said:**
> There are three firmware packages, depends on which BCM you have.

[ATTACH=CONFIG]245869[/ATTACH]

You can find them in the software center.

Unfortunately, I can't find an option for 'firmware' listed

This is what I see

[IMG]file:/C:/Users/PURNISH/Downloads/33.png[/IMG]

Sorry can't get the file url right.. I am operating from a Windows file system right now.

I have bcm4312 by the way, if that helps.

I also tried to copy the driver from my Windows installation to the Linux partition and tried installing using ndiswrapper but it returned with errors saying bcmwl666.sys was not found. Should I paste the output to that?

Can you help?

---

### Post by Purnish_Dave on 2013-08-31
> **Hadaka said:**
> Hi, please open a terminal...ctrl/alt/t then Copy
and paste the following..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list
```
post the output..thanks.

hadaka,
here are the outputs

lspci -nn | egrep '0200|0280'

> 03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)




lsmod

> Module                  Size  Used by
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                97485  0 
b43                   365819  0 
snd_seq_midi           13324  0 
serio_raw              13211  0 
uvcvideo               72627  0 
snd_rawmidi            30748  1 snd_seq_midi
videodev               98259  1 uvcvideo
jmb38x_ms              17646  0 
v4l2_compat_ioctl32    17128  1 videodev
mac80211              506862  1 b43
memstick               16569  1 jmb38x_ms
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205774  2 b43,mac80211
bcma                   26696  1 b43
btusb                  18332  2 
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
ir_mce_kbd_decoder     12777  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
ir_rc6_decoder         12507  0 
ir_rc5_decoder         12507  0 
rc_rc6_mce             12502  0 
ene_ir                 18457  0 
ir_nec_decoder         12507  0 
parport_pc             32866  0 
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ene_ir,ir_nec_decoder
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
bluetooth             180153  23 btusb,rfcomm,bnep
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
i915                  477763  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
hid                    99636  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62154  0 
ssb                    52752  1 b43
wmi                    19256  1 hp_wmi
i2c_algo_bit           13423  1 i915
video                  19651  1 i915



rfkill list

> 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no



what should i do next?

---

### Post by Hadaka on 2013-08-31
Hi, please do..
```
sudo apt get install firmware-b43-lpphy-installer
sudo modprobe b43
```
thanks.

---

### Post by Purnish_Dave on 2013-09-01
Hi,

When I try to install firmware-b43-lpphy-installer, it says that it depends on
b43-fw-cutter_015-14.1_i386.deb
which is fine. it's a utility to extract and place the firmware
b43-fw-cutter_015-14.1_i386.deb
depends on libc6
I have never been able to get libc6 to work on my distro because the dependencies seem to be quite deep and circular.
I also had to try to install libc6 when getting bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb to work.
but libc6 is not easy to install on my distro if at all possible.
but it seems to be required.

can you advise me how to proceed? thanks!

---

### Post by praseodym on 2013-09-01
Install this tarball instead:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
sudo modprobe -rfv b43
sudo modprobe -v b43
sudo service network-manager restart 
```

---

### Post by jonathan_wrobel on 2013-09-01
I'm very new to Linux and running into the same problem with a Dell Studio 17.  When I try to install the additional Hardware drivers that are related to the broadcam card I get this error:

"sorry, installation of this driver failed
Please have a look at the log file for details: /var/log/jockey.log"

I tried some of the different instructions for other to no avail.

This is what I'm getting when I rn the commands that I see recommended:

lspci -nn | grep 0280

> 04:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

lsmod

> Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
joydev                 17613  0 
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_idt      71153  1 
coretemp               13596  0 
snd_hda_intel          44339  3 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
kvm_intel             137899  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm                   455932  1 kvm_intel
uvcvideo               82214  0 
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
snd_seq_midi           13324  0 
psmouse                97873  0 
ir_mce_kbd_decoder     12777  0 
snd_rawmidi            30417  1 snd_seq_midi
ir_sanyo_decoder       12513  0 
ir_sony_decoder        12510  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         40785  1 uvcvideo
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
videodev              130053  2 uvcvideo,videobuf2_core
ir_jvc_decoder         12507  0 
r852                   18241  0 
sm_common              16860  1 r852
nand                   59304  2 r852,sm_common
mtd                    45243  2 sm_common,nand
ir_rc6_decoder         12507  0 
videobuf2_vmalloc      13056  1 uvcvideo
ir_rc5_decoder         12507  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
nand_ids               12723  1 nand
i915                  620421  3 
ir_nec_decoder         12507  0 
dell_wmi               12681  0 
dell_laptop            17425  0 
nand_bch               13147  1 nand
rc_rc6_mce             12502  0 
serio_raw              13215  0 
bch                    22063  1 nand_bch
r592                   18144  0 
ite_cir                25776  0 
snd_timer              29989  2 snd_pcm,snd_seq
rc_core                 26422  11  ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ite_cir
microcode              23017  0 
memstick               16605  1 r592
nand_ecc               13273  1 nand
lpc_ich                17144  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14449  1 dell_laptop
drm_kms_helper         49597  1 i915
sparse_keymap          13890  1 dell_wmi
wmi                    19256  1 dell_wmi
drm                   287564  4 i915,drm_kms_helper
snd                     69533  16  snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
i2c_algo_bit           13564  1 i915
video                  19652  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
firewire_ohci          44864  0 
firewire_core          64836  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
tg3                   165622  0 
ahci                   25879  2 
ptp                    18668  1 tg3
pps_core               14080  1 ptp
libahci                31606  1 ahci


rfkill list doesn't bring up anything.

Can anyone point me in the right direction?  

Thanks so much in advance.

---

### Post by praseodym on 2013-09-01
Did you install the compiling tools:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms bcmwl-kernel-source
```

---

### Post by Purnish_Dave on 2013-09-01
> **praseodym said:**
> Install this tarball instead:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
sudo modprobe -rfv b43
sudo modprobe -v b43
sudo service network-manager restart 
```

i did this and it worked within the space of a few seconds !!

guess i wrote the firmware directly on to the broadcom wlan chipset and removed and reinserted the b43 module.

thanks a million !!

---

