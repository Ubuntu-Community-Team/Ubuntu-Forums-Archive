---
title: "Lost sound, only noise"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by marianom on 2006-10-13
My sound was working ok since the day I installed Ubuntu. 
Due to an error in Skype, I tried every option you can find in the "Comprehensive Sound Problem Solutions Guide" ([http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)).
Yesterday, after doing a lot of changes I cannot now recall and rebooting the machine several times all was ok (my skype issue was still there but I least I could listen music).

This morning when I restarted the pc my sound was totally dead. I only hear this "beat" every 3 seconds with some white noise behind. If I go to System-Preferences-Sound I can see that my Via 8237 as the default soundcard but I log into alsamixer, mute everything and this "beat" is still there.
I rebooted with the LiveCD and the "beat" is still there and no other sound.

If somebody can suggest a way to fix this, I will totally appreciate it.


Some output from my system.

```

mariano@mishima:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: V8237 [VIA 8237], dispositivo 0: VIA 8237 [VIA 8237]
  Subdispositivos: 4/4
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
tarjeta 0: V8237 [VIA 8237], dispositivo 1: VIA 8237 [VIA 8237]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

```

mariano@mishima:~$ sudo lspci -v
 ...
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 0430
        Flags: medium devsel, IRQ 201
        I/O ports at c400 [size=256]
        Capabilities: [c0] Power Management version 2
 ...

```

```

mariano@mishima:~$ lsmod | grep snd
snd_seq_oss            34816  0
snd_seq_midi            8992  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                52048  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            29464  1
gameport               15496  1 snd_via82xx
snd_ac97_codec         96804  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            47648  0
snd_mixer_oss          18816  1 snd_pcm_oss
snd_pcm                81032  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              24964  2 snd_seq,snd_pcm
snd_page_alloc         10760  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8704  1 snd_via82xx
snd_rawmidi            25376  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8460  4 snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    56164  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd

```

---

### Post by marianom on 2006-10-13
I realize I've an additional question:

could it be possible that there's a hardware issue? I suppose this since with Live CD I got the same error. ¿Does the Live CD use its own set of audio configuration? If so it shouldn't get the same error of the installed version (assuming the installed version conf is messed up).

What do you guys suggest?

Thanks and regards.

---

### Post by marianom on 2006-10-13
In case somebody need it:
Fixed. I uninstalled every piece of soft sound related I could found and installed all over again. Reboot the machine and the sound is here again.

---

