---
title: "Intel 82801DB doesn't produce sound on Drake"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by Jhodytropical on 2006-06-28
Hi All,

 I upgrade to Drake 6.06 with  kernel 2.6.15-25-686  with version: 2.6.15-23.39. I am using a Gateway 7326GZ with the followings:
 Mobile Intel(R) Pentium(R) 4 CPU 3.06GHz - 512 RAM - etc.

 At first my Wireless did not work, but thanks to this thread : [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) the problem was solved. Now my big concern is the sound, I've read every where on the forum were a few other people have the same, I tried most of the idea(s) and nothing seems to work.

 I would really want to have sound. I am posting the info on my systems hoping someone can help.

Thanks in advance !!!


jean@jean-laptop:~$ dmesg |grep -e intel8x0 -e ICH4
[17179572.776000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[17179572.776000] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[17179574.964000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179574.964000] ICH4: chipset revision 3
[17179574.964000] ICH4: not 100% native mode: will probe irqs later
[17179588.388000] intel8x0_measure_ac97_clock: measured 58178 usecs
[17179588.388000] intel8x0: clocking to 48000


jean@jean-laptop:~$ lsmod |grep snd
snd_intel8x0           35708  1
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm


jean@jean-laptop:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <available only to root>

0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, fast devsel, latency 0

0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, fast devsel, latency 0, IRQ 193
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0380000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at eff0 [size=8]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0300000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at ef20 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at ef40 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at ef80 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 185
        Memory at e02ffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=05, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e0000000-e00fffff
        Prefetchable memory behind bridge: 20000000-22ffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Memory at 23000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at e400 [size=256]
        I/O ports at ee80 [size=64]
        Memory at e02ff800 (32-bit, non-prefetchable) [size=512]
        Memory at e02ff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Rioworks: Unknown device 202f
        Flags: medium devsel, IRQ 169
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <available only to root>

0000:01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff01
        Flags: bus master, medium devsel, latency 64, IRQ 193
        Memory at e00ff800 (32-bit, non-prefetchable) [size=2K]
        Memory at e00f8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Rioworks: Unknown device 202f
        Flags: bus master, medium devsel, latency 168, IRQ 169
        Memory at e0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 24000000-25fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

0000:01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Rioworks: Unknown device 2029
        Flags: bus master, fast devsel, latency 64, IRQ 201
        Memory at e00fc000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at 22000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Unknown device 17f9:0002
        Flags: bus master, fast devsel, latency 64, IRQ 177
        Memory at e00f6000 (32-bit, non-prefetchable) [size=8K]



jean@jean-laptop:~$ cat /proc/interrupts |grep -e Intel -e CMI
169:       9284          0   IO-APIC-level  Intel 82801DB-ICH4, yenta

jean@jean-laptop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [on] Capture [off]
  Front Right: Playback 31 [100%] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [on] Capture [on]
  Front Right: Playback 31 [100%] [on] Capture [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [on]
Simple mixer control 'Aux',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [off]
  Front Right: Capture 15 [100%] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


jean@jean-laptop:~$ cat /proc/devices |grep -e Character -e sound -e alsa -e Block -e sd
Character devices:
 14 sound
116 alsa
Block devices:
  8 sd
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd

---

### Post by LordRaiden on 2006-06-28
Check for it being muted. If its not muted then try ```
sudo modprobe snd-intel8x0
```

Try playing something and if it works add the line "snd-intel8x0" to /etc/modules to have it load on start up.

---

### Post by Jhodytropical on 2006-06-29
Hi Lord,

 Thanks for your help but I tried it and it didn't help. anything else you can think of ?

---

### Post by LordRaiden on 2006-06-29
Try my guide in my signature below.

---

### Post by Soarer on 2006-06-30
Hi LordRaiden,

Just to let you know, I have the same sound card. I used your guide as I was getting no sound from the mic in the new Skype Beta. Found the AlsaMixer part, turned up the mic & it all works. Even shares the output with AmaroK! Great stuff - thanks for writing it :)

---

### Post by Jhodytropical on 2006-06-30
Thanks Lord,

 My sound finally comes up. I went to alsamixer and I muted the  external Speaker and the sound works fine.

 People like you make us Beginners feel and experience Linux and make us realize  what a waste of time we spent on learning WINDOWS.

Thanks again.

---

### Post by skitzo on 2006-08-23
Same card... Muting the External Amplifier worked for me as well :D Thanks!

---

### Post by CassioBunana on 2006-08-25
Hi guys! I guess I've a very similar problem...few days ago the sound disappered from my laptop! I've the same optput diagnostic but:
andrea@cassioli:/proc/asound$ cat /proc/devices |grep -e Character -e sound -e alsa -e Block -e sd
Character devices:
 14 sound
116 alsa
Block devices:

The external amplifier is switch off...what should I do? I've already read the Comprehensive Sound Problems Solution Guide and tried to get brand new alsa sound modules...nothing helped! From the multimedia selector I get :" ALSA - Impossible to write on the resource"...any ideas?

---

### Post by hscottyh on 2006-10-27
> **Jhodytropical said:**
> Thanks Lord,

 My sound finally comes up. I went to alsamixer and I muted the  external Speaker and the sound works fine.

 People like you make us Beginners feel and experience Linux and make us realize  what a waste of time we spent on learning WINDOWS.

Thanks again.

A big thanks from me as well! That also done the trick for me with the same chipset.

---

