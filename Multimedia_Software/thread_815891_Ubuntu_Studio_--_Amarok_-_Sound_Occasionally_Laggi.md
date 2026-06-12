---
title: "Ubuntu Studio -- Amarok - Sound Occasionally Lagging/Skipping (Read for more details)"
date: 2008-06-02
forum: Multimedia Software
---

### Post by Adreniline on 2008-06-02
In 7.10 Amarok ran fine, no problems at all.

In 8.04, I reinstalled (now running Ubuntu Studio) - and reinstalled Amarok.

Before I go further, it is worth noting that I have 2 GB of Ram, and deleted the Swap File when I switched to Ubuntu Studio (to my knowledge, whenever I checked the Swap File in 7.10, it was never used).

Now onto the problem.

Amarok will play fine for usually about a minute, and then will lag for half a second, and play fast (not quite fast forwarding) for a second until it catches up with where it's supposed to be on the song.  Needless to say, this is quite annoying as it does this about every minute or so, regardless of the song format being played.
  -The song isn't skipping, but merely lagging behind for half a second, then trying to catch up to where it's supposed to be.

When using Movie Player to watch videos, no sound problems have been experienced.  I did not run into any sound problems when using Audacious either, I have only encountered these problems in Amarok.

Occasionally, the boot-up sound will skip when playing, but it's not the same kind of distortion.

Any help would be much appreciated.

Thank You,

  -Adreniline

---

### Post by Ashrael on 2008-06-02
what kernel are you using? uname -r?


see what we can do...

---

### Post by Adreniline on 2008-06-02
Did you mean enter 'uname -r' in a Terminal?

I did that and it says:
2.6.24-17-rt

If that's not what you meant, could you please explain a little more what I was supposed to do?

Thanks,

  -Adreniline

---

### Post by Ashrael on 2008-06-03
yes, that's what i meant. so, you are using the RT kernel. 
Can you give me more details about your hardware? 
what motherboard / chipset / videocard / soundcard etc...
Aslo give output of (terminal) lspci  and  lsusb  and lsmod, to start with.
see what we can do for ya!

---

### Post by Adreniline on 2008-06-03
I'm using a Dell e1505 (Laptop) with 2GB Ram and a Core Duo.  AtI Radeon X1400, Sigmatel (is the soundcard).

Here it goes:

lspci
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)


lsusb
> 
Bus 005 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  



lsmod
> 
Module                  Size  Used by
rfkill_input            5760  0 
ipv6                  275108  10 
snd_rtctimer            4640  1 
binfmt_misc            13320  1 
rfcomm                 43280  2 
l2cap                  25984  13 rfcomm
bluetooth              62564  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10924  1 
cpufreq_conservative     8840  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7360  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5760  0 
dock                   11564  0 
sbs                    15368  0 
sbshc                   7808  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16644  1 ip_tables
af_packet              24196  2 
ndiswrapper           197928  0 
sbp2                   24456  0 
parport_pc             36516  0 
lp                     13252  0 
parport                38600  3 ppdev,parport_pc,lp
loop                   19460  0 
snd_hda_intel         344728  2 
arc4                    2944  2 
ecb                     4480  2 
snd_pcm_oss            42400  0 
blkcipher               8580  1 ecb
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78724  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
b43                   115232  0 
snd_seq_dummy           4868  0 
rfkill                  8848  3 rfkill_input,b43
mac80211              168212  1 b43
cfg80211               15368  1 mac80211
led_class               6148  1 b43
input_polldev           5896  1 b43
snd_seq_oss            35968  0 
snd_seq_midi            9376  0 
fglrx                1557932  23 
video                  19984  0 
output                  4736  1 video
ricoh_mmc               4480  0 
sdhci                  19204  0 
joydev                 13248  0 
mmc_core               52228  1 sdhci
battery                14596  0 
wmi_acer                9772  0 
snd_rawmidi            25632  1 snd_seq_midi
button                  9232  0 
ac                      7044  0 
serio_raw               7940  0 
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54992  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57636  17 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                41104  0 
dcdbas                  9504  0 
iTCO_wdt               13524  0 
evdev                  13312  9 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
soundcore               9312  1 snd
shpchp                 34708  0 
pci_hotplug            31776  1 shpchp
intel_agp              25492  0 
agpgart                34900  2 fglrx,intel_agp
ext3                  137480  1 
jbd                    49044  1 ext3
mbcache                 9856  1 ext3
sg                     36624  0 
sr_mod                 18084  0 
cdrom                  37152  1 sr_mod
sd_mod                 31232  2 
ata_generic             8452  0 
usbhid                 32256  0 
hid                    38912  1 usbhid
b44                    28560  0 
mii                     6400  1 b44
ata_piix               19716  1 
ssb                    32644  2 b43,b44
ohci1394               34096  0 
ieee1394               95544  2 sbp2,ohci1394
pata_acpi               8320  0 
uhci_hcd               26896  0 
libata                159984  3 ata_generic,ata_piix,pata_acpi
ehci_hcd               37644  0 
usbcore               146924  5 ndiswrapper,usbhid,uhci_hcd,ehci_hcd
scsi_mod              153196  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                16924  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fuse                   51604  1 



---

### Post by Ashrael on 2008-06-04
I remember something being wrong or problematic about the intel sound driver and IHC7.
The fastest way to solve your probs is to look at the next posts. Maybe you can fix it with these:

[http://ubuntuforums.org/showthread.php?t=731106&highlight=00%3A1b.0+Audio+device%3A+Intel+Corporation+82801G+%28ICH7+Family%29+High+Definition+Controller+%28rev+01%29](http://ubuntuforums.org/showthread.php?t=731106&highlight=00%3A1b.0+Audio+device%3A+Intel+Corporation+82801G+%28ICH7+Family%29+High+Definition+Controller+%28rev+01%29)

and

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and

[http://ubuntuforums.org/showthread.php?t=616845&highlight=snd+hda+intel](http://ubuntuforums.org/showthread.php?t=616845&highlight=snd+hda+intel)

and

[http://ubuntuforums.org/showthread.php?t=780961&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=780961&highlight=snd_hda_intel)

If this is too much for you, just tell... we will try and help you on.. 

Another option is to ditch the onboard sound and put in a cheap pci soundblaster for 20 bucks or so.. Works out of the box, with usualy better latency then an onboard card..

Keep us posted..

---

