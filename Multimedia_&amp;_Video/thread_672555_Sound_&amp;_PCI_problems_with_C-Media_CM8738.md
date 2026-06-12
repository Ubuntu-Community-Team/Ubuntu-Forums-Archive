---
title: "Sound &amp; PCI problems with C-Media CM8738"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by v4169sgr on 2008-01-19
Ubuntu 6.04 32bit user running kernel 2.6.15-51-k7

Intermittent issue with sound out of C-Media card: sound can be crackly, or applications can hang with repeating sounds.

Recent onset on well-maintained system with no provious history of issues.

Grep for PCI in /var/log/syslog gives:

```
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Using ACPI for IRQ rout
ing
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: If a device doesn't wor
k, try "pci=routeirq".  If it helps, post a report
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Cannot allocate resourc
e region 1 of device 0000:07:09.0
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Cannot allocate resourc
e region 0 of device 0000:07:09.0
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Cannot allocate resourc
e region 3 of device 0000:07:09.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:01.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:02.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.1
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.2
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.3
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:13.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Error while updating re
gion 0000:07:09.0/0 (fbe00006 != 00000011)
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Error while updating re
gion 0000:07:09.0/3 (fbe00100 != 00000110)
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Error while updating re
gion 0000:07:09.0/1 (0000e001 != 02100011)
```

This only appears in some boots, and not others, where it will cause the Num Lock key to light on the keyboard, and the keyboard becomes inactive [forcing a reboot]. Sound problems may exist without the above appearing.

The above messages have only recently appeared too [~ past two weeks].

lspci output for the PCI code affected gives:

```
lspci | grep "0000:07:09.0"
0000:07:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

i.e. the sound card.


QUESTION: Is this a hardware or software issue? Is it time to clean and reseat the cards / buy a new sound card / boot with noacpi / change some config somewhere / file a bug?

Many thanks in advance for your answers!

---

### Post by v4169sgr on 2008-01-19
Should add that apparently the PCI errors above do not necessarily correlate with the keyboard problem.

---

### Post by xeth_delta on 2008-01-19
> **v4169sgr said:**
> Ubuntu 6.04 32bit user running kernel 2.6.15-51-k7

Intermittent issue with sound out of C-Media card: sound can be crackly, or applications can hang with repeating sounds.

Recent onset on well-maintained system with no provious history of issues.

Grep for PCI in /var/log/syslog gives:

```
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Using ACPI for IRQ rout
ing
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: If a device doesn't wor
k, try "pci=routeirq".  If it helps, post a report
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Cannot allocate resourc
e region 1 of device 0000:07:09.0
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Cannot allocate resourc
e region 0 of device 0000:07:09.0
Jan 19 12:11:38 localhost kernel: [17179571.836000] PCI: Cannot allocate resourc
e region 3 of device 0000:07:09.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:01.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:02.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.1
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.2
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:03.3
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Bridge: 0000:00:13.0
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Error while updating re
gion 0000:07:09.0/0 (fbe00006 != 00000011)
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Error while updating re
gion 0000:07:09.0/3 (fbe00100 != 00000110)
Jan 19 12:11:38 localhost kernel: [17179571.860000] PCI: Error while updating re
gion 0000:07:09.0/1 (0000e001 != 02100011)
```

This only appears in some boots, and not others, where it will cause the Num Lock key to light on the keyboard, and the keyboard becomes inactive [forcing a reboot]. Sound problems may exist without the above appearing.

The above messages have only recently appeared too [~ past two weeks].

lspci output for the PCI code affected gives:

```
lspci | grep "0000:07:09.0"
0000:07:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

i.e. the sound card.


QUESTION: Is this a hardware or software issue? Is it time to clean and reseat the cards / buy a new sound card / boot with noacpi / change some config somewhere / file a bug?

Many thanks in advance for your answers!

Can you please post your "/etc/modprobe.d/alsa-base"?

---

### Post by v4169sgr on 2008-01-20
Thanks in advance!


```
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

```


Please remember this system has been working well until recently.

---

### Post by v4169sgr on 2008-01-20
Well, I've been cleaning and reseating both the C-Media card and the RAM, and have been putting the  machine through it's [very noisy!!] paces. Not much wrong so far. Will keep an eye on it and will revisit this thread if the need arises.

:guitar:

---

