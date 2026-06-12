---
title: "No Sound"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by boodle_bug on 2006-06-03
I need a little help... I'm in year 8 and my dad recommended I start using Linux because the programs are free. I have figured out how to use alot of the programs and i am fairly confident using it but I can't figure out how to get my sound working. On windows my sound was working fine. The speakers are inbuilt in the computer, its a compaq deskpro and the information on the computer says "DPENS-P400/6 4/N4 AUST COMPAQ SERIAL NO.: H930 CBP4 0714" Can anyone help? :confused:

---

### Post by deodatus on 2006-06-04
Open terminal(gnome-terminal)type:
*sudo alsaconf*
follow instructions, then:
*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted.
If that doesn't help sorry:(

---

### Post by Osamabingandhi on 2006-06-05
try to dubbelclick on the speakersymbol on the panel and turn every bar up. Could be that easy :)

---

### Post by ktulu1115 on 2006-06-05
[QUOTE=deodatus]Open terminal(gnome-terminal)type:
*sudo alsaconf*
follow instructions, then:
*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted.
If that doesn't help sorry:([/QUOTE]
Not sure about you, but alsaconf isn't included in the version of ALSA contained in Dapper to the best of my knowledge.

boodle_bug:
Try checking the information provided by these commands:
lspci
cat /proc/asound/cards
aplay /dev/urandom
alsamixer
lsmod

---

### Post by phpmonkey on 2006-06-06
Hmmm, I'm also having similar problems.

Sound was working fine 'til I upgraded to 6.06 LTS.

Thanks in advance if you can help :)

Here's my info:
lspci
```
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 945G Integrated Graphics Controller (rev 02)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 01)

```

cat /proc/asound/cards
> 0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xe04c0000 irq 225


aplay /dev/urandom
```
Playing raw data '/dev/urandom' : Unsigned 8 bit, Rate 8000 Hz, Mono

```

alsamixer
[everything on maximum, nothing on mute]

lsmod
```
Module                  Size  Used by
ppp_deflate             6272  0
zlib_deflate           24344  1 ppp_deflate
bsd_comp                6272  0
ppp_async              11904  1
crc_ccitt               2304  1 ppp_async
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
i915                   20608  1
drm                    73236  2 i915
ppdev                   9220  0
acpi_cpufreq            6792  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 acpi_cpufreq,cpufreq_stats
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
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265600  15
ppp_generic            30100  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7424  1 ppp_generic
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
tsdev                   8000  0
floppy                 62148  0
tg3                   102020  0
usbhid                 38368  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
psmouse                36228  0
snd_hda_intel          18964  9
snd_hda_codec         142640  1 snd_hda_intel
rtc                    13492  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  4 snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
snd                    55268  20 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
evdev                   9856  1
sg                     37920  0
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  3
ata_piix               11012  5
libata                 78992  1 ata_piix
scsi_mod              139496  3 sg,sd_mod,libata
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 acpi_cpufreq,thermal
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

```


Cheers! :0)

---

### Post by Burkey on 2006-06-06
Same here.. no sound out my speakers.. however! I can get sound out the headphone socket (if I make sure the "headphone" option is ticked)

I also read that you need 1.0.11 alsa drivers for it to work, I have installed that as per the instructions on [www.asla-project.org](www.asla-project.org) but still have the same problems... though I am not 100% sure my install process was correct for Dapper (no errors, but no improvement too)

---

### Post by th3gh05t on 2006-06-06
phpmonkey: I also do not have any sound, but sound was working fine w/ Breezy. And, I also have the HDA Intel on-board sound card.

[Here is my related thread.]("http://ubuntuforums.org/showthread.php?t=186914")

Regards, th3gh05t

---

### Post by gnurf on 2006-06-06
Same thing for me. I have a Intel 82801CA/CAM AC97 card.

Is this reported as a bug?

---

### Post by spotman on 2006-06-10
same here, thinkpad t60..

Right now I am preparing to compile a kernel without dappers alsa, and I will then build alsa separately.... 

I have also tried all of the above.. what is weird is that I can get microphone feedback (high pitched noise) if I turn my mic volume up all the way, but not for the life of me can I get either the headphones or speakers to play any sort of audio file.....

---

### Post by phpmonkey on 2006-06-18
:KS Good news! The new updated kernel fixed all!

And now that I have it, it's better than I had in 5.10... I can now use the socket at the front as well as the back, and I can now play the onboard sound too!

:-({|=

---

### Post by machalla on 2006-06-18
This is probably an aside but it may be useful to some.

I was having a problem with the front headphones.  My system uses HDA Intel.

Under windows you can swap the headphones and microphone speakers around as it asks you everytime you plug in earphones.  I had working earphones under windows with this but not with ubuntu.  After this latest kernel update I just swapped the socket the earphones are plugged into from the one marked as earphones to the mic socket and now it works fine :)

My onboard sound, speakers and headphones all appear to work together now after the kernel upgrade as the previous poster stated.

It might just be that simple.

---

