---
title: "EMU support is broken in 2.6.32.23 kernel"
date: 2010-07-14
forum: Multimedia Software
---

### Post by ap1 on 2010-07-14
I recently updated kernel version from 2.6.32.22 to 2.6.32.23

I have EMU 0404USB audio card. It worked well with 2.6.32.22 kernel after I installed
linux-backports-modules-alsa-2.6.32-22-generic package. 

Now, after kernel upgrade (and yes, I installed linux-backports-modules-alsa-2.6.32-23-generic package) any attempt to connect EMU card results in system hung. 

Here is what I see in /var/adm/messages:

```
Jul 14 22:04:04 king kernel: [   70.976026] usb 1-8: new high speed USB device using ehci_hcd and address 10
Jul 14 22:04:04 king kernel: [   71.109936] usb 1-8: configuration #1 chosen from 1 choice
Jul 14 22:04:04 king kernel: [   71.111618] ALSA pcm.c:174: 10:1:1: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.111866] ALSA pcm.c:174: 10:1:2: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.112126] ALSA pcm.c:174: 10:1:3: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.112373] ALSA pcm.c:174: 10:1:4: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.112620] ALSA pcm.c:174: 10:1:5: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.112869] ALSA pcm.c:174: 10:1:6: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.113122] ALSA pcm.c:174: 10:1:7: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.113369] ALSA pcm.c:174: 10:1:8: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.113619] ALSA pcm.c:174: 10:1:9: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.113868] ALSA pcm.c:174: 10:1:10: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.114117] ALSA pcm.c:174: 10:1:11: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.114367] ALSA pcm.c:174: 10:1:12: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.114620] ALSA pcm.c:174: 10:1:13: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.116308] ALSA pcm.c:174: 10:1:14: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.116660] ALSA pcm.c:174: 10:1:15: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.116876] ALSA pcm.c:174: 10:1:16: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.117286] ALSA pcm.c:174: 10:1:17: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.117621] ALSA pcm.c:174: 10:1:18: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.120792] ALSA pcm.c:174: 10:2:1: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.120999] ALSA pcm.c:174: 10:2:2: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.121247] ALSA pcm.c:174: 10:2:3: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.121494] ALSA pcm.c:174: 10:2:4: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.121869] ALSA pcm.c:174: 10:2:5: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.122117] ALSA pcm.c:174: 10:2:6: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.122493] ALSA pcm.c:174: 10:2:7: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.122744] ALSA pcm.c:174: 10:2:8: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.123122] ALSA pcm.c:174: 10:2:9: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.123520] ALSA pcm.c:174: 10:2:10: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.123874] ALSA pcm.c:174: 10:2:11: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.124449] ALSA pcm.c:174: 10:2:12: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.124882] ALSA pcm.c:174: 10:2:13: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.125242] ALSA pcm.c:174: 10:2:14: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.125620] ALSA pcm.c:174: 10:2:15: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:04 king kernel: [   71.125992] ALSA pcm.c:174: 10:2:16: endpoint lacks sample rate attribute bit, cannot set.
Jul 14 22:04:13 king kernel: [   79.804532] ata1: lost interrupt (Status 0x58)
Jul 14 22:04:13 king kernel: [   79.896033] sr 0:0:1:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Jul 14 22:04:13 king kernel: [   79.949996] ata1: soft resetting link
Jul 14 22:04:14 king kernel: [   80.308819] ata1.00: configured for UDMA/33
Jul 14 22:04:14 king kernel: [   80.344787] ata1.01: configured for UDMA/66
Jul 14 22:04:14 king kernel: [   80.411342] ata1: EH complete
Jul 14 22:04:21 king kernel: [   87.804546] ata1: lost interrupt (Status 0x58)
Jul 14 22:04:21 king kernel: [   87.895893] sr 0:0:1:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Jul 14 22:04:21 king kernel: [   87.949419] ata1: soft resetting link
Jul 14 22:04:22 king kernel: [   88.324789] ata1.00: configured for UDMA/33
Jul 14 22:04:22 king kernel: [   88.356820] ata1.01: configured for UDMA/66
Jul 14 22:04:22 king kernel: [   88.411140] ata1: EH complete
Jul 14 22:04:52 king kernel: [  118.804531] ata1: lost interrupt (Status 0x58)
Jul 14 22:04:52 king kernel: [  118.894700] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Jul 14 22:04:52 king kernel: [  118.932493] ata1: soft resetting link
Jul 14 22:04:53 king kernel: [  119.296739] ata1.00: configured for UDMA/33
Jul 14 22:04:53 king kernel: [  119.328769] ata1.01: configured for UDMA/66
Jul 14 22:04:53 king kernel: [  119.330210] ata1: EH complete



```With older kernel I get:

```
Jul 14 22:23:15 king kernel: [  300.588030] usb 1-7: new high speed USB device using ehci_hcd and address 10
Jul 14 22:23:16 king kernel: [  300.721796] usb 1-7: configuration #1 chosen from 1 choice
Jul 14 22:23:40 king pulseaudio[2286]: ratelimit.c: 15 events suppressed
Jul 14 22:25:41 king pulseaudio[2781]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Jul 14 22:27:01 king pulseaudio[3370]: pid.c: Stale PID file, overwriting.
Jul 14 22:27:12 king pulseaudio[3456]: pid.c: Stale PID file, overwriting.
Jul 14 22:27:13 king pulseaudio[3456]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Jul 14 22:27:25 king pulseaudio[3370]: ratelimit.c: 1 events suppressed
Jul 14 22:27:28 king pulseaudio[3639]: pid.c: Stale PID file, overwriting.
Jul 14 22:27:48 king pulseaudio[3639]: ratelimit.c: 1 events suppressed
Jul 14 22:27:55 king pulseaudio[3639]: ratelimit.c: 6 events suppressed
Jul 14 22:28:16 king pulseaudio[3827]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Jul 14 22:32:10 king pulseaudio[4327]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Jul 14 22:33:11 king pulseaudio[4441]: ratelimit.c: 4 events suppressed

```

---

