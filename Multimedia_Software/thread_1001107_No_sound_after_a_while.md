---
title: "No sound after a while"
date: 2008-12-03
forum: Multimedia Software
---

### Post by Farajamo on 2008-12-03
Hi all,

Since upgrading from 8.04 to 8.10, sound stops working after a while. The issue was not present in 8.04.

Steps to reproduce for me are:
1) Boot Ubuntu
2) Open rhythmbox and play some mp3s - everything works fine
3) Stop music
4) Go to school
5) Come back home, press the play button on rhythmbox and the application freezes completely.
6) Watching Youtube videos have no sound either, and the videos hang after 2 seconds.
7) Going to System>Preferences>Sound and clicking on Sound Playback "Test" hangs for a while and then shows "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Timeout"

Notes:
I have never seen the sound stop working while I was using the computer, so maybe it is related to the screensaver or some power management process. I haven't found any workaround to fix the issue, besides rebooting the computer.

Please find below some information that I hope could help resolve the issue. Please let me know if you need anything else.

Thanks!

```
arian@arian-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
03:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

```

```
arian@arian-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  2 
binfmt_misc            16904  1 
sco                    18308  2 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
vboxdrv                71576  0 
ipv6                  263972  12 
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
coretemp               14080  0 
w83627ehf              27144  0 
hwmon_vid              11264  1 w83627ehf
lp                     17156  0 
snd_hda_intel         381488  5 
snd_pcm_oss            46848  0 
joydev                 18368  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
serio_raw              13444  0 
snd_rawmidi            29824  1 snd_seq_midi
pcspkr                 10624  0 
evdev                  17696  8 
psmouse                45200  0 
nvidia               6900560  38 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               18596  0 
i2c_core               31892  1 nvidia
iTCO_vendor_support    11652  1 iTCO_wdt
parport_pc             39204  1 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
snd                    63268  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  1 
libusual               27156  1 usb_storage
sd_mod                 42264  5 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
usbhid                 35840  1 
hid                    50560  1 usbhid
ata_piix               24580  2 
libata                177312  3 pata_acpi,ata_generic,ata_piix
ehci_hcd               43276  0 
scsi_mod              155212  5 usb_storage,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
usbcore               148848  7 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
e1000e                112680  0 
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
```

---

### Post by Farajamo on 2008-12-08
Anyone think they know a solution or could redirect me to where one is? It's becoming a nuisance.

---

### Post by Farajamo on 2008-12-22
I'm attempting not to bump this too often. If someone has a fix that would be awesome, thanks.

---

### Post by Cracauer on 2008-12-22
Can't tell you what causes it, but you get can your sound back without rebooting by unloading and reloading the kernel module that contains the driver. Several modules in the stack might have to be cycled.

---

### Post by mastergoomba on 2008-12-23
where do you find that? i'm having kind of the same problem, but mine says couldn't stop playback.

---

### Post by Farajamo on 2008-12-23
> **Cracauer said:**
> Can't tell you what causes it, but you get can your sound back without rebooting by unloading and reloading the kernel module that contains the driver. Several modules in the stack might have to be cycled.

Hmm, I'm afraid I have no idea how to do that. Could you explain how to do it?  I'm still a novice as far as linux goes, sorry.

---

### Post by Cracauer on 2008-12-23
You do `rmmod` on all modules that have snd_ at the beginning of their name. There might be sound modules that don't have that naming convention but are in the stack. It will say "no can do, module is busy" if you try to remove a module lower in the stack than one that's still loaded. In that case you consult `lsmod` to find out who's using what.

Then, you try to play a sound and see whether they are automatically reloaded. If not, manually `modprobe` all modules you nuked.

How far down the stack you have to go I can't tell you. After removing something just give it a shot until you thing the sucker that was screwed up.

---

### Post by jjarrettc on 2008-12-27
I have the same hardware and have the same issue.  Sounds works for a while, then stops.  I have to reboot to fix it.  It does not really matter what sound app I use.  If I am in and out of sound apps, sound eventually stops working.

I will try to troubleshoot further and share my steps.

John

---

### Post by Cracauer on 2008-12-27
Reloading modules will almost certainly fix the problem.

---

