---
title: "Help getting sound after install, esoniq 5880, running on 606 lts"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by stu01 on 2006-10-05
Hi all 

I am at a complete loss as to what to do here. I am a newbie to Linux having only installed for a few weeks and have been following the information from various websites to try and solve this problem myself ](*,) 

Anyway i have a soundblaster Esoniq 5880 sound card and I just can`t get sound to work. I have followed lord raidens tutorial as best I cn and still can`t get anything more than the system bleep 

Some details for you to look at  
lsmod gives me this 
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
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
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  4
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
lp                     11844  0
tsdev                   8000  0
snd_ens1371            24800  0
gameport               15496  1 snd_ens1371
snd_rawmidi            25504  1 snd_ens1371
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93216  1 snd_ens1371
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
cdc_ether               6016  0
usbnet                 17032  1 cdc_ether
snd_page_alloc         10632  1 snd_pcm
nvidia               3921884  0
floppy                 62148  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
snd_ac97_bus            2304  1 snd_ac97_codec
psmouse                36100  0
serio_raw               7300  0
rtc                    13492  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
amd_k7_agp              8588  1
agpgart                34888  2 nvidia,amd_k7_agp
ne2k_pci               10976  0
8390                   10496  1 ne2k_pci
i2c_amd756              6660  0
i2c_core               21904  2 i2c_acpi_ec,i2c_amd756
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ohci_hcd               21892  0
usbcore               130820  4 cdc_ether,usbnet,ohci_hcd
ide_cd                 33028  3
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  4
generic                 5124  0
amd74xx                15260  0 [permanent]
thermal                13576  0
processor              23360  1 thermal
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

lspci 
0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
0000:00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
0000:00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
0000:00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
0000:00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
0000:00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
0000:00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:01:05.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

SO linux sees my card but won`t let me config 

If I try and open alsamixer i get 
alsamixer: function snd_ctl_open failed for default: No such device

When I look for the sound drivers for my card which are ens-1371 modprobe says that they are not found 

Any help would be very helpfull

---

### Post by Zer0Nin3r on 2006-10-06
Try the following as it worked from me.  This came from another thread:

*******************************
Davilinux's Avatar  	
Davilinux Davilinux is offline
First Cup of Ubuntu
	  	
Join Date: Aug 2006
Location: Málaga, Spain
Beans: 1
Kubuntu 6.06 User
Lightbulb Re: Ensoniq 5880 No Sound
Hi all!!

Did you tried adding **"acpi=ht"** to your GRUB/LILO?

I was like you, trying to "hear something" from my box, but nothing at all, searching and testing all the answers I've found... until I made the next modification of GRUB (that I read about a shutdown problem):

(extract from my /boot/grub/menu.lst)

title Ubuntu, kernel 2.6.15-25-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash vga=788 **acpi=ht**
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot


... and now I can hear my music, videos, system sounds ... 


******************

If you need anymore help let me know.  Also, be sure to restart once you have made your changes.

---

