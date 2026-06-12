---
title: "Sound problem with Asus ROG Supreme-fx"
date: 2015-01-23
forum: Multimedia Software
---

### Post by N94 on 2015-01-23
Hello
i have a very bad sound with ROG suprême-fx, help me please  

**lspci -v:**

00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 8602
        Flags: bus master, fast devsel, latency 0, IRQ 34
        Memory at f7930000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

**cat /proc/asound/version**

Advanced Linux Sound Architecture Driver Version 1.0.21.

**head -n 1 /proc/asound/card*/codec#***

==> /proc/asound/card0/codec#0 <==
Codec: Intel Haswell HDMI

==> /proc/asound/card1/codec#0 <==
Codec: Realtek ALC1150

==> /proc/asound/card2/codec#0 <==
Codec: Nvidia GPU 60 HDMI/DP

[SIZE=4][COLOR=#b22222]_**i have use this solution but it s no good:**_[/COLOR][/SIZE]

vi /etc/modprobe.d/dist-alsa.conf

# ALSA Sound Support
#
# We want to ensure that snd-seq is always loaded for those who want to use
# the sequencer interface, but we can't do this automatically through udev
# at the moment...so we have this rule (just for the moment).
#
# Remove the following line if you don't want the sequencer.

install snd-pcm /sbin/modprobe --ignore-install snd-pcm && /sbin/modprobe snd-seq
[COLOR=#b22222]**options snd-hda-intel model=6stack-dig**[/COLOR]
[B][COLOR=#000000]
Can you help me please? [/COLOR][/B]
~

---

### Post by Yellow Pasque on 2015-01-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421)


> Advanced Linux Sound Architecture Driver Version 1.0.21.
That's ancient. I have no idea how you got that, but you should undo your previous "fixes" before trying the workaround in the link above. If you're really running that old of an Ubuntu version, then try a newer version.

---

