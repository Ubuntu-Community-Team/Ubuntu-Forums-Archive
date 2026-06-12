---
title: "no sound after dapper upgrade"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by Ben Branch on 2006-06-04
upgraded to dapper from breezy on a P4 laptop. onboard sound with
SiS7012 (according to alsamixer), but there's no sound at all. No drumroll,
no podcast, no audio CD, just zip. Programs *think* they are working, and
the volume function keys on the laptop work, but no sound comes out.

Never had any sound problems with breezy.

I've reinstalled the kernel, modules, and various alsa bits but all
to no avail. I've tried some of the remedies in other threads (check
that Master is on in alsamixer, etc.), but no luck.

Attached is my lsmod, and fragment of lscpi. Any suggestions?

Best Regards,
Ben

---

### Post by rbalfour on 2006-06-04
Check your user rights.

Add your username to the audio group.

---

### Post by Ben Branch on 2006-06-04
Checked that, I'm fine (audio is one of my group permissions). So
*that's* not it, sigh. Thanks anyway!

Ben

---

### Post by LordRaiden on 2006-06-04
Have you checked 'PCM' and 'DXS' values in alsamixer. 'PCM' should be above 70 and  all  'DXS' channels should be at 100.

If that is not the case , please give the output of ```
dmesg | grep snd
```

---

### Post by Ben Branch on 2006-06-04
Thanks in advance ...

Hmm ... let's see ... PCM is 100, but I don't see anything called DXS?!
Does this have some other name such as Surround Channel?

dmesg ... very interesting ... there is nothing in the output of dmesg
with the string 'snd' in it!!! lsmod grepping for snd shows,

```
snd_intel8x0           35740  0 
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0 
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96676  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
```

Just to be thorough, here's the last third of dmesg:

```
[4294675.903000] XFS mounting filesystem hda1
[4294675.903000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[4294675.904000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:03.2-1
[4294675.904000] usbcore: registered new driver usbhid
[4294675.904000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294676.018000] Ending clean XFS mount for filesystem: hda1
[4294676.026000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d53257033c1]
[4294688.619000] ts: Compaq touchscreen protocol output
[4294690.087000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.092000] agpgart: Detected SiS 648 chipset
[4294690.101000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294690.479000] sis900.c: v1.08.09 Sep. 19 2005
[4294690.480000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 217
[4294690.481000] 0000:00:04.0: VIA 6103 PHY transceiver found at address 1.
[4294690.493000] 0000:00:04.0: Using transceiver found at address 1 as default
[4294690.494000] eth0: SiS 900 PCI Fast Ethernet at 0xe800, IRQ 217, 00:03:0d:14:ea:0e.
[4294690.968000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.031000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.359000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa36eb3, caps: 0x904713/0x10008
[4294691.401000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294691.727000] i2c-sis96x version 1.0.0
[4294691.728000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[4294691.774000] input: PC Speaker as /class/input/input3
[4294691.877000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[4294691.877000] Yenta: CardBus bridge found at 0000:00:09.0 [1584:3005]
[4294691.877000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294691.877000] Yenta O2: enabling read prefetch/write burst
[4294691.936000] parport: PnPBIOS parport detected.
[4294691.936000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[4294691.999000] Yenta: ISA IRQ mask 0x0a38, PCI irq 169
[4294692.000000] Socket status: 30000006
[4294692.004000] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 169
[4294692.004000] Yenta: CardBus bridge found at 0000:00:09.1 [1584:3005]
[4294692.126000] Yenta: ISA IRQ mask 0x0a38, PCI irq 169
[4294692.127000] Socket status: 30000006
[4294692.346000] irda_init()
[4294692.346000] NET: Registered protocol family 23
[4294692.415000] NET: Registered protocol family 17
[4294692.453000] nsc_ircc_pnp_probe() : Found cfg_base 0x000 ; firbase 0x3F8 ; irq 4 ; dma 1.
[4294692.453000] nsc-ircc, Found chip at base=0x000
[4294692.453000] nsc-ircc, driver loaded (Dag Brattli)
[4294692.454000] IrDA: Registered device irda0
[4294692.454000] nsc-ircc, Found dongle: Supports SIR Mode only
[4294692.640000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 177
[4294693.095000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[4294693.099000] cs: IO port probe 0xc00-0xcf7: clean.
[4294693.099000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[4294693.102000] cs: IO port probe 0xc00-0xcf7: clean.
[4294693.103000] cs: IO port probe 0xa00-0xaff: clean.
[4294693.104000] cs: IO port probe 0xa00-0xaff: clean.
[4294693.452000] intel8x0_measure_ac97_clock: measured 50493 usecs
[4294693.452000] intel8x0: clocking to 48000
[4294693.699000] lp0: using parport0 (interrupt-driven).
[4294693.796000] SCSI subsystem initialized
[4294693.822000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294693.822000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294693.822000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294693.911000] Adding 3036244k swap on /dev/hda5.  Priority:-1 extents:1 across:3036244k
[4294694.213000] eth0: Media Link On 100mbps full-duplex 
[4294694.232000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.232000] md: bitmap version 4.39
[4294695.305000] cdrom: open failed.
[4294696.738000] ip_tables: (C) 2000-2002 Netfilter core team
[4294697.045000] ACPI: AC Adapter [AC0] (on-line)
[4294697.104000] ACPI: Battery Slot [BAT0] (battery present)
[4294697.190000] ACPI: Power Button (FF) [PWRF]
[4294697.190000] ACPI: Lid Switch [LID]
[4294697.190000] ACPI: Sleep Button (CM) [SLPB]
[4294697.190000] ACPI: Power Button (CM) [PWRB]
[4294697.397000] ibm_acpi: ec object not found
[4294697.432000] NET: Registered protocol family 10
[4294697.433000] lo: Disabled Privacy Extensions
[4294697.433000] IPv6 over IPv4 tunneling driver
[4294697.456000] pcc_acpi: loading...
[4294697.570000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294699.885000] serial8250: too much work for irq4
[4294701.641000] ppdev: user-space parallel port driver
[4294702.715000] [drm] Initialized drm 1.0.1 20051102
[4294702.734000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 225
[4294702.735000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294703.739000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294703.739000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[4294703.739000] agpgart: SiS delay workaround: giving bridge time to recover.
[4294703.750000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[4294704.083000] [drm] Setting GART location based on new memory map
[4294704.083000] [drm] Loading R300 Microcode
[4294704.083000] [drm] writeback test succeeded in 1 usecs
[4294708.011000] eth0: no IPv6 routers present
[4294713.644000] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available

```

---

### Post by deodatus on 2006-06-04
This is what I did to fix the same problem, I found something like this on a Fedora forum.
Open terminal:
#*sudo alsaconf*
follow instructions, then:
#*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted. 
Soooo... I hope this works for everyone.

---

### Post by arkTIK on 2006-06-04
The symptoms that I encountered on my XUBUNTU 6.06 installed on a Toshiba Satellite M50 were:
- playing mpeg files with XFMEDIA: movie works but NO sound
- playing mp3 files with XFMEDIA: NO sound
- playing mp3 files with XMMS: sound is OK
- also alarm/system sounds are OK

I was able to correct the sound-problem by using EasyUbuntu and install codecs for older files.

Regards
ark-TK
----- think non-thinking -----

---

### Post by Ben Branch on 2006-06-05
[QUOTE=deodatus]This is what I did to fix the same problem, I found something like this on a Fedora forum.
Open terminal:
#*sudo alsaconf*
follow instructions, then:
#*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted. 
Soooo... I hope this works for everyone.[/QUOTE]

Where did alsaconf come from? I can't find it either on my computer or
in any package recognized by synaptic.

I tried gst-register-0.8, but still no sound, even after reboot. To tell the
truth, I'm confused because the upgrade has left the gstreamer package
with a bunch of stuff labeled as -0.10 and a bunch as -0.8. In my experience
this usually indicates a two-versions-at-once problem, but I'm not an
expert here. (I even uninstalled the -0.8 codecs but that didn't help, so I
put them back). Even rebooted after *each* step, no joy.

Interesting point: I tried booting from a Knoppix live-cd from 2005,
and it saw and Intel 82440MX audio controller, module i810_audio ... but
*it* had no sound *either*!!!

Geeesh. At this rate I don't have any confidence that a fresh install would
work either, and I'd much rather not not not not not have to go through
reconfiguring a fresh install to my preferences again. Did that with Breezy,
and that was enough!!

---

### Post by Ben Branch on 2006-06-06
I am soooo embarrassed. well, maybe there was something wrong anyway,
which I fixed by following the various threads on this popular topic,
but my sound finally started working again when I (ahem) adjusted the
volume wheel on the side of my laptop. See, I've always used the mixers,
so I tend to forget that silly little wheel ...

never mind ...

Be

---

