---
title: "agp not enabled please help"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by linuxnoob40 on 2006-08-12
allow me to start by saying i am a total noob and im so confused after reading all day on many different forums.
ok here we go
the basics of it is i find agp is no longer enabled after i edited xorg conf it used to look like this
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
Option "nvidia"  

EndSection

now it looks like this after i edited the file 
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
Option "NvAGP" "1" 
Option "RenderAccel" "off" 
Option "IgnoreDisplayDevices" "DFP,TV" 
Option "NoRenderExtension" "Off" 
Option "AllowGLXWithComposite" "off" 
EndSection

this is what i have when i check if agp is enabled
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

my card is geforce 7800 gs oc i am at a wall here i dont know what to do to get this back working again,
Please Help!!

---

### Post by louis_nichols on 2006-08-12
I just went through a similarv process and it seems I've gotten somewhere. I posted my results in [this post]("http://ubuntuforums.org/showthread.php?t=234495"). I suggets you just follow the instructions in the links I posted. They work.

---

### Post by linuxnoob40 on 2006-08-12
ok i reconfigured xserver so now agp is working howver it says agpgart for a driver and not nvidia so now im back to square one again how do i lose agpgart and gain nvidia:confused:  ](*,)

---

### Post by tseliot on 2006-08-13
> **linuxnoob40 said:**
> ok i reconfigured xserver so now agp is working howver it says agpgart for a driver and not nvidia so now im back to square one again how do i lose agpgart and gain nvidia:confused:  ](*,)

Agpgart works just fine and is more compatible than nvidia.

Anyhow if you're convinced that you need it post the output of:
```
lsmod
```

---

### Post by linuxnoob40 on 2006-08-13
ok here is the output of lsmod.
Module                  Size  Used by
snd_rtctimer            3340  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                   9220  0
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
vfat                   13440  0
fat                    53020  1 vfat
ipv6                  265728  8
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
tsdev                   8000  0
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
joydev                 10048  0
rtc                    13492  1 snd_rtctimer
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
analog                 12320  0
snd_emu10k1           117284  2 snd_emu10k1_synth
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
sk98lin               164832  0
skge                   38800  0
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         93088  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  4 snd_rtctimer,snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
af_packet              22920  4
psmouse                36100  0
nvidia               4550772  12
serio_raw               7300  0
usbhid                 39904  0
snd                    55268  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10208  1 snd
emu10k1_gp              3840  0
gameport               15496  3 analog,emu10k1_gp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
amd64_agp              12356  1
agpgart                34888  2 nvidia,amd64_agp
i2c_nforce2             6912  0
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
sg                     37920  0
evdev                   9856  4
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
forcedeth              30732  0
ehci_hcd               34184  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ohci_hcd               21892  0
usbcore               130692  4 usbhid,ehci_hcd,ohci_hcd
sata_sil                9348  0
ide_disk               17664  1
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
generic                 5124  0
sd_mod                 19984  3
amd74xx                15260  0 [permanent]
sata_nv                 9732  4
libata                 78992  2 sata_sil,sata_nv
scsi_mod              139496  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                13576  0
processor              23360  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

 its not so much that im convinced that i need nvidia as it is that i want to increase my frame rate,30fps just doesnt cut it

---

### Post by tseliot on 2006-08-13
Blackist the amd64_agp & agpgart modules by adding this to your /etc/modprobe.d/blacklist (don't worry if the file is blank or doesn't exist):

```
sudo nano -w /etc/modprobe.d/blacklist
```

Copy and paste the following lines:
```
blacklist agpgart
blacklist amd64_agp
```

CTRL+X to exit (save)

```
sudo nano -w /etc/X11/xorg.conf
```

Put this option in the Section Device of your /etc/X11/xorg.conf:

```
Option          "NvAGP"                 "1"
```
 
Restart your computer

---

### Post by linuxnoob40 on 2006-08-13
still only getting about 30 fps got any other tips or tricks to increase it? otherwise all works i thank you much

---

### Post by tseliot on 2006-08-13
Try enabling AGP fastwrites and SBA:
[http://doc.gwos.org/index.php/Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing](http://doc.gwos.org/index.php/Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing)

---

### Post by linuxnoob40 on 2006-08-14
ok i followed your advice and did everything you said and the fps were slower than when i started.
now keeping in mind that fastwrites was enabled to begin with and sba was diabled... aftre removing that line i now have fastwrites disabled and sba enabled and fps worse than when i started.
how do i switch them back so that fastwrites is enabled and sba is disabled at least its tolerable that way =(

---

### Post by tseliot on 2006-08-14
remove the files and/or lines you added

---

### Post by linuxnoob40 on 2006-08-14
i did

---

### Post by tseliot on 2006-08-14
> **linuxnoob40 said:**
> i did

Log out and press CTRL+ALT+Backspace


then post the output of this:
```

cat /proc/driver/nvidia/agp/status
```

---

### Post by linuxnoob40 on 2006-08-14
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

---

### Post by tseliot on 2006-08-14
Are you sure that Fast writes was enabled and SBA disabled by default (and not viceversa)?

Anyhow, post the content of:

1) The Section Device of your /etc/X11/xorg.conf


2) /etc/modprobe.d/blacklist

3) /etc/modprobe.d/nvidia-kernel-nkc

---

### Post by linuxnoob40 on 2006-08-14
im relatively 99.8% positive 
here is the info
```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA geforce 7800 gs oc"
	Driver		"nvidia" 
	BusID		"PCI:1:0:0"
	VideoRam	262144
EndSection
```

Blacklist:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
# added in attempt to reneable agp
blacklist agpgart
blacklist nvidia_agp
```

```
alias char-major-195* nvidia
```

---

### Post by tseliot on 2006-08-15
> **linuxnoob40 said:**
> im relatively 99.8% positive 
here is the info
```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA geforce 7800 gs oc"
	Driver		"nvidia" 
	BusID		"PCI:1:0:0"
	VideoRam	262144
EndSection
```

Blacklist:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
# added in attempt to reneable agp
blacklist agpgart
blacklist nvidia_agp
```

```
alias char-major-195* nvidia
```
Everything but this is fine:
```
# added in attempt to reneable agp
blacklist agpgart
blacklist nvidia_agp
```

If you blacklist those modules and don't have NvAGP set to 1 in your xorg.conf you should get no agp at all (in theory).

In other words remove those lines and reboot

---

### Post by linuxnoob40 on 2006-08-15
ok i have removed those lines everything works but nothing has changed in other words, fastwrite still disabled, sba still enabled, frame rate still sucks. ](*,)   im ready to pull put my hair if i had any:p

---

### Post by tseliot on 2006-08-15
> **linuxnoob40 said:**
> ok i have removed those lines everything works but nothing has changed in other words, fastwrite still disabled, sba still enabled, frame rate still sucks. ](*,)   im ready to pull put my hair if i had any:p

The only thing I can do is suggesting you to ask for help here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

