---
title: "Sound frustration with games and flash"
date: 2010-11-15
forum: Multimedia Software
---

### Post by Rhemat on 2010-11-15
Hello All,
A few days ago I installed Ubuntu 10.10, and was going to deal with PulseAudio, but issues with laggy/disappearing sound in Quake 4.

So I installed ALSA, which worked for just about everything (Quake 4, Flash video in Chrome/Firefox, music players, etc.).  However, I couldn't get sound in Quake 3, and I tried to install IOQuake 3, but the install failed.

So I tried installing OSS4 (following this guide here:
[http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html) ).

I wasn't able to get the package from the OpenSound website, I just installed the packages inside Synaptic.  The problem here, is osstest works, but Rhythmbox is the only other program I can get to output sound (haven't tried Quake 4 yet).  No sound from flash video, no sound from Quake 3 (though I haven't tried all the /dev/dsp* devices).

What would be your best solution?  Note, I've already tried these solutions for ALSA:  
[http://alsa.opensrc.org/index.php/Quake_3_engine_games_(Howto](http://alsa.opensrc.org/index.php/Quake_3_engine_games_(Howto))

[http://www.linuxquestions.org/questions/linux-games-33/no-sound-in-quake3-alsa-emu101k-149937/](http://www.linuxquestions.org/questions/linux-games-33/no-sound-in-quake3-alsa-emu101k-149937/)
  Note:  When I was using ALSA, I had no dsp device in /dev

I'll post some more information in a while, and I think I'm going to go back to alsa for now.
===================================================

I tried using SVN, and ioquake3-q3a-1.32-9.run file then make, to compile, but I get this:

```

Building ioquake3 in build/release-linux-i386:
  PLATFORM: linux
  ARCH: i386
  VERSION: 1.36_SVN1802
  COMPILE_PLATFORM: linux
  COMPILE_ARCH: i386
  CC: cc

  CFLAGS:
    -Wall
    -fno-strict-aliasing
    -Wimplicit
    -Wstrict-prototypes
    -pipe
    -DUSE_ICON
    -m32
    -DNO_GZIP
    -Icode/zlib
    -DUSE_LOCAL_HEADERS
    -DPRODUCT_VERSION="1.36_SVN1802"
    -MMD
    -DNDEBUG
    -O3
    -march=i586
    -fomit-frame-pointer
    -funroll-loops
    -falign-loops=2
    -falign-jumps=2
    -falign-functions=2
    -fstrength-reduce
    -ffast-math

  CLIENT_CFLAGS:
    -DUSE_OPENAL
    -DUSE_OPENAL_DLOPEN
    -DUSE_CURL
    -DUSE_CURL_DLOPEN
    -Icode/SDL12/include
    -DUSE_MUMBLE
    -DUSE_VOIP
    -DFLOATING_POINT
    -DUSE_ALLOCA
    -Icode/libspeex/include

  SERVER_CFLAGS:
    -DUSE_VOIP

  LDFLAGS:

  LIBS:
    -ldl
    -lm

  CLIENT_LIBS:
    -lGL
    -lrt

  Output:
    build/release-linux-i386/ioq3ded.i386
    build/release-linux-i386/ioquake3.i386
    build/release-linux-i386/baseq3/cgamei386.so
    build/release-linux-i386/baseq3/qagamei386.so
    build/release-linux-i386/baseq3/uii386.so
    build/release-linux-i386/missionpack/cgamei386.so
    build/release-linux-i386/missionpack/qagamei386.so
    build/release-linux-i386/missionpack/uii386.so
    build/release-linux-i386/baseq3/vm/cgame.qvm
    build/release-linux-i386/baseq3/vm/qagame.qvm
    build/release-linux-i386/baseq3/vm/ui.qvm
    build/release-linux-i386/missionpack/vm/qagame.qvm
    build/release-linux-i386/missionpack/vm/cgame.qvm
    build/release-linux-i386/missionpack/vm/ui.qvm

make[2]: Entering directory `/usr/local/games/ioquake3'
make[2]: `build/release-linux-i386/ioq3ded.i386' is up to date.
CC code/client/qal.c
In file included from code/SDL12/include/SDL_config.h:42,
                 from code/SDL12/include/SDL_stdinc.h:30,
                 from code/SDL12/include/SDL_main.h:26,
                 from code/SDL12/include/SDL.h:30,
                 from code/client/../sys/sys_loadlib.h:39,
                 from code/client/qal.c:32:
code/SDL12/include/SDL_config_minimal.h:39: error: conflicting types for &#8216;uintptr_t&#8217;
/usr/include/stdint.h:129: note: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [build/release-linux-i386/client/qal.o] Error 1
make[2]: Leaving directory `/usr/local/games/ioquake3'
make[1]: *** [targets] Error 2
make[1]: Leaving directory `/usr/local/games/ioquake3'
make: *** [release] Error 2
```

Can I do anything about uintptr_t?  I've heard about configuring ALSA to emulate OSS, any way to do that?  Maybe something about libopenal?
=========================================================================

I've looked some more into OSS emulation via ALSA, and about modules (still don't really understand).  I found a couple of module files; /etc/modules, and /lib/modules/2.6.35-22-generic-pae/.  The first contains:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

The second contains:

```

build          modules.alias.bin    modules.dep          modules.inputmap   modules.pcimap    modules.symbols.bin
initrd         modules.builtin      modules.dep.bin      modules.isapnpmap  modules.seriomap  modules.usbmap
kernel         modules.builtin.bin  modules.devname      modules.ofmap      modules.softdep   updates
modules.alias  modules.ccwmap       modules.ieee1394map  modules.order      modules.symbols

```

Am I missing anything?  Do I need to reconfigure something?



Thanks in advance.

---

### Post by Rhemat on 2010-11-15
Yet more information; lsmod yields:

```


Module                  Size  Used by
parport_pc             26378  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
joydev                  8735  0 
nvidia               9331115  44 
arc4                    1165  2 
iwlagn                179813  0 
snd_hda_codec_nvhdmi    12879  1 
snd_hda_codec_realtek   217980  1 
iwlcore               127479  1 iwlagn
mac80211              231541  2 iwlagn,iwlcore
snd_hda_intel          22203  0 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71571  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
r852                    9600  0 
sm_common               3285  1 r852
cfg80211              144470  3 iwlagn,iwlcore,mac80211
snd                    49006  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   34905  2 r852,sm_common
video                  18712  0 
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
intel_agp              26720  0 
asus_oled               7488  0 
mtd                    18877  2 sm_common,nand
psmouse                59033  0 
serio_raw               4022  0 
output                  1883  1 video
soundcore                880  1 snd
asus_laptop            14084  0 
agpgart                32075  2 nvidia,intel_agp
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
sparse_keymap           3145  1 asus_laptop
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
sdhci_pci               6339  0 
firewire_ohci          21394  0 
firewire_core          46675  1 firewire_ohci
r8169                  36777  0 
sdhci                  15954  1 sdhci_pci
ahci                   19013  0 
led_class               2633  2 asus_laptop,sdhci
libahci                21731  2 ahci
mii                     4425  1 r8169
crc_itu_t               1383  1 firewire_core

```
I know I can't find snd-pcm-oss, snd-seq-oss, or snd-mixer-oss.  How do I install/load/enable these modules?  I do have the alsa-oss, and oss-compat packages installed.  Are they conflicting?

Also, I tried to install the alsa-oss package from source, but that ended in failure (I'll get the output later).  I'm hoping I don't have to compile ALSA from source.

I know I'm dumping a lot of information here, but I really want to play Quake 3.  This will also help a lot of other people out there searching for a solution too.

Thanks in advance again.

---

### Post by Rhemat on 2010-11-17
Okay, I tried to recompile my kernel, and while everything that worked before has continued to work, I still don't have /dev/dsp.  I still can't get OSS emulation.  I followed this guide here to get to the kernel configuration menu:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

and some advice from this thread:

[http://ubuntuforums.org/showthread.php?t=1607546&highlight=oss](http://ubuntuforums.org/showthread.php?t=1607546&highlight=oss)

I enabled some OSS modules under the sound configuration, but I still don't have OSS emulation.  Here is output from my dpkg -i in the final step if it will help.

```


root@main-linux:/usr/src/linux-source-2.6.35# dpkg -i linux-image-2.6.35.4-custom_2.6.35.4-custom-10.00.Custom_i386.deb
Selecting previously deselected package linux-image-2.6.35.4-custom.
(Reading database ... 146331 files and directories currently installed.)
Unpacking linux-image-2.6.35.4-custom (from linux-image-2.6.35.4-custom_2.6.35.4-custom-10.00.Custom_i386.deb) ...
Done.
Setting up linux-image-2.6.35.4-custom (2.6.35.4-custom-10.00.Custom) ...
Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom
 * dkms: running auto installation service for kernel 2.6.35.4-custom                                                                                                  
 *       nvidia-current (260.19.06)...                                                                                                                          [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom
update-initramfs: Generating /boot/initrd.img-2.6.35.4-custom
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35.4-custom
Found initrd image: /boot/initrd.img-2.6.35.4-custom
Found linux image: /boot/vmlinuz-2.6.35-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
root@main-linux:/usr/src/linux-source-2.6.35# dpkg -i linux-headers-2.6.35.4-custom_2.6.35.4-custom-10.00.Custom_i386.deb
(Reading database ... 150180 files and directories currently installed.)
Preparing to replace linux-headers-2.6.35.4-custom 2.6.35.4-custom-10.00.Custom (using linux-headers-2.6.35.4-custom_2.6.35.4-custom-10.00.Custom_i386.deb) ...
Unpacking replacement linux-headers-2.6.35.4-custom ...
Setting up linux-headers-2.6.35.4-custom (2.6.35.4-custom-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom
 * dkms: running auto installation service for kernel 2.6.35.4-custom                                                                                                  
 *       nvidia-current (260.19.06)...                                                                                                                          [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35.4-custom /boot/vmlinuz-2.6.35.4-custom

```

If any one has a clue, please help.  Thanks in advance.

---

### Post by rajeev1204 on 2010-11-18
Getting q3 to run has always been a pain. I remember even getting it installed properly was a pain.

Anyways,

Did you go here to download OSS ?  [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

You can select your version from this .

Also, iam having issues with quake 4 also since 10.04.This problem did not exist before .

See this [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/577727](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/577727)

---

### Post by Rhemat on 2010-11-18
Actually, until 10.04 (maybe sooner), I never had issues installing Quake 3.  Video drivers maybe (4.10 to 5.10), but installing Quake 3 was simple.

I tried using just OSS4 before, but that didn't work out.  I also tried installing it via Synaptic.  Am I supposed to have OSS installed for the ALSA-OSS packages to work?

I'm guessing your issues with Quake 4 are laggy/no sound?  What I did is purged PulseAudio, and then just installed ALSA using Hugo's instructions here:

[http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

One of the packages he references (libesd-alsa0) is no longer in the repos, but it can be ignored (I think that was the package anyway).

I hope that helps.

---

### Post by Rhemat on 2010-11-19
Okay, after having recompiled my kernel twice, and altered/deleted a couple of blacklist files in /etc/modprobe.d, and tweaking alsa-base.conf a little, I still don't have sound in Quake 3.  I have snd_pcm_oss, and snd_mixer_oss modules loaded automatically, and /dev/dsp is present, but still no sound in Quake3.  I try aoss quake3, and I get:

```


------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xa2cf670 dma buffer
No background file.
----------------------
Sound memory manager started

```

I've tried just plain quake3, and I get:

```


------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started

```

I even tried esddsp quake3, and I get:

```


------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started

```

I still get no sound.  So what is there left to do?  Is there another hidden blacklist file, or is there some code hidden in a configuration file blacklisting OSS emulation?

I should point out, that if the developers are so hell-bent on removing any form of support for OSS, then they may also want to remove all OSS packages from the repository (such as Quake3).

---

### Post by calraith on 2010-11-22
> **Rhemat said:**
> Okay, I tried to recompile my kernel, and while everything that worked before has continued to work, I still don't have /dev/dsp.  I still can't get OSS emulation.  I followed this guide here to get to the kernel configuration menu:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

and some advice from this thread:

[http://ubuntuforums.org/showthread.php?t=1607546&highlight=oss](http://ubuntuforums.org/showthread.php?t=1607546&highlight=oss)

I enabled some OSS modules under the sound configuration, but I still don't have OSS emulation.  Here is output from my dpkg -i in the final step if it will help.


Actually, you can leave the OSS (deprecated) stuff disabled.  Don't confuse OSS with ALSA OSS Emulation.  They're two separate beasts.  When you make menuconfig, enable the following within Device Drivers --> Sound Card Support --> **Advanced Linux Sound Architecture**:

[LIST]
[*]OSS Mixer API
[*]OSS PCM API
[*]OSS Sequencer API
[/LIST]
------------------------------------------------------------------------------------------------

For what it's worth, I've also found that it's possible to run Lucid's kernel in Maverick, which seems to fix a whole assload of problems (/dev/dsp, lirc, updated nvidia drivers from ubuntu-x-swat/x-updates breaking dkms when using a custom kernel, prolly a plethora of other junk).

Anyway, to install the Lucid kernel in Maverick, modify **/etc/apt/sources.list** and add this line:
```
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
```Then do the following:
```
sudo apt-get update
sudo apt-get install linux-image-2.6.32-25-generic linux-headers-2.6.32-25-generic
```After installing, reboot.  After POST when Grub is counting down, hit Esc to get into the Grub boot menu to boot to a different kernel.  Choose your new (old) 2.6.32 kernel.

Then get rid of your broken kernel.
```
sudo apt-get purge linux-image-2.6.35-22-generic linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
```... as well as any 2.6.35 kernels you've compiled.  **Pay attention to the output of apt when you remove kernels.**  You might need to reapply Grub to your hard drive's boot sector.  If so, do this:
```
sudo update-grub && sudo grub-install /dev/sda
```... where /dev/sda is the device name of your system drive.

---

