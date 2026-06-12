---
title: "Feisty - Intel HDA (SigmaTel STAC9274D) LINE IN Not working"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Berto on 2007-04-27
Hi everyone!  I have Feisty with an Intel D975XBX2 motherboard, which has a SigmaTel STAC9274D audio chip on it.

I cannot get the Line In to work, even after enabling everything.  No audio comes out of the speakers.

Any help is appreciated.  I've attached tons of information for anyone who might have some ideas.  It's probably too much.

Thanks!!!
berto

aplay -l
[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/PHP]

lspci -v
[PHP]00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
        Subsystem: Intel Corporation Unknown device 5842
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 88000000-89ffffff
        Prefetchable memory behind bridge: 0000000080000000-0000000087ffffff
        Capabilities: [88] Subsystem: Intel Corporation Unknown device 0000
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Intel Corporation Unknown device 0419
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 8a200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0[/PHP]


lspci -nv
[PHP]00:00.0 0600: 8086:277c
        Subsystem: 8086:5842
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 0604: 8086:277d (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 88000000-89ffffff
        Prefetchable memory behind bridge: 0000000080000000-0000000087ffffff
        Capabilities: [88] Subsystem: 8086:0000
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1b.0 0403: 8086:27d8 (rev 01)
        Subsystem: 8086:0419
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 8a200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 0604: 8086:27d0 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 8a300000-8a3fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: 8086:27d0
        Capabilities: [a0] Power Management version 2

00:1c.4 0604: 8086:27e0 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 8a100000-8a1fffff
        Prefetchable memory behind bridge: 000000008a400000-000000008a4fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: 8086:27e0
        Capabilities: [a0] Power Management version 2

00:1c.5 0604: 8086:27e2 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 8a000000-8a0fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: 8086:27e2
        Capabilities: [a0] Power Management version 2

00:1d.0 0c03: 8086:27c8 (rev 01) (prog-if 00 [UHCI])
        Subsystem: 8086:5842
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 3080 [size=32]

00:1d.1 0c03: 8086:27c9 (rev 01) (prog-if 00 [UHCI])
        Subsystem: 8086:5842
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 3060 [size=32]

00:1d.2 0c03: 8086:27ca (rev 01) (prog-if 00 [UHCI])
        Subsystem: 8086:5842
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 3040 [size=32]

00:1d.3 0c03: 8086:27cb (rev 01) (prog-if 00 [UHCI])
        Subsystem: 8086:5842
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 3020 [size=32]

00:1d.7 0c03: 8086:27cc (rev 01) (prog-if 20 [EHCI])
        Subsystem: 8086:5842
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at 8a204400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 0604: 8086:244e (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        Capabilities: [50] Subsystem: 8086:5842

00:1f.0 0601: 8086:27b0 (rev 01)
        Subsystem: 8086:5842
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 0101: 8086:27df (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: 8086:5842
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 30b0 [size=16]

00:1f.2 0101: 8086:27c0 (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: 8086:5842
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 30c8 [size=8]
        I/O ports at 30e4 [size=4]
        I/O ports at 30c0 [size=8]
        I/O ports at 30e0 [size=4]
        I/O ports at 30a0 [size=16]
        Memory at 8a204000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [70] Power Management version 2

00:1f.3 0c05: 8086:27da (rev 01)
        Subsystem: 8086:5842
        Flags: medium devsel, IRQ 11
        I/O ports at 3000 [size=32]

01:00.0 0300: 10de:016a (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 89000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 80000000 (64-bit, prefetchable) [size=128M]
        Memory at 88000000 (64-bit, non-prefetchable) [size=16M]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

03:00.0 0106: 11ab:6145 (rev a1) (prog-if 8f)
        Subsystem: 11ab:6145
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 2018 [size=8]
        I/O ports at 2024 [size=4]
        I/O ports at 2010 [size=8]
        I/O ports at 2020 [size=4]
        I/O ports at 2000 [size=16]
        Memory at 8a100000 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at 8a400000 [disabled] [size=256K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

04:00.0 0200: 8086:109a
        Subsystem: 8086:30a5
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 8a000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 1000 [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0[/PHP]

lsmod:
[PHP]
bluetooth              62340  0
acpi_cpufreq           10760  1
cpufreq_userspace       6176  0
cpufreq_stats           8416  0
cpufreq_powersave       3072  0
cpufreq_ondemand       10640  2
freq_table              6336  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9736  0
tc1100_wmi              9224  0
pcc_acpi               15616  0
dev_acpi               17028  0
sony_acpi               7064  0
video                  19080  0
sbs                    17856  0
i2c_ec                  6784  1 sbs
dock                   11992  0
button                 10016  0
battery                12040  0
container               6144  0
ac                      6920  0
asus_acpi              19756  0
backlight               8448  1 asus_acpi
af_packet              27020  0
lp                     15048  0
snd_hda_intel          24224  9
snd_hda_codec         262912  1 snd_hda_intel
snd_pcm_oss            49536  0
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0
usbhid                 29088  0
hid                    34048  1 usbhid
snd_seq_oss            36608  0
snd_seq_midi           11008  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
xpad                   11272  0
nvidia               5659736  22
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  4 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                43536  0
i2c_core               26624  2 i2c_ec,nvidia
parport_pc             40104  1
parport                43404  2 lp,parport_pc
pcspkr                  4736  0
serio_raw               9092  0
snd                    68904  24 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
shpchp                 37404  0
pci_hotplug            36228  1 shpchp
ipv6                  307072  926
evdev                  13056  0
tsdev                  10112  0
ext3                  143760  4
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0
sd_mod                 25092  7
sr_mod                 18980  0
cdrom                  40744  1 sr_mod
ata_piix               18308  5
ata_generic            10628  0
e1000                 133824  0
ehci_hcd               37004  0
pata_marvell            9344  0
libata                137000  3 ata_piix,ata_generic,pata_marvell
scsi_mod              166968  4 sg,sd_mod,sr_mod,libata
generic                 6532  0 [permanent]
uhci_hcd               28320  0
usbcore               154416  5 usbhid,xpad,ehci_hcd,uhci_hcd
thermal                16912  0
processor              34952  2 acpi_cpufreq,thermal
fan                     6536  0
fbcon                  44416  0
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0
commoncap               9472  1 capability[/PHP]

Thanks again!
berto

---

### Post by Berto on 2008-01-04
Hi all,

I know this is old, but I'm still having this problem in 7.10.  Line In and Mic don't work.  Does anyone have any ideas?

From the alsa team, I found a program called aadebug which gives me this:

```

ALSA Audio Debug v0.1.0 - Fri Jan  4 18:15:56 PST 2008
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux destroyal 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel         337192  2
snd_pcm_oss            50048  0
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq_dummy           5380  0
snd_seq_oss            36864  0
snd_seq_midi           11008  0
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  13 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x8a300000 irq 22
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
cat: /proc/asound/hwdep: No such file or directory
00-01: STAC92xx Digital : STAC92xx Digital : playback 1
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2
Client info
  cur  clients : 3
  peak clients : 3
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  seq  timer

CPU -------------------------------------------------------
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
cpu MHz         : 1596.000
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
cpu MHz         : 1596.000

RAM -------------------------------------------------------
MemTotal:      2061512 kB
SwapTotal:     6024332 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub

```

---

### Post by Yellow Pasque on 2008-01-05
I would try OSSv4 (see link in my sig).

---

