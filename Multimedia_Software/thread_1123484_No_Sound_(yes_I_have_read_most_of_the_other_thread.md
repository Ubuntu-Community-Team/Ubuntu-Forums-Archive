---
title: "No Sound (yes I have read most of the other threads)"
date: 2009-04-12
forum: Multimedia Software
---

### Post by Jakey_TheSnake on 2009-04-12
Thanks for reading =) 

Well, my sound used to work fine, but suddenly it didn't. I don't recall doing anything major to my system before it broke, so meh. 

Firstly, output from several commands: 

```
jake@jake-desktop:~$ aplay -l
aplay: device_list:207: no soundcards found...

```

Bummer. 

```
jake@jake-desktop:~$ sudo lspci -v


00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7290
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 12
	I/O ports at cc00 [size=256]
	I/O ports at c000 [size=128]
	Memory at d4080000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel modules: snd-intel8x0

```

I've tried reinstalling the alsa drivers, but don't know what to do now. Presumably edit my /etc/modprobe.d/alsa-base file somehow? 

Oh, I almost forgot:

```
jake@jake-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

Looking for a Ubuntu sound-nerd to become my new best friend! 

Thanks in advance, 

- Jake


edit2: ```
jake@jake-desktop:~$ sudo modprobe snd-intel8x0 
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.27-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Edit3: Then when I run "dmesg" I get lots of random crap, but the important bit is here: 

```
[ 2165.386197] snd_intel8x0: Unknown symbol snd_ac97_pcm_close
[ 2165.386418] snd_intel8x0: Unknown symbol snd_ac97_resume
[ 2165.388290] snd_intel8x0: Unknown symbol snd_ac97_pcm_open
[ 2165.388523] snd_intel8x0: Unknown symbol snd_ac97_set_rate
[ 2165.388641] snd_intel8x0: Unknown symbol snd_ac97_update_bits
[ 2165.388767] snd_intel8x0: Unknown symbol snd_ac97_mixer
[ 2165.388931] snd_intel8x0: Unknown symbol snd_ac97_bus
[ 2165.391801] snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
[ 2165.391939] snd_intel8x0: Unknown symbol snd_ac97_update_power
[ 2165.392162] snd_intel8x0: Unknown symbol snd_ac97_suspend
[ 2165.393103] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
[ 2165.393400] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
[ 2165.394112] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware

```

---

### Post by Jakey_TheSnake on 2009-04-12
Right, well, I got it working again, thanks for the help guys :roll: 

For anyone else that had this problem, I used this: 

> Refreshing/Reinstalling the drivers

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. If this is the case, you can purge your custom changes, and restore your system to a clean base. This may clear up your problem, and restore you to a working state.

Open a terminal and type sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2. This will purge any custom configurations that you've made, and any hand-compiled modules that you've built, and restore your sound stack to the "Official" Ubuntu core. You can also do this as two separate steps: sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils and then sudo apt-get install linux-sound-base alsa-base alsa-utils , but this may result in some other packages which depend on the sound-base and alsa-utils from being removed, such as gdm and ubuntu-desktop. If this happens, then do sudo apt-get install gdm ubuntu-desktop 

From: 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Also, 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338)

can be quite helpful.

---

