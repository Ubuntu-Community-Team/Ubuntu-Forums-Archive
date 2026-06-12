---
title: "No sound on the omnibook 4150, Save my baby!"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by beepboop on 2006-07-06
Contents:
1.Intro
2.Related Threads/Sites
3.Standard Sound Commands And Results
4.Attempted Solutions And Results
5. Brief summary/beg for help
-------------------------------------------------------------------------------
[Color=red]1. Intro: My sound doesnt work.[/color]
I have seen this problem on several boards acrossed several distros and many years, each one leaving the user with a sense that the solution is a mysterious set of guessed parameters and drivers. In this thread I intend to establish once and for all a method of making my baby sing.

[Color=red]2.Other threads on this subject:[/color]
[http://www.ubuntuforums.org/showthread.php?t=150819&highlight=nm256](http://www.ubuntuforums.org/showthread.php?t=150819&highlight=nm256)
[http://www.ubuntuforums.org/showthread.php?t=160696&highlight=nm256](http://www.ubuntuforums.org/showthread.php?t=160696&highlight=nm256)
[http://www.ubuntuforums.org/showthread.php?t=109057&highlight=nm256](http://www.ubuntuforums.org/showthread.php?t=109057&highlight=nm256)
[http://www.ubuntuforums.org/showthread.php?t=28922&highlight=nm256](http://www.ubuntuforums.org/showthread.php?t=28922&highlight=nm256)
[http://www.redhat.com/archives/sound-list/2000-September/msg00050.html](http://www.redhat.com/archives/sound-list/2000-September/msg00050.html)
[http://lists.debian.org/debian-laptop/2005/06/msg00010.html](http://lists.debian.org/debian-laptop/2005/06/msg00010.html)
[http://www.nixu.fi/~tsilven/linux/hp4150.html](http://www.nixu.fi/~tsilven/linux/hp4150.html)

[color=red]3.Command outputs:[/color]
[quote=lspci]
# lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
**0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)**
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
[/quote]
Result: The sound card is listed.

[quote=lsmod grep nm256]
# lsmod | grep nm256
**snd_nm256              69280  0**
snd_ac97_codec         92704  1 snd_nm256
snd_pcm                89864  5 snd_ad1848_lib,snd_nm256,snd_cs4231_lib,snd_pcm_oss,snd_ac97_codec
snd                    55268  13 snd_ad1848_lib,snd_nm256,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_timer
[/quote]
Result: The module is listed in lsmod

[quote=dmesg]
# cat dmesg | grep nm256
[4294667.296000] Built 1 zonelists
[   83.559091] nm256: The device is blacklisted.  Loading stopped
[/quote]
Result: Checked the blacklist file, the device is not in the blacklist file.


[quote=aplay]
# aplay -l
aplay: device_list:221: no soundcards found...
[/quote]
Result: No sound cards found.
[quote=alsamixer]
# alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
[/quote]
Result: No such device

[color=red]4. Attempted Solutions[/color]
Solution 1, Using the ad1848 module.
[quote=heimo]
from thread: [http://www.ubuntuforums.org/showthread.php?t=28922&highlight=nm256](http://www.ubuntuforums.org/showthread.php?t=28922&highlight=nm256)
 Note: The NM256 chip can be linked internally with non-AC97
codecs. This driver supports only the AC97 codec, and won't work
with machines with other (most likely CS423x or OPL3SAx) chips,
even though the device is detected in lspci. In such a case, try
other drivers, e.g. snd-cs4232 or snd-opl3sa2. Some has ISA-PnP
but some doesn't have ISA PnP. You'll need to speicfy isapnp=0
and proper hardware parameters in the case without ISA PnP.

Note: This driver is really crappy. It's a porting from the
OSS driver, which is a result of black-magic reverse engineering.
The detection of codec will fail if the driver is loaded *after*
X-server as described above. You might be able to force to load
the module, but it may result in hang-up. Hence, make sure that
you load this module *before* X if you encounter this kind of
problem.
[/quote]
This seems to coincide with information from another thread:
[quote=eddie303]
modprobe ad1848 io=0x530 irq=5 dma=1 dma2=0
[/quote]
This information is also supported:
here [http://www.nixu.fi/~tsilven/linux/hp4150.html](http://www.nixu.fi/~tsilven/linux/hp4150.html)
here [http://lists.debian.org/debian-laptop/2005/06/msg00010.html](http://lists.debian.org/debian-laptop/2005/06/msg00010.html)

The attempt went as follows:
i/o is set to "WSS I/O= 0x530" in the bios. I am pretty sure this is correct for the io parameter.
Using this command:
```
modprobe ad1848 io=0x530 irq=5 dma=1 dma2=0
```
Did not alter the output from aplay or alsamixer or /dev/sndstat.
According to [https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)
"you must supply a boot argument for older non-PNP ISA cards to be detected."
This is supported at [http://www.ubuntuforums.org/showthread.php?t=28922&highlight=nm256](http://www.ubuntuforums.org/showthread.php?t=28922&highlight=nm256)
with:
[quote=heimos]
This driver is really crappy. It's a porting from the
OSS driver, which is a result of black-magic reverse engineering.
The detection of codec will fail if the driver is loaded *after*
X-server as described above. [/quote]
The second attempt went as follows:
Added the modprobe command for ad1848 to /etc/modules.
I rebooted to allow the module to load on boot.

[color=green]Result: [/color]No change, no sound. The module does not show up in lsmod, but I did get some interesting output from dmesg:
[quote=dmesg]
[   85.212156] ad1848/cs4248 codec driver Copyright (C) by Hannu Savolainen 1993-1996
[   85.212214] ad1848: No ISAPnP cards found, trying standard ones...
[/quote]

I think that I am missing some vital part of this solution.
Some other documents refer to leading multiple modules in order to get this working.
Supported: [http://www.nixu.fi/~tsilven/linux/hp4150.html](http://www.nixu.fi/~tsilven/linux/hp4150.html)
[quote=website]
Update September 5, 2001:
Erik Wenzel send me these instructions for Sound with Kernel release > 2.4.1
The driver has been rewritten, so you need the following kernel modules: opl3, ad1848, mpu401, sound and soundcore create a /etc/modutils/ad1848 with:
---snip---
alias char-major-14 ad1848
pre-install ad1848 modprobe "-k" "mpu401"
post-install ad1848 modprobe "-k" "opl3"
options ad1848 io=0x530 irq=5 dma=1 dma2=0
options opl3 io=0x388
---snip---
and then run insmod ad1848 or if you want to start it in booting process enter echo ad1848 >>/etc/modules 
[/quote]
[color=red]5. Brief summary/beg for help[/color]
I feel certain that adding the ad1848 module may be the solution to my problem, but I do not know what to try next.
What modules do I need to be loading, and what parameters do they take?
How do I pass these parameters to them?

---

### Post by beepboop on 2006-07-15
Update: I have made no progress and the sound is still non-working

---

