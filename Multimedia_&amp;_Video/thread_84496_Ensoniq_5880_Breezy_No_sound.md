---
title: "Ensoniq 5880 Breezy No sound"
date: 2005-10-31
forum: Multimedia &amp; Video
---

### Post by noctambulo on 2005-10-31
After succesfully installing Ubuntu on my laptop, :) I'm having some trouble doing the same in my desktop.:confused:  I'm following the troubleshooter pointers from Linux sound howto.:shock:  This is what I get. 

**1. Linux version**
uname -a
Linux ubuntu2 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

**2. Sound modules seem to be loaded**. Apart from the ensoniq audio card, I've also got a tv card (bttv). There seems to be both references to emu10kl and ens1371 ....
/sbin/lsmod
Module                  Size  Used by
emu10k1                68484  0
sound                  70444  1 emu10k1
ac97_codec             17420  1 emu10k1
ipt_limit               2432  8
iptable_mangle          2816  0
ipt_LOG                 6400  8
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  1
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  6
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppp_synctty             8704  1
ppp_generic            25748  5 ppp_synctty
slhc                    6656  1 ppp_generic
n_hdlc                  8708  1
nls_utf8                2176  1
nls_cp437               5888  2
isofs                  32824  1
vfat                   12288  1
fat                    46492  1 vfat
udf                    75524  0
ipv6                  217408  8
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
tsdev                   7616  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_ens1371            22240  0
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  3 emu10k1,sound,snd
snd_page_alloc         10120  1 snd_pcm
bttv                  141456  0
video_buf              19844  1 bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
videodev                9344  1 bttv
i2c_amd756              6148  0
i2c_core               19728  5 i2c_acpi_ec,bttv,i2c_algo_bit,tveeprom,i2c_amd756
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
amd_k7_agp              8460  1
agpgart                32328  1 amd_k7_agp
dm_mod                 50364  1
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
sd_mod                 17424  2
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
usb_storage            64704  2
scsi_mod              124872  2 sd_mod,usb_storage
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104188  5 usbhid,usb_storage,ehci_hcd,ohci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  4
ide_generic             1664  0
amd74xx                12828  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  608
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


**3. Kernel sound drivers are NOT compiled in**

ls -l /dev/dsp

ls: /dev/dsp: No such file or directory

$ cat crash.au >/dev/audio
bash: /dev/audio: No such device
$ sudo ls -l /dev/sound
ls: /dev/sound: No such file or directory

The suggested solution; use of to edit /dev/MAKEDEV is way out of my weight class at this time ...
$ gedit /dev/MAKEDEV


**4. Other tests I have run **

a) Running lspci
~$ lspci
0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
0000:00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
0000:00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
0000:00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
0000:00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
0000:00:08.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 12)
0000:00:09.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:09.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
**0000:00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)**
0000:01:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

**2. The only file in /dev/snd is timer**

**3. When I try to load the module I'm told will work, I get: **

g$ sudo modprobe snd-es1371
Password:
FATAL: Module snd_es1371 not found.

3bis on the other hand snd-ens1371 says

sudo modprobe snd-ens1371

Does not complain but it doesn't improve things either...

4. Despite the content of lspci, aplay says It can't find my sound card

 aplay -l
aplay: device_list:218: no soundcards found...

Thanks in advance for any help... or perhaps for any additional tests I might want to run??? ;)

---

