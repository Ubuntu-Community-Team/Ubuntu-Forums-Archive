---
title: "[SOLVED] ndiswrapper Help"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by ToyotaGuy23 on 2008-12-08
Hey all,

I need help getting my wireless to work through ndiswrapper.  

My system:
Dell Inspiron 1721 17"
2.0 Ghz AMD TL-60
2 GB DDR2
250 GB HDD
Broadcom 440x 10/100 network controller
Dell 1505 WLAN mini card (802.11n draft) 
Ubuntu 8.10 Intrepid 32 bit OS

I am coming to you now through a wired connection, but really need my wireless to work.  

Thanks in advance.

---

### Post by spcwingo on 2008-12-08
We need a little more info on your card, so open a terminal and type:

```
lspci
```

If it's a USB model open a terminal and type:

```
lsusb
```

Then copy and paste the results in your next post.

---

### Post by ToyotaGuy23 on 2008-12-08
> **spcwingo said:**
> We need a little more info on your card, so open a terminal and type:

```
lspci
```

If it's a USB model open a terminal and type:

```
lsusb
```

Then copy and paste the results in your next post.

Sure thing.  
Terminal says: 

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by spcwingo on 2008-12-08
Open synaptic and search for ndisgtk and install it.  Next download the windows driver files from here:

[http://myspamb8.googlepages.com/R151517-pruned.zip]("http://myspamb8.googlepages.com/R151517-pruned.zip")

Extract the zip file.  Run ndisgtk from system>admin>windows wireless drivers.  Choose new driver.  Select the previously extracted .inf file.  By then you should be rockin-n-rollin wirelessly.\\:D/

Most of the info above was pulled from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver")

---

### Post by ToyotaGuy23 on 2008-12-08
OK, I've done what you said, and still have no wireless.

Out of pure curiosity, what does sudo ndiswrapper -l mean?
what would happen if you ran that?
if it disables ndiswrapper, how can you re-enable it?

---

### Post by spcwingo on 2008-12-09
ndiswrapper -l would list currently installed drivers.  I just noticed that you are running 8.10.  In 8.10 (I'm running 8.04) I believe that you should have an option to install and/or enable the driver in system>admin>hardware drivers.  Give that a shot if you haven't already and let me know how it turns out.

---

### Post by ToyotaGuy23 on 2008-12-09
That shows two drivers.

One (active) called wl
One (inactive) called ATI graphics

---

### Post by caljohnsmith on 2008-12-09
How about posting the output of:
```
ndiswrapper -l
iwconfig
lsmod
```
Also, where did you get the Windows wireless driver you are using with your wireless card? Is it for XP or Vista, and is it 32 bit or 64 bit? Since your wireless card has a Broadcom chipset, you will most likely have to "blacklist" the native broadcom drivers in Intrepid so you can use ndiswrapper instead, but first post the above commands so we can see what is loaded.

---

### Post by Ayuthia on 2008-12-09
Have you tried using the wl (Broadcom STA) driver?  It seems to work with some of the 4328 drivers:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```
This will remove all the possible wireless drivers and use the wl driver.  It will then scan for wireless sites.  If it finds some, then the card is working with it.

If you want to try out ndiswrapper (this is assuming that you have already installed ndiswrapper and have loaded the Windows driver):
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```

If one of the options work, please let us know which one worked and we can tell you how to make it permanent.  You have a Broadcom wired driver also so you will need to have a script to allow you to be able to use your wireless or wired card.

---

### Post by ToyotaGuy23 on 2008-12-09
> **caljohnsmith said:**
> How about posting the output of:
```
ndiswrapper -l
iwconfig
lsmod
```
Also, where did you get the Windows wireless driver you are using with your wireless card? Is it for XP or Vista, and is it 32 bit or 64 bit? Since your wireless card has a Broadcom chipset, you will most likely have to "blacklist" the native broadcom drivers in Intrepid so you can use ndiswrapper instead, but first post the above commands so we can see what is loaded.

[B]Sure thing.

ndiswrapper -l says:[/B]

bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)

[B]iwconfig says:
[/B]
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

**lsmod says:**
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
container              11520  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
dcdbas                 15008  0 
psmouse                45200  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
serio_raw              13444  0 
evdev                  17696  13 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ricoh_mmc              11904  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12416  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
uvcvideo               62728  0 
i2c_piix4              16144  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
i2c_core               31892  1 i2c_piix4
video                  25104  0 
output                 11008  1 video
ndiswrapper           196380  0 
battery                18436  0 
wmi                    14504  0 
ati_agp                14988  0 
button                 14224  0 
ac                     12292  0 
agpgart                42184  2 drm,ati_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
pata_acpi              12160  0 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
sg                     39732  0 
ohci1394               37936  0 
b44                    35984  0 
mii                    13440  1 b44
ieee1394               96324  2 sbp2,ohci1394
pata_atiixp            12800  0 
ehci_hcd               43276  0 
ohci_hcd               31888  0 
usbcore               148848  5 uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd
ahci                   37132  2 
libata                177312  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ssb                    40580  1 b44
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

How does this look?
Oh, I got the driver from post #4 in this very thread ^^^ =)
Which OS is it for?  No idea, to be honest.

---

### Post by Ayuthia on 2008-12-09
> **ToyotaGuy23 said:**
> [B]Sure thing.

ndiswrapper -l says:[/B]

bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)

[B]iwconfig says:
[/B]
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

**lsmod says:**
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
container              11520  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
dcdbas                 15008  0 
psmouse                45200  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
serio_raw              13444  0 
evdev                  17696  13 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ricoh_mmc              11904  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12416  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
uvcvideo               62728  0 
i2c_piix4              16144  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
i2c_core               31892  1 i2c_piix4
video                  25104  0 
output                 11008  1 video
ndiswrapper           196380  0 
battery                18436  0 
wmi                    14504  0 
ati_agp                14988  0 
button                 14224  0 
ac                     12292  0 
agpgart                42184  2 drm,ati_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
pata_acpi              12160  0 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
sg                     39732  0 
ohci1394               37936  0 
b44                    35984  0 
mii                    13440  1 b44
ieee1394               96324  2 sbp2,ohci1394
pata_atiixp            12800  0 
ehci_hcd               43276  0 
ohci_hcd               31888  0 
usbcore               148848  5 uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd
ahci                   37132  2 
libata                177312  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ssb                    40580  1 b44
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

How does this look?
Oh, I got the driver from post #4 in this very thread ^^^ =)
Which OS is it for?  No idea, to be honest.

Please try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```It looks like the ssb module for the wired card is blocking out ndiswrapper.  These commands will remove the conflicting modules and the load the necessary ones in the right order, then it will restart your networking, and scan for wireless sites.

---

### Post by ToyotaGuy23 on 2008-12-09
And now, coming to you from Ubuntu 8.10 

WIRELESSLY!
 
Thanks to everyone for your help!

Now... will these changes be permanent??
If not, what should I do.  

Other thoughts:  It shows me connected at 802.11g, which should be 802.11n speeds.  I won't complain, I'm just curious to learn why.

---

### Post by Ayuthia on 2008-12-09
Enter the following in the Terminal:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```

This will add a line in /etc/modprobe.d/ndiswrapper that should back out the modules and reload them in the correct order.

As for the speed, it might be because of the selected driver.  I am not for sure about what that driver supports.  If that driver does not support 802.11n, then it does not use it.

---

