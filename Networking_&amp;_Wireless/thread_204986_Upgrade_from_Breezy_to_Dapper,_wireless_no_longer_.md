---
title: "Upgrade from Breezy to Dapper, wireless no longer functioning."
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by Schuler on 2006-06-27
Same old thing.  Ndiswrapper says it's there and working, but the lights on my card aren't on and it's not detected by anything else.  Here's some info.

Here's the entry on it on the ndiswrapper wiki-
> #  Laptop: Dell Inspiron 5150 Card: Wireless 1350 (802.11b/g) WLAN miniPCI Card

    * Chipset: Broadcom Corporation BCM#4306 802.11b/g Wireless LAN Controller (rev 03)
    * pciid: ?
    * Driver: [ftp://ftp.us.dell.com/network/R83097.EXE](ftp://ftp.us.dell.com/network/R83097.EXE)
    * Other: This card is in the miniPCI slot of the Inspiron 5150. This driver is for US only. I think this is a Truemobile 1350. To install unzip (program "unzip" works on the .exe) the exe file and use the bcmwl5a.inf in directory AR. 


Here's my lsmod output-
> Module                  Size  Used by
ehci_hcd               34184  0
ndiswrapper           177364  0
isofs                  37688  1
udf                    88452  0
nls_cp437               5888  2
ntfs                  103536  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
ipv6                  265728  6
speedstep_ich           5260  0
speedstep_lib           4484  1 speedstep_ich
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_ich,cpufreq_stats
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
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
bcm43xx               124044  0
ieee80211softmac       29696  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6272  1 ieee80211
pcmcia                 40508  0
joydev                 10048  0
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
yenta_socket           28428  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
tsdev                   8000  0
b44                    25740  0
mii                     5888  1 b44
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
hw_random               5652  0
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
serio_raw               7300  0
pcspkr                  2180  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
psmouse                36100  0
nvidia               4550772  0
i2c_core               21904  2 i2c_acpi_ec,nvidia
rtc                    13492  0
intel_agp              22940  1
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
agpgart                34888  2 nvidia,intel_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33680  0
usbcore               130692  4 ehci_hcd,ndiswrapper,uhci_hcd
ide_disk               17664  4
ide_cd                 33028  1
cdrom                  38560  2 sr_mod,ide_cd
piix                   11012  1
generic                 5124  0
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


---

### Post by GTvulse on 2006-06-27
You listing shows that the bcm43xx module is loaded at boot up time, therefore there is a conflict. You could either:

1. Blacklist the bcm43xx module. Create a file in /etc/modprobe.d with whatever name fits your mind and add the line:
```
blacklist bcm43xx
```
or,
2. Remove the ndis driver and test the native GPL driver to see if it works with your card (IMO, I'd try this first). Make sure you are not loading ndsiwrapper in /etc/modules (or make sure it is loading if you want to use the ndis driver instead, this could be the solution to your problem).

---

### Post by Schuler on 2006-06-27
Thanks, I used the blacklist method and it's working fine now.

---

