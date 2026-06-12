---
title: "Sound working some time, some others doesn't"
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by Cloud[01] on 2006-02-24
As from the topic title.
The sound of my ubuntu server (which I use as a music server, attached to my amplifier and all the speakers in my house) sometime works, some other doesn't.

This is the error I receive when trying for example mpg321 foo.mp3 (I'm sshd to it, as it doesn't have any input or screen attached):

```

cloud@musicserver:~$ mpg321 foo.mp3
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
No default libao driver available.

```

When it does work (after three or four reboots, for example) mpg321 plays flawlessy :) ...

But keep rebooting it's not a great thing to do.

Is this an hardware problem (I should change my soundcard) or something else?

By the way, running Breezy (edited, sorry), 2.6.12-10-386.

---

### Post by Cloud[01] on 2006-02-25
lspci give me this:
```

0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)

```

while dmesg (when the card does not work) give me this
```

[4294703.551000] ALSA /home/cloud/alsa-driver-1.0.10/pci/../alsa-kernel/pci/via82xx.c:583: codec_read: codec 0 is not valid [0x1fc0000]
[4294703.557000] ALSA /home/cloud/alsa-driver-1.0.10/pci/../alsa-kernel/pci/via82xx.c:583: codec_read: codec 0 is not valid [0x1fe0000]
[4294703.559000] ALSA /home/cloud/alsa-driver-1.0.10/pci/../alsa-kernel/pci/via82xx.c:526: codec_ready: codec 0 is not ready [0x1000000]
[4294703.560000] ALSA /home/cloud/alsa-driver-1.0.10/pci/../alsa-kernel/pci/via82xx.c:526: codec_ready: codec 0 is not ready [0x1000000]
[4294704.067000] ALSA /home/cloud/alsa-driver-1.0.10/pci/../alsa-kernel/pci/via82xx.c:583: codec_read: codec 0 is not valid [0x1fc0000]
[4294704.073000] ALSA /home/cloud/alsa-driver-1.0.10/pci/../alsa-kernel/pci/via82xx.c:583: codec_read: codec 0 is not valid [0x1fe0000]
[4294704.073000] ALSA /home/cloud/alsa-driver-1.0.10/pci/ac97/ac97_codec.c:1943: AC'97 0 access is not valid [0xffffffff], removing mixer.
[4294704.073000] ACPI: PCI interrupt for device 0000:00:07.5 disabled
[4294704.073000] VIA 82xx Audio: probe of 0000:00:07.5 failed with error -5

```

Drivers are the latest (stable) compiled by me.
BTW, the card worked yesterday with these drivers, today it's again dead.

I've done a reboot, and now it works fine.

WHAT CAN I DO?

Cloud

---

### Post by gregh on 2006-02-26
This is an ongoing problem I have had since hoary, I have a builtin AC97 based card inside a Toshiba A70 laptop, sometimes sound works and for no reason, after a reboot, it stops working.

The dmesg error is "atiixp: codec acquire timeout" repeated many times until it says "AC'97 2 does not respond - RESET" and finally "atiixp: no codec available"

I used to fix it by adding "snd_atiixp" and "snd_atiixp_modem" into the hotplug blacklists, and loading "snd_atiixp" in the /etc/modules but even that does not work with Dapper.

I know this does not help you, but maye together we can find out why ALSA and AC97 have so many problems.

-Greg

---

### Post by littlemanthim on 2008-04-11
Out of curiosity, has anyone gotten any further on this issue?  I've had this issue on my Toshiba A75 laptop since Fiesty, and I've tried many different things in an attempt to fix it... I'm beginning to wonder if it's possible to fix.

---

