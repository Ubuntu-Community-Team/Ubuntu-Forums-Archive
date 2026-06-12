---
title: "AC'97 Audio Controller (rev 02) Solution"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by c8h10n4o2 on 2007-07-18
All,

I've been working on this one all day and finally fixed it so I want to share the solution. Ignore the smilies as I don't have time to turn them off. You will still get the point.

[SIZE="5"][COLOR="Red"]Problem: Somewhere in me screwing around I killed my sound. The speaker by the clock had a red x on it. When I opened KMIX, it listed Current Mixer as null.[/COLOR][/SIZE]

Commands I tried & results:
**lspci**
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

**lspci -v**
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 0603
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

**cat /proc/asound/cards**
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with STAC9758,59 at 0xe0000c00, irq 16
**cat /proc/asound/modules**
 0 snd_intel8x0


**lsmod | grep snd**
snd_intel8x0           34332  0
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
...

**aplay**
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
...

[COLOR="Green"][SIZE="5"]SOLUTION
I found out that screwing around yesterday, I removed myself from all groups. In order to have sound, you MUST be a member of the **audio** group!!!!
[/SIZE][/COLOR]Thus:

**sudo vi /etc/group**
at the end of the line that starts with audio, add your username after the **:**
EX: **audio:x:29:c8h10n4o2**
Then log out and log back in !

---

