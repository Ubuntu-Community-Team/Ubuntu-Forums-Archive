---
title: "Midi Keyboard in Breezy"
date: 2005-12-25
forum: Multimedia &amp; Video
---

### Post by _axiom_ on 2005-12-25
Fixed below with this:


```
connect also the audio out of zynaddsubfx to alsa_pcm
you should use amidi
try amidi -l to see the devices
then amidi -d -p <device>
to dump midi incoming as hex bytes

```
----------------------------------------------------------------------------
I'm trying to use my midi keyboard in ZynAddSubFX (a thoughly awsome program), but I've yet to get any response with the actual midi keyboard. I can play it with the on screen keyboard, but that's only fun for a little bit. (I've also tried RoseGarden, Beast, Muse, and anything else I could apt-get. Same result.)

I've tried the HOWTO's around here and got my computer to play midi files, which is nice, but not what I need. In /dev, I have sequencer and sequencer2, both of which claim to be unavailable:

```
# tail -f /dev/sequencer
tail: error reading `/dev/sequencer': Resource temporarily unavailable
tail: tail.c:836: recheck: Assertion `valid_file_spec (f)' failed.
Aborted

```

The sound card supports midi stuff, I think. It's a SB Live! something-or-other. An lspci follows:

```
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 11)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
0000:02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:02:02.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:02:04.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

And an lsmod, just for the fun of it:

```

Module                  Size  Used by
radeon                 68352  1 
drm                    58004  2 radeon
binfmt_misc            10888  1 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0 
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  15 
af_packet              20232  2 
tsdev                   7616  0 
analog                 10528  0 
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
emu10k1_gp              3712  0 
gameport               14472  3 analog,emu10k1_gp
snd_emu10k1_synth       6528  0 
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0 
snd_seq_oss            29440  0 
snd_seq_midi            8608  0 
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  3 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  17 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd
tpm_atmel               5504  0 
tpm_nsc                 6528  0 
tpm                     9504  2 tpm_atmel,tpm_nsc
shpchp                 80612  0 
pci_hotplug            24628  1 shpchp
intel_agp              21276  1 
agpgart                32328  2 drm,intel_agp
reiserfs              217200  1 
dm_mod                 50364  1 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
usbhid                 30688  0 
8139too                23552  0 
8139cp                 18432  0 
mii                     5248  2 8139too,8139cp
ehci_hcd               29448  0 
uhci_hcd               28048  0 
usbcore               104188  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  5 
ide_generic             1664  0 
piix                    9476  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  623 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

And the /dev/sndstat:

```

$ cat /dev/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux axiom 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
SB Live 5.1 (rev.10, serial:0x80641102) at 0xa000, irq 23

Audio devices:
0: ADC Capture/Standard PCM Playback (DUPLEX)

Synth devices:
0: Emu10k1

Midi devices:
0: EMU10K1 MPU-401 (UART)

Timers:
7: system timer

Mixers:
0: eMicro 28028

```

Any advice to point me in the right direction would be greatly appreciated.

---

### Post by dolson on 2006-01-01
I don't understand what you did... Could you detail it more please?

---

### Post by stratotak on 2006-01-01
are you using jack??all i have to do is launch jack..then launch synth..then go to jack connections and connect my usb midi keyboard to synth and it works..

---

### Post by _axiom_ on 2006-01-01
Well, I don't really understand what I did either, but I am using jack.

I got help from someone at [http://www.agnula.org/](http://www.agnula.org/)

My synthaziser is working on a gnomish box, but I can't get it working on my kde (kubuntu) box, because libqt3c102-mt is tries to uninstall KDE.

More here:

[http://ubuntuforums.org/showthread.php?t=109369](http://ubuntuforums.org/showthread.php?t=109369)

---

### Post by dolson on 2006-01-02
I thought you were using the MIDI/gamepad port and not USB. I don't have a USB controller yet. I am waiting for it to arrive, but I don't think it supports Linux (E-MU Xboard 49). Which do you have?

But anyhow, I did manage to get it working. I tried out FluidSynth and ZynSubAddFX. I did use JACK. But I get a ton of XRUNs. Do you?

I'll probably try getting the DeMuDi kernel installed.

---

### Post by stratotak on 2006-01-02
getting alot of xrun errors??are you running jack in real time mode??when i ran it with out realtime it would kick out xrun errors..but with realtime enabled xrun errors are gone..had a hard time geting real time to compile under breezy..used module-assistant but it never would work..kept saying the source code couldnt be found even though it was in /usr/src...finally gave up.. Agnula works great for  sound and midi..thats  what im using now..dual booting Ubuntu and Agnula,,when i plug in my usb keyboard it just works..its a Edirol PCR-30...pretty decent midi controller ...

---

### Post by dolson on 2006-01-03
I've read bad things about the Edirol and M-Audio boards, so I stayed away from them.

I am not using Real Time yet. I had the module thing compiled before, but the XRUNs *only* are popping up whenever I click somewhere in the interface of Zyn.. Pretty strange. I will try out the module again soon. After I get my keyboard.

I tried out DeMuDi, but I didn't like it as much as Ubuntu. It's basically Debian with some fixed packages. I think Ubuntu could be so much more than this - right out of the box - if Mark ever gets back to me about it...

---

### Post by dolson on 2006-01-11
Just for anyone interested, I bought the E-MU Xboard 49, and IT WORKS IN LINUX!!! I didn't expect it to work, but IT DOES! I just plugged it in, checked in JACK, and it's there! I connected it to ZynAddSubFX, and BAM, instant music creation!

Unbelievable. Everywhere on the net that I could find said it did not work in Linux, but it does!

---

