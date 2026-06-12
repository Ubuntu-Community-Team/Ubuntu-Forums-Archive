---
title: "Sound worked yesterday, but not today"
date: 2008-12-20
forum: Multimedia Software
---

### Post by rudeboyskunk on 2008-12-20
Yesterday sound worked perfectly.  I talked on Skype, watched a movie, listened to some music, etc.  Today, I only get sound through my headphones.  And because I've had sound issues before, I can tell you YES, I have indeed done everything in the "Comprehensive Sound Problems Solution Guide."  When I do sudo modprobe snd-intel8x0, I still get no sound.  I've changed everything in System>Preferences>Sound to everything else, and tried it all, it still only works with headphones (if it works at all).  Nothing is muted, I've quadruple-checked that.  It's a laptop, so, yes, the speakers are attached, unless they've somehow come unattached inside (if that's even possible).  Both Master and PCM are enabled.  My laptop is a DELL Latitude D610.  I'm running 8.10.  My soundcard is an ICH6.

Here is output from lsmod:

```
rudeboyskunk@kimchi:~$ lsmod
Module                  Size  Used by
af_packet              25728  6 
binfmt_misc            16904  1 
ipv6                  263972  14 
ppdev                  15620  0 
speedstep_centrino     15360  0 
cpufreq_ondemand       14988  1 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
gspca_zc3xx            55936  0 
gspca_main             29312  1 gspca_zc3xx
videodev               41344  1 gspca_main
v4l1_compat            22404  1 videodev
lp                     17156  0 
joydev                 18368  0 
pcmcia                 43052  0 
dcdbas                 15008  0 
evdev                  17696  14 
serio_raw              13444  0 
psmouse                45200  0 
pcspkr                 10624  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
video                  25104  0 
output                 11008  1 video
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_dummy          10884  0 
ipw2200               151244  0 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
ieee80211              38088  1 ipw2200
ieee80211_crypt        13572  1 ieee80211
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            38528  0 
fglrx                1813960  23 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 14224  0 
battery                18436  0 
ac                     12292  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
intel_agp              33724  0 
agpgart                42184  2 fglrx,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
pata_acpi              12160  0 
ahci                   37132  0 
sg                     39732  0 
usb_storage            81728  1 
libusual               27156  1 usb_storage
ata_piix               24580  2 
ata_generic            12932  0 
libata                177312  4 pata_acpi,ahci,ata_piix,ata_generic
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
ehci_hcd               43276  0 
tg3                   129924  0 
uhci_hcd               30736  0 
libphy                 27392  1 tg3
usbcore               148848  7 gspca_zc3xx,gspca_main,usb_storage,libusual,ehci_hcd,uhci_hcd
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fuse                   60828  5 
vesafb                 13828  1 
fbcon                  47648  72 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Here's lspci:

```
rudeboyskunk@kimchi:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

---

### Post by rudeboyskunk on 2008-12-21
*bump*  Still no sound. . .  I'm almost to the point of doing a clean install of 8.04, with which at least I never had any problems.

---

### Post by Monotoko on 2008-12-21
I cant help you, id just like to say that im also having the same problem and had to revert back to 8.04, at first my sound was horribly grainy and then after a few days it stopped working altogether, so i think its something which the developers have done somewhere....

---

### Post by Amof on 2008-12-21
Well from the looks of it Ubuntu see the card and it useing it properly. Have you tried killing Pulseaudio? just type "sudo pkill pulseaudio" into your terminal. It's kinda a shot in the dark. Also, are you sure that you have the speakers turned up in the alsamixer? Some program could have just muted them on you and you don't have the channel showing in the gnome mixer.

---

### Post by Oxidize on 2008-12-22
I have a issue like this, sound worked fine for a while then just stopped.
Had a speaker icon on the screen flashing on and on persistantly, reinstalled the OS since and the issue still persists.
I can hear sound if i pull the volume bar up but the bar instantly drags its self back down so im stumped at what to to.

---

### Post by rudeboyskunk on 2008-12-24
My proposed solution of re-installing 8.04 didn't bring the sound back.  I'm beginning to think it's a hardware problem, though the only evidence I have of that is that absolutely nothing I do is bringing back my sound.  Is it possible to buy replacement internal speakers for a laptop?  It's been hard finding them through Google.

---

### Post by linux_tech on 2008-12-24
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer
```

To open gnome-alsamixer type
```
gnome-alsamixer
```

check all settings, make sure nothing is muted

To open volume control type:
```

gnome-volume-control
```

---

### Post by caro on 2008-12-24
I have a Dell 1505 laptop  with 8.10 and had the exact same problem.  Yesterday everything worked fine, but today I can't play music on Rhythmbox or get any audio on any web app.  I've never had sound problems before, so i am just now researching them.  Suggestions would be appreciated!

Update:
The info in this post fixed the problem for me. 
[http://ubuntuforums.org/showthread.php?t=1004657]("http://ubuntuforums.org/showthread.php?t=1004657")

---

### Post by parminides on 2008-12-30
I am having the same problem, too. Someone please help!

---

### Post by IQRules on 2008-12-30
Try this,

~$ sudo alsa force-reload

---

### Post by zezerbing on 2008-12-30
I know I'm a nube. But mine does that when my computer goes into sleep mode or shuts down. I restart the system and then it work again. I don't know why

---

