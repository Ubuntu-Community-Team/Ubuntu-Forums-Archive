---
title: "&quot;Unknown symbol in module&quot; errors with Alsa"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by greybirds on 2006-11-29
The past several months sound would sometimes just stop and refuse to work until reboot. Mild annoyance, nothing big. Two days ago it stopped again but rebooting didn't help. aplay -l returned ```
aplay: device_list:221: no soundcard found...
```.

I've tried the [Comprehensive Sound Problem thread]("http://www.ubuntuforums.org/showthread.php?t=205449"); purging/reinstalling linux-sound-base, alsa-base, alsa-utils, libasound2; tried compiling and installing alsa from both repository and (I know I'm a moron) alsa's released source; tried purging/reinstalling every sound- or kernel-related package I laid hands on. I managed to get to the point where gnome-settings-daemon and gnome-panel were cyling crashes and bug reports and where aplay -l was reporting core dumps, then managed to get it back to a stable desktop with no identified sound cards.

I'm now receiving this error when trying to modprobe (both sound cards return similar errors): ```
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.17-10-386/kernel/sound/core/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.17-10-386/kernel/sound/core/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.17-10-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.17-10-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.17-10-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_au8820 (/lib/modules/2.6.17-10-386/kernel/sound/pci/au88x0/snd-au8820.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

I'm obviously going about this the wrong way and apparently have bits and pieces of the hand-compiled alsa drivers/utils laying around. I don't know enough about alsa and how Ubuntu works with it to get rid of my mistake. Reinstalling Ubuntu would solve it but (1) keep me ignorant of how to properly reinstall and configure the sound subsystem and (2) not solve the very first problem of my sound card suddenly not working (it works fine in Windows). 

I exhausted the guides I can find that seem to be relevant and appreciate any help or information you can toss at this. I read a post about alsa having the same initial issue when certain usb devices were unplugged but haven't found any specifics or solutions. 

My system: AMD Sempron 2400+ 1.6GHz, 756MB, au8820 pci card and via8235 chipset on the motherboard. I've tried uninstalling the au8820 and disabling the via8235 - neither helped.

For what it's worth, the output of alsa's aadebug script: ```
http://alsa.opensrc.org/index.php?page=aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux Lothar 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_ac97_bus            2432  0 
snd_page_alloc         10504  0 
snd                    65164  0 

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

CPU -------------------------------------------------------
model name      : AMD Sempron(tm) 2400+
cpu MHz         : 1666.673

RAM -------------------------------------------------------
MemTotal:       775500 kB
SwapTotal:     2265124 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:0a.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

---

