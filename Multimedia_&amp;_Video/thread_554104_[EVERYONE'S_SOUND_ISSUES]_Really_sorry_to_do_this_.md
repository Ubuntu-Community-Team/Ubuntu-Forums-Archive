---
title: "[EVERYONE'S SOUND ISSUES] Really sorry to do this but"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by AstarothCY on 2007-09-18
obviously there is a number of people having similar or even identical sound issues that have arisen recently, many of them due to an Edgy->Feisty upgrade. I don't even need to link any threads because they are simply all over the place. Just check the huge sound problem solving thread for starters.

How come there have been absolutely no replies and no attempts from any of the more experienced people to at least try to help in the several weeks people have been having these problems?** I am not demanding anything from anyone, I am just wondering why this is the case**. 

We can't even file a bug report because the problem is so bizarre, you wouldn't really know where to begin reporting. Surely having sound is something crucial to most Ubuntu users and I would subsequently expect it to have quite high priority, but it doesn't seem to be the case for some reason.

---

### Post by tfarinella on 2007-09-18
thank you i was gonna say something myself about the experienced users waisting there time on questions about mythtv instead of no sound

---

### Post by AstarothCY on 2007-09-19
bump

---

### Post by AstarothCY on 2007-09-19
bump

---

### Post by loserboy on 2007-09-19
ya know canonical offers a support program and they will be able to help you in a timely manner...

---

### Post by AstarothCY on 2007-09-21
they just keep piling on

---

### Post by Vadi on 2007-09-21
> **AstarothCY said:**
> obviously there is a number of people having similar or even identical sound issues that have arisen recently, many of them due to an Edgy->Feisty upgrade. I don't even need to link any threads because they are simply all over the place. Just check the huge sound problem solving thread for starters.

How come there have been absolutely no replies and no attempts from any of the more experienced people to at least try to help in the several weeks people have been having these problems?** I am not demanding anything from anyone, I am just wondering why this is the case**. 

We can't even file a bug report because the problem is so bizarre, you wouldn't really know where to begin reporting. Surely having sound is something crucial to most Ubuntu users and I would subsequently expect it to have quite high priority, but it doesn't seem to be the case for some reason.

I haven't noticed any sound issues, except one, which was solved. It wasn't the case of upgrading however.

I'd gladly help you out, but where do I start? You say "kjust check the huge sound problem solving thread". Well, I don't know where it is, and you haven't even given me a link to it. 
"huge" could mean there are lots of replies or lots of questions, but whatever.

So, uh, great, you have a sound problem. I don't. I don't know what your sound card is even to start with - sound works perfectly with mine!

See the problem? I'll help you out, gladly. But where do I start even with zero information?

---

### Post by kerry_s on 2007-09-21
so i'm guessing you have no sound?

[B]sudo apt-get install alsa-base alsa-utils
sudo alsaconf
reboot[/B]

not sure if ubuntu is still using esd, but esd is not that great, hopefully alsa will help you.

---

### Post by AstarothCY on 2007-09-21
The reason I made this thread was that no-one was replying to the actual threads with all the problem information. So I made a thread basically to ask "Does anyone even care?", and if anyone responds, I'll forward them to the threads. So here you are!

[This](http://ubuntuforums.org/showthread.php?t=205449&page=66) is the first place to start. If you look at that page of the thread and the last few posts of the previous page you will realize that something is going on there. I am having exactly the same problem as all those people.

[This](http://ubuntuforums.org/showthread.php?t=550102) is the thread I made for my issues.

Thanks for replying! Hope you manage to help out.

---

### Post by AstarothCY on 2007-09-21
> **kerry_s said:**
> so i'm guessing you have no sound?

[B]sudo apt-get install alsa-base alsa-utils
sudo alsaconf
reboot[/B]

not sure if ubuntu is still using esd, but esd is not that great, hopefully alsa will help you.

Thank you, i've done that. Please refer to my previous post.

---

### Post by kerry_s on 2007-09-21
> **AstarothCY said:**
> Thank you, i've done that. Please refer to my previous post.

bummer

have you tried adding a user and see if sound works for a fresh user?

it might just be a settings file that is loading and turning sound off/muting.

---

### Post by AstarothCY on 2007-09-21
yup, tried that

---

### Post by Vadi on 2007-09-21
Please follow the guide I found on the wiki ([click]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29")), and post the output.

I had an odd problem with sound too, it would play for a second when I plugged/unplugged my laptop. It solved itself though.

---

### Post by AstarothCY on 2007-09-21
I actually have to go through all that again? Will you just trust me that everything works fine and my sound card is recognized and everything but i simply cannot hear any sound?

Nevermind, I'll do it anyway. Give me a little while, it is a lot to go through since everything just works fine.

---

### Post by Vadi on 2007-09-21
I don't know what you went through! So yeah, go through it again.

I found a second guide here too if the first fails ([click]("https://help.ubuntu.com/community/DebuggingSoundProblems?highlight=%28sound%29"))

---

### Post by AstarothCY on 2007-09-21
The guide you gave me is identical to the one in the thread I linked for you, the Comprehensive Sound Solutions thread. I already answered your question then, everything works fine, I get to the "Using alsa-source" section, I use the method without module-assistant, I untar and configure, but when i get to the make part it gives the exact same error everyone else is getting, and here is the output for the make:

```
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -auvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/src/modules/alsa-driver'
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
copying file alsa-kernel/core/info.c
patching file info.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #3 succeeded at 2815 (offset -32 lines).
Hunk #4 succeeded at 2835 (offset -32 lines).
Hunk #5 succeeded at 2888 (offset -32 lines).
Hunk #6 succeeded at 2915 (offset -32 lines).
Hunk #7 succeeded at 3006 (offset -32 lines).
Hunk #8 succeeded at 3025 (offset -32 lines).
Hunk #9 succeeded at 3044 (offset -32 lines).
Hunk #10 succeeded at 3077 (offset -32 lines).
Hunk #11 succeeded at 3110 (offset -32 lines).
Hunk #12 succeeded at 3143 (offset -32 lines).
Hunk #13 succeeded at 3172 (offset -32 lines).
Hunk #14 succeeded at 3193 (offset -32 lines).
Hunk #15 succeeded at 3211 (offset -32 lines).
Hunk #16 succeeded at 3231 (offset -32 lines).
Hunk #17 succeeded at 3243 (offset -32 lines).
Hunk #18 succeeded at 3275 (offset -32 lines).
Hunk #19 succeeded at 3341 (offset -32 lines).
Hunk #20 succeeded at 3370 with fuzz 1 (offset -32 lines).
Hunk #21 succeeded at 3411 (offset -32 lines).
Hunk #22 succeeded at 3561 (offset -32 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #2 succeeded at 1411 (offset 194 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #1 succeeded at 309 (offset 6 lines).
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 204 (offset 12 lines).
Hunk #3 succeeded at 277 (offset 13 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1297 (offset 30 lines).
Hunk #2 succeeded at 1380 with fuzz 1 (offset 30 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 1012 with fuzz 1 (offset 17 lines).
Hunk #2 succeeded at 1925 (offset 134 lines).
Hunk #3 succeeded at 1970 with fuzz 2 (offset 125 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 83 (offset -1 lines).
Hunk #3 succeeded at 143 (offset -1 lines).
Hunk #4 succeeded at 174 (offset -1 lines).
Hunk #5 succeeded at 207 (offset -1 lines).
Hunk #6 succeeded at 228 (offset -1 lines).
Hunk #7 succeeded at 264 (offset -1 lines).
Hunk #8 succeeded at 286 (offset -1 lines).
Hunk #9 succeeded at 311 (offset -1 lines).
Hunk #10 succeeded at 329 (offset -1 lines).
Hunk #11 succeeded at 608 (offset -1 lines).
Hunk #12 succeeded at 697 (offset -1 lines).
Hunk #13 succeeded at 712 (offset -1 lines).
Hunk #14 succeeded at 746 (offset -1 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
Hunk #1 succeeded at 379 with fuzz 1 (offset 2 lines).
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #1 succeeded at 2528 (offset 2 lines).
Hunk #2 succeeded at 2579 (offset 2 lines).
Hunk #3 succeeded at 2702 (offset 2 lines).
Hunk #5 succeeded at 3012 (offset -2 lines).
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #1 succeeded at 57 (offset 6 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
Hunk #2 succeeded at 2209 (offset 68 lines).
Hunk #3 succeeded at 2558 with fuzz 1 (offset 89 lines).
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 248 (offset 3 lines).
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #1 succeeded at 189 (offset 3 lines).
Hunk #2 succeeded at 223 with fuzz 1 (offset 3 lines).
Hunk #3 succeeded at 326 (offset -8 lines).
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[2]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
Hunk #1 succeeded at 30 (offset 2 lines).
Hunk #2 succeeded at 46 (offset 2 lines).
Hunk #3 succeeded at 64 with fuzz 2 (offset 2 lines).
Hunk #4 succeeded at 92 with fuzz 2 (offset -55 lines).
Hunk #5 succeeded at 296 (offset 49 lines).
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #1 succeeded at 435 (offset 2 lines).
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[3]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
Hunk #1 succeeded at 53 with fuzz 2 (offset 1 line).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 815 (offset 5 lines).
Hunk #2 succeeded at 954 (offset 6 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #1 succeeded at 41 (offset -2 lines).
Hunk #2 succeeded at 728 (offset -21 lines).
Hunk #3 succeeded at 739 (offset -21 lines).
Hunk #4 succeeded at 3052 (offset 239 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #5 succeeded at 2911 (offset 1 line).
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #1 succeeded at 35 (offset 2 lines).
Hunk #2 succeeded at 1890 with fuzz 2 (offset 77 lines).
Hunk #3 succeeded at 1924 with fuzz 2 (offset 78 lines).
copying file alsa-kernel/pci/ac97/ac97_bus.c
patching file ac97_bus.c
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #1 succeeded at 262 (offset 2 lines).
Hunk #2 succeeded at 301 (offset 2 lines).
Hunk #3 succeeded at 320 (offset 2 lines).
Hunk #4 succeeded at 336 (offset 2 lines).
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #1 succeeded at 1273 (offset 4 lines).
Hunk #2 succeeded at 2230 (offset 4 lines).
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 659 (offset 1 line).
Hunk #4 succeeded at 686 (offset 1 line).
Hunk #5 succeeded at 767 (offset 1 line).
Hunk #6 succeeded at 782 (offset 1 line).
Hunk #7 succeeded at 1149 (offset 1 line).
Hunk #8 succeeded at 2073 (offset 38 lines).
Hunk #9 succeeded at 2092 (offset 38 lines).
Hunk #10 succeeded at 2109 (offset 38 lines).
Hunk #11 succeeded at 2656 (offset 45 lines).
Hunk #12 succeeded at 2728 (offset 44 lines).
Hunk #13 succeeded at 3013 (offset 44 lines).
Hunk #14 succeeded at 3085 (offset 44 lines).
Hunk #15 succeeded at 3154 (offset 44 lines).
Hunk #16 succeeded at 3172 (offset 44 lines).
Hunk #17 succeeded at 3186 (offset 44 lines).
Hunk #18 succeeded at 3199 (offset 44 lines).
Hunk #19 succeeded at 3395 (offset 70 lines).
Hunk #20 succeeded at 3486 (offset 70 lines).
Hunk #21 succeeded at 3624 (offset 76 lines).
Hunk #22 succeeded at 3645 (offset 76 lines).
Hunk #23 succeeded at 3667 (offset 76 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 225 with fuzz 2 (offset -3 lines).
Hunk #3 succeeded at 249 with fuzz 2 (offset -3 lines).
Hunk #4 succeeded at 343 (offset -3 lines).
Hunk #5 succeeded at 1363 (offset 53 lines).
Hunk #6 succeeded at 1707 (offset 58 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #2 succeeded at 49 (offset 1 line).
Hunk #3 succeeded at 1726 (offset 27 lines).
Hunk #4 succeeded at 1775 (offset 27 lines).
Hunk #5 succeeded at 1796 (offset 27 lines).
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o
In file included from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of &#8216;jiffies_to_msecs&#8217;
include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of &#8216;msecs_to_jiffies&#8217;
include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
In file included from /usr/src/modules/alsa-driver/include/adriver.h:858,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/linux/pci.h:541: error: expected identifier or &#8216;(&#8217; before numeric constant
In file included from /usr/src/modules/alsa-driver/include/sound/driver.h:46,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
make[3]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

```

I've been through that other guide btw, it didn't help.

---

### Post by AstarothCY on 2007-09-21
Tried it again with the Gutsy version of build-essential and the error is the same.

---

### Post by Vadi on 2007-09-21
Okay!

Try the second guide then ([click]("http://https://help.ubuntu.com/community/DebuggingSoundProblems?highlight=%28sound%29")).

I'll search on launchpad meanwhile to see if there's a bug report about this.

---

### Post by AstarothCY on 2007-09-21
I have tried the second guide, as I said, and it did not help at all.

---

### Post by Vadi on 2007-09-21
Great, except I don't know which part of the pages long guide didn't help.

What does aplay --list-devices return?

---

### Post by Vadi on 2007-09-21
Since you *do* get sound at times, lets try this odd idea that I saw:

In the terminal, do "sudo su", then "aplay -vv /usr/share/sounds/login.wav". If you hear nothing, do "exit".

---

### Post by AstarothCY on 2007-09-21
What? Who said I get sound at times? I don't have ANY sound, EVER, in Ubuntu. I ALWAYS have sound in other OSs.

anyway

aplay --list-devices:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Tried to play the login sound as su, predictably enough, i couldn't hear anything. No errors were displayed, the output seemed perfectly happy.

---

### Post by Vadi on 2007-09-21
> **AstarothCY said:**
> What? Who said I get sound at times? I don't have ANY sound, EVER, in Ubuntu. I ALWAYS have sound in other OSs.

"I was trying to configure a wireless USB module (ZyXEL G-260) and **was listening to music** on Amarok"

Pardon?

---

### Post by AstarothCY on 2007-09-21
Uh, yes, sound used to work fine, then that bizarre Amarok thing happened, and since then it doesn't.

---

### Post by Vadi on 2007-09-21
The other thread where the sound issue was solved is here ([http://ubuntuforums.org/showthread.php?t=550753](http://ubuntuforums.org/showthread.php?t=550753)), if you read towards the end, mj did a bunch of instructions and got it working. Maybe they'll work for you.

---

### Post by AstarothCY on 2007-09-21
I've done that already, but I'll do it again just in case.

---

### Post by AstarothCY on 2007-09-21
Done, same result, no sound.

btw here's some output if you're interested:

```
menelaos@menelaos-linux:~$ dir /proc/asound
Audigy  card0  cards  devices  hwdep  modules  oss  pcm  seq  timers  version
menelaos@menelaos-linux:~$ dir /proc/asound/card0
codec97#0     fx8010_gpr        midi0  oss_mixer  pcm2c     voices
emu10k1       fx8010_tram_addr  midi1  pcm0c      pcm2p     wavetableD1
fx8010_acode  fx8010_tram_data  midi2  pcm0p      pcm3p
fx8010_code   id                midi3  pcm1c      spdif-in
```

---

### Post by Vadi on 2007-09-21
I've asked mali to help you on this, hopefully he'll come by. :/

---

### Post by AstarothCY on 2007-09-21
Thanks :) I really appreciate you taking the time, you are the first person to do so.

---

### Post by Vadi on 2007-09-21
If all else fails, you could just backup your home folder, reinstall Ubuntu and *dont* have amarok playing while you're configuring that usb thing!

---

### Post by mali2297 on 2007-09-21
> **AstarothCY said:**
> obviously there is a number of people having similar or even identical sound issues that have arisen recently, many of them due to an Edgy->Feisty upgrade. I don't even need to link any threads because they are simply all over the place. Just check the huge sound problem solving thread for starters.

How come there have been absolutely no replies and no attempts from any of the more experienced people to at least try to help in the several weeks people have been having these problems?** I am not demanding anything from anyone, I am just wondering why this is the case**. 

We can't even file a bug report because the problem is so bizarre, you wouldn't really know where to begin reporting. Surely having sound is something crucial to most Ubuntu users and I would subsequently expect it to have quite high priority, but it doesn't seem to be the case for some reason.

I have read your posts in the other threads and it seems like you've already tried everything that I could have come up with, but I'm **not** an expert.  

As you said yourself, the Amarok thing appears bizarre. You really should file a bug report. You have a better chance finding a true expert at Launchpad than here.

---

### Post by AJWhitewolf on 2007-09-22
Hey, I didn't comb through the threads you posted, so if you already tried this, then I'm sorry, but when I first installed ubuntu I did not have any sound until I unchecked the Audigy Analog/Digital Output Jack found when you double-click the volume button, and tab over to switches.

---

### Post by AstarothCY on 2007-09-22
Thanks AJWW, tried that as well. Mali, what sort of bug report should I file? I have no clue what or where the bug even is!

---

### Post by mali2297 on 2007-09-23
> **AstarothCY said:**
> Thanks AJWW, tried that as well. Mali, what sort of bug report should I file? I have no clue what or where the bug even is!

I think you can follow these advices on reporting sound bugs:
[https://help.ubuntu.com/community/DebuggingSoundProblems#head-b6a8376cdf0f686715eda6c8d393479f5502a559](https://help.ubuntu.com/community/DebuggingSoundProblems#head-b6a8376cdf0f686715eda6c8d393479f5502a559)

> 
If you feel you have encountered a software bug, please report the bug at [https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug) using **your kernel version as the package**.


---

### Post by AstarothCY on 2007-09-23
Thank you very much! I will try to do that later today.

---

### Post by click4851 on 2007-09-23
I really wish these sound problems could be elevated a little higher....the one system I seem to have to fight every time is sound. I won't pretend to know the issues, so I'll fall back to it should just work, and I mean better than ESD. Alsa, Polyaudio, I don't care, perferably something that will work with JACK. Please.

---

