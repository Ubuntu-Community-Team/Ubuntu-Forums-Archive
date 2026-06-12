---
title: "No sound on Dapper Drake"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by unclescotty on 2006-07-24
Hi,

I've installed Ubuntu's Dapper Drake and can't get any sound from the sound card, which is HDA NVidia. What to do? I am a new user.

Here is the output of lspci:

scottspiegler@cuatro:~$ lspci
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00: 00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

Here is the output of lsmod 

scottspiegler@cuatro:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
binfmt_misc            12296  1
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
ipv6                  265728  6
ppdev                   9220  0
powernow_k8            12680  1
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
sr_mod                 16932  0
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0
pcspkr                  2180  0
rtc                    13492  0
tsdev                   8000  0
psmouse                36100  0
serio_raw               7300  0
usblp                  13056  0
nvidia               4550772  0
agpgart                34888  1 nvidia
usbhid                 39904  0
snd_hda_intel          18964  4
snd_hda_codec         153776  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  3 snd_pcm_oss
snd_pcm                89864  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
usb_storage            74176  1
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  3 snd
af_packet              22920  2
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
i2c_core               21904  2 i2c_acpi_ec,nvidia
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sg                     37920  0
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  6 usblp,usbhid,usb_storage,ehci_hcd,ohci_hcd
forcedeth              30732  0
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
generic                 5124  0
sd_mod                 19984  5
amd74xx                15260  0 [permanent]
sata_nv                 9732  6
libata                 78992  1 sata_nv
scsi_mod              139496  5 sr_mod,usb_storage,sg,sd_mod,libata
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

---

### Post by twotonz on 2006-07-24
Hallo,
Which sound server are you useing, alsa or open? Maybee you just need to activate the proper server, oh, and check the volumes on the mixer.

Love & Peace (to all)
anthony

---

### Post by unclescotty on 2006-07-25
I tried both. Also, hhow do you check the volumes on the mixer?

Thanks, Scott

---

### Post by unclescotty on 2006-07-25
BTW, is ALSA the right one to use? How do you get into the the mixer?

---

### Post by twotonz on 2006-07-25
Hi,
Alsa is the best bet. The mixer you have to install, for example "gnome alsa mixer" which can also be used under kde.

Love & Peace
anthony

EDIT*******
Please see next post from me below......

---

### Post by BerlinOliver on 2006-07-26
Hi,

I have the same audio device. lsmod gives out:

0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)

I also have audio problems. But I figuered out, we have to use the nvsound module and OSS (Open Sound System).

nvsound you can install via the CD-ROM which you received with your motherboard. You need to have the kernel sources and the corresponding headers installed. than the auto-installer from nvidia works fine. 

My problem is to switch to OSS and get nvsound as the default module loaded. Perhaps anybody here can explain how to do that...

---

### Post by twotonz on 2006-07-27
Hi,
Berlinoliver, now you have got me confused, I also have an onboard nvidia chip. Sound is the one thing that I have no problems with (as long as I remember to put up the volume after installing) I am not at home right now, but I shall have to have a look if I have nvsound installed, I am pretty sure not, to be quite honest, didn't even know it existed! What I am sure of though, is that I use "Alsa  Sound Server" so whatever problem you were having, it doesn't apply to all cases. Just thought I would point that out.

Love & Peace (to all)
anthony

UPDATE***********
OK, just had a peek (back at home now). Just as I thought, no sign of nvsound, my sound chip is using a load of snd_stuff to run it. One thing though, and now it is going to get embarrasing, two of the drivers I have loaded is snd_pcm_oss & snd_mixer_oss, which I guess means that I am running open & not alsa! :oops:  So I guess, that, BerlinOliver I owe you an appology, looks like you are correct with the oss/alsa thing.

---

### Post by twotonz on 2006-07-27
#Unclescotty,
I compared my working setup with yours.....
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

To me it looks fine (only difference is the codec, but that is proberly because I have an AC5 card & you have stereo (?))

So I am staying with the mixer therory. Right click on your task-bar, & look for something like add applet/add program, and then look for the audio mixer. 
Add it, check that pcm, master, cd, video are all turned up. (by default, most sliders are at zero)

Love & Peace (to all)
anthony

---

### Post by twotonz on 2006-07-27
And me again,
Sorry for hogging this thread here.....
#BerlinOliver, to get special drivers loaded you have to add the driver that you want loaded in /etc/modprobe.d/options. In order for the new driver to load, you have to make sure all other (sound) drivers are first removed 
sudo rmmod "thedriverthathastogo"
But please check this before you do anything (perhaps look in the wiki -replacing drivers)
So now I shall shut up, and give others a chance.

P.S (ooppps)
ermm BerlinOliver, do you live in Berlin, de by any chance?

anthony

---

### Post by twotonz on 2006-08-01
Hi all,
So ok I am breaking my own rule, but it seems that this thread has died, so here goes......
#BerlinOliver
So I have now sent you two emails & a pm. I am not ignoring you, something has gone wrong, please check your mails.

Love & Peace
anthony

---

