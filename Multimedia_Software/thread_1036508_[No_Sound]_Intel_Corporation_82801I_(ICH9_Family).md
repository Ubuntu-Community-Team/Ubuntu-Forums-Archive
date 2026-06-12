---
title: "[No Sound] Intel Corporation 82801I (ICH9 Family)"
date: 2009-01-10
forum: Multimedia Software
---

### Post by kelbizzle on 2009-01-10
Could someone help me troubleshoot a sound issue?  Heres what I have done since a brand new install minutes ago. I've added ```
options snd-hda-intel enable_msi=1
``` to the end of ```
/etc/modprobe.d/alsa-base
```

I have a Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02). All the clues say it should be working. It's recognized in lspci, lshw -c multimedia shows the card and it seems as if the modules are loaded. I have a theory on what might be happening. I think it's playing the audio through the digital out. but I have no way of testing the digital out.
Here are the three outputs:
```
kel@Bizzle-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series
04:00.0 Communication controller: Conexant Systems, Inc. Device 2f82

```

```
kel@Bizzle-PC:~$ sudo lshw -c multimedia
[sudo] password for kel: 
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia UNCLAIMED
       description: Multimedia controller
       product: XCode 2100 Series
       vendor: ViXS Systems, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

```
kel@Bizzle-PC:~$ sudo lsmod
Module                  Size  Used by
ipv6                  263972  14 
af_packet              25728  2 
binfmt_misc            16904  1 
i915                   38144  2 
drm                    86056  3 i915
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  3 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
container              11520  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
sbshc                  13440  1 sbs
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
evdev                  17696  6 
lirc_mceusb2           20228  0 
lirc_dev               20020  1 lirc_mceusb2
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
psmouse                45200  0 
pcspkr                 10624  0 
serio_raw              13444  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
button                 14224  0 
shpchp                 37908  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
libusual               27156  1 usb_storage
ata_piix               24580  2 
usbhid                 35840  0 
hid                    50560  1 usbhid
pata_acpi              12160  0 
ohci1394               37936  0 
3c59x                  48936  0 
mii                    13440  1 3c59x
ieee1394               96324  2 sbp2,ohci1394
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
r8169                  35972  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  7 lirc_mceusb2,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by r0tu on 2009-01-11
I have the same issue.  I'll keep you posted on my results.  

What system are you installing this on? I just got myself an Aspire 8930G

---

### Post by r0tu on 2009-01-11
Found your troubleshooting here:... still looking.


 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)

---

### Post by Timmy81 on 2009-01-20
I just tried the following on my Aspire 8930G...Kubuntu 8.10

Edit/reduce alsa-base (the last few lines beginning "options...") to just this:

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto 

and reboot...

Sound works beautifully... hope this helps...

EDIT: alsa-base lies in /etc/modprobe.d/alsa-base
just type *sudo pico /etc/modprobe.d/alda-base*

---

### Post by kelbizzle on 2009-01-20
Were you guys having the same issue as me? Where gnome-sound-preferences will test the digital audio but not the analog?

---

### Post by Sabnil on 2009-08-30
> **r0tu said:**
> I have the same issue.  I'll keep you posted on my results.  

What system are you installing this on? I just got myself an Aspire 8930G

did you ever get that fixed? i have aspire 8930 too and no luck getting my sound working. i'm on ubuntu. if you got it fixed then i am very interested in how D:

---

### Post by Nonexistent on 2009-10-04
> **Timmy81 said:**
> Edit/reduce alsa-base (the last few lines beginning "options...") to just this:

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto 


It works for my Acer 8930g, Kubuntu 9.04. Thanks!

---

### Post by erikmy on 2011-01-02
> **Timmy81 said:**
> I just tried the following on my Aspire 8930G...Kubuntu 8.10

Edit/reduce alsa-base (the last few lines beginning "options...") to just this:

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto 

and reboot...

Sound works beautifully... hope this helps...

EDIT: alsa-base lies in /etc/modprobe.d/alsa-base
just type *sudo pico /etc/modprobe.d/alda-base*

This seems to have fixed my issue with dissappearing sound on a Lenovo Ideapd Netbook too. Thanks alot!

Just a little question: Isn't it supposed to be a dash in the first line?;
*options snd**[COLOR=red]-[/COLOR]**slots=snd-hda-intel*

Don't want to be ungreatful, but stuff like that seems to be important when editing config-files etc..

Anyways: Thanks again!! Saved my day :)

---

### Post by naviathan on 2011-07-30
The option is passed to the snd module so no, there is not suppose to be a "-" between snd and slots.

---

### Post by asiersanmi on 2012-06-22
> **Timmy81 said:**
> I just tried the following on my Aspire 8930G...Kubuntu 8.10

Edit/reduce alsa-base (the last few lines beginning "options...") to just this:

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto 

and reboot...

Sound works beautifully... hope this helps...

EDIT: alsa-base lies in /etc/modprobe.d/alsa-base
just type *sudo pico /etc/modprobe.d/alda-base*

Thanks you so much, it has worked to me 3 years later!!!!

---

### Post by Takehaniyasubiko on 2012-10-21
> **asiersanmi said:**
> Thanks you so much, it has worked to me 3 years later!!!!
Same here. I upgraded from 12.04 to 12.10 and my audio went to hell. I was starting to get nervous with "fixes" that didn't work at all, but here I found myself, taking this old fix - it works like a charm! 

THANK YOU!

---

### Post by wildmanne39 on 2012-10-21
Old thread closed.

---

