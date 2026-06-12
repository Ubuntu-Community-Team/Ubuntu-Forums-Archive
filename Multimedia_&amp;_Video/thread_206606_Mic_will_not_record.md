---
title: "Mic will not record"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by d3dtn01 on 2006-06-30
I can't get my mic to record anything. I'm using a basic phone jack mic, not a USB based one. Having read through the posts, most people solve this problem by configuring alsamixer. But when I look at alsamixer, I only have a volume control for capture, not a separate one for mic. Shouldn't there be one for mic? Here's the output I get from amixer:

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 1 [3%] [on]
  Front Right: Playback 1 [3%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [on]
  Front Right: Capture 15 [100%] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%]
  Front Right: 4 [100%]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Mic'

I have an HDA-Intel sound card.

Any ideas for a fix based on this info?

---

### Post by lodp on 2006-06-30
You could try and compile the latest ALSA release (1.0.11) from alsa-project.org. there's some instructions how to do that here: [http://ubuntuforums.org/showthread.php?t=195434&highlight=hda-intel](http://ubuntuforums.org/showthread.php?t=195434&highlight=hda-intel) (just ignore the stuff with about the new kernel). i think some of the hda-intel cards are only supported since 1.0.11RC1. on a sidenote, i've got a hda-intel alc883, and the mic is the only thing that works, no internal speakers, no headphones :confused: 

you can check which alsa version you're running this way:

```
cat /proc/asound/version
```

---

### Post by d3dtn01 on 2006-06-30
UPDATE: I solved the problem below. I had to install the kernel headers.

[QUOTE=lodp]You could try and compile the latest ALSA release (1.0.11) from alsa-project.org. there's some instructions how to do that here: [http://ubuntuforums.org/showthread.php?t=195434&highlight=hda-intel](http://ubuntuforums.org/showthread.php?t=195434&highlight=hda-intel) (just ignore the stuff with about the new kernel). i think some of the hda-intel cards are only supported since 1.0.11RC1. on a sidenote, i've got a hda-intel alc883, and the mic is the only thing that works, no internal speakers, no headphones :confused: 

you can check which alsa version you're running this way:

```
cat /proc/asound/version
```[/QUOTE]

lodp, thanks for the advice and links. I came across that thread earlier but was too scared to attempt to compile a new alsa since I'm such a linux newbie. But I dove in and got stuck early on. The following is what happened when I tried to configure the driver (skip to the end where an error message is bolded):

```
root@DellB120:~/Desktop/alsa-driver-1.0.11# ./configure --with-oss=yes --with-ca rds=hda-intel --with-kernel=/usr/include/linux
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/daren/Desktop/alsa-driver-1.0.11
checking cross compile...
checking for directory with kernel source... /usr/include/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/include/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
root@DellB120:~/Desktop/alsa-driver-1.0.11# ./configure --with-oss=yes --with-ca rds=hda-intel --with-kernel=/usr
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/daren/Desktop/alsa-driver-1.0.11
checking cross compile...
checking for directory with kernel source... /usr
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.11
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.0.3 (Ub untu 4.0.3-1ubuntu5)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel .

checking for built-in ALSA... no
checking for existing ALSA module... no
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... no
Creating a dummy <linux/pm.h>...
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... no
Creating a dummy <linux/rwsem.h>...
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... yes
checking for kernel linux/highmem.h... no
Creating a dummy <linux/highmem.h>...
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... no
Creating a dummy <linux/dma-mapping.h>...
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... no
Creating <linux/platform_device.h>...
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... no
Creating <linux/mutex.h>...
checking for kernel module symbol versions... no
checking for PCI support in kernel... no
checking for I2C driver in kernel... unknown
checking for firmware loader... unknown
checking for input subsystem in kernel... unknown
checking for directory to store kernel modules... /lib/modules/2.6.11/misc
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... unknown
checking for SMP... no
checking for Video device support in kernel... no
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... no
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
no
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
Symlinking <linux/pnp.h>...
checking for driver version... 1.0.11
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... no
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... no
checking for USB support... no
checking for USB module support... no
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... no
checking for PCMCIA module support... no
checking for PC9800 support in kernel... no
checking for parallel port support... no
checking for parallel port module support... no
[B]checking for which soundcards to compile driver for... configure: error: Unsuppo rted soundcard hda-intel
[/B]root@DellB120:~/Desktop/alsa-driver-1.0.11# 
```

Sorry for the verbose code, but notice the error message that said hda-intel is unsupported. I ignored this and proceeded to the next step, getting this result:

```

root@DellB120:~/Desktop/alsa-driver-1.0.11# make
make all-deps
make[1]: Entering directory `/home/daren/Desktop/alsa-driver-1.0.11'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/daren/Desktop/alsa-driver-1.0.11'

Please, run the configure script as first...
root@DellB120:~/Desktop/alsa-driver-1.0.11#

```

So it looks to me like my configuration step didn't work. I'm really unfamiliar with this process, so forgive me if I'm making a simple mistake. Can anyone explain what I'm doing wrong?

---

### Post by lodp on 2006-07-01
so you compiled alsa 1.0.11 successfully? is sound working now?

---

### Post by d3dtn01 on 2006-07-03
[QUOTE=lodp]so you compiled alsa 1.0.11 successfully? is sound working now?[/QUOTE]

Not yet. I got the driver installed successfully. Whilst running configure for alsa-utils I go the following error:

```
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

```

I'm not real familiar with curses libraries, but here are the ones that I have installed:

lib64ncurses5
libncurses5
libncursesw5
ncurses-base
ncurses-bin
ncurses-term

Is there some other one that I need?

---

### Post by d3dtn01 on 2006-07-05
Thanks to LordRaiden and killerjay_47 I found the correct curses library (libncurses5-dev). So, I've compiled the latest alsa release and still this has not fixed my mic problem. Where do I go from here?

---

### Post by lodp on 2006-07-07
Did you try compiling the latest release candidate (1.0.12rc1)? might be worth a shot.

did you actually load the driver after compiling?

you definitely need to know which chip your hda-intel card uses. then you can look it up in /usr/src/linux/Documentation/sound/alsa/ALSA-Configuration.txt and try different model options when loading the driver.

find out what chip you got by typing

```
cat /proc/asound/card0/codec#0
```
-- it's right in the first line (codec). also, alsamixer tells you the name of the chip.

you load the driver by typing

```
sudo modprobe snd-hda-intel model=xxxx
``` whereby xxxx is replaced by the model option. to load the driver automatically on startup, you have to add "snd-hda-intel model=xxxx" to your /etc/modules

---

### Post by d3dtn01 on 2006-07-07
No, I did not load the driver after compiling. I followed your directions and found that my chip model is SigmaTel STAC9200. This model wasn't listed in the ALSA-Configuration.txt file. I proceeded to load the driver with:

```
sudo modprobe snd-hda-intel model=STAC9200
```

I tried recording something with the mic, but still nothing. Should I compile the release candidate?

Thanks for the help.

---

### Post by LordRaiden on 2006-07-07
run alsamixer, and make sure that Microphone and Capture are not muted (not grayed out).

---

### Post by lodp on 2006-07-07
couldn't hurt to install the latest version. the fact that your chip isn't listed is not a good thing -- did you search alsa-project.org (documentation, bug tracker) for the chip's name?

if you don't find anything, you could file a bug report (or a feature request?) on alsa-project.org

---

### Post by extremecarver on 2006-07-17
Uh - I have exactly the same configuration:

HDA and the Sigmatel 92OO

Did the newest driver work for you?

I'm on 1.O.11 RC4 using a 2.6.17beyond1.1 (2.6.17.2 with loads of patches)
Kernel.

Thank you for clearing this up before I give the whole compiling some more runs. I have problems with the script as there are no headers for 2.6.17 and it won't recognise the ones I did use when installing the kernel.

Mic doesn't work. Everything else runs great and cold due to undervolting

---

### Post by extremecarver on 2006-07-17
Just subscribing to the thread - ignore

---

### Post by d3dtn01 on 2006-07-22
Sorry for the late response (I was on vacation). No, the latest version of ALSA didn't work. I can record using Sound Recorder, but the volume is extremely low and there's lots of static. My goal is to get skype working, but it still won't record anything.

Sorry that this doesn't help.

---

### Post by extremecarver on 2006-07-22
Thanks for answering now. I really appreciate it.

For me its the same. I did compile alsa as well from source. However I don't even here a bit.

If you find a solution please write back here. Sigmatel chipset shouldn't be so uncommon, maybe one of us still finds a solution.

Under Windows without Automatic boost it is very silent too - maybe its only that.

Thanks

Felix

---

### Post by extremecarver on 2006-08-04
Well after reading in some forums people got the STAC9200 running as well the microphone starting from 1.11 rc5
I will just play around a bit, remove ALSA support from my kernel (2.6.17.2-beyond1.1 which at least compiles in 20 minutes) and compiling all modules offered by Alsa instead only the firmware.

---

### Post by extremecarver on 2006-08-06
Nope, no succes.
1. Tried to recompile all Also Software - no success.
2. Deleted all ALSA support from Kernel - no Alsa at all.
3. Put ALSA as module only without driver into kernel - no success either

---

### Post by extremecarver on 2006-08-07
I updated my kernel again.
However now I'm back on 1.0.11rc4 - I can't get back to my 1.0.12rc2 - what shall I do?
On 1.0.11rc4 I can't hear any voice, if I however tap on the microphone I can hear it on the record. Loads of noise too.
I tried going into the alsa folder and did make install - like the last time. Last time it however did install those drivers. Where does make install place the install script for me to execute?

---

### Post by kamal_sisira on 2006-08-08
"amixer set Capture toggle"

Dell Inspiron 6400 with Sigmatel STAC9200; Fedora Core 5.

Had the same problem. Tried with various alsa drivers. But this simply worked at the end.

Source: [http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2003-08/1923.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2003-08/1923.html)

Regards,
Kamal Wickramanayake

---

### Post by extremecarver on 2006-08-08
Can you see anything wrong here?
Still does not work - this is after doing what you told me
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 13 [87%] [19.50dB] [off]
  Front Right: Capture 13 [87%] [19.50dB] [off]

---

### Post by extremecarver on 2006-08-08
here is my full amixer output: If I chose line I can here my recorded voice very very quiet. If I chose micro as capture source I can't here anything.

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%]
  Front Right: 4 [100%]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Line'
  Item0: 'Line'
```

---

### Post by extremecarver on 2006-08-08
Some more information

```
root@felix-laptop:/usr/src/alsa/alsa-driver-1.0.12rc2# cat /proc/asound/card0/codec#0
Codec: SigmaTel STAC9200
Address: 0
Vendor Id: 0x83847690
Subsystem Id: 0x102801b5
Revision Id: 0x102201
Default PCM: rates 0x7e0, bits 0x0e, types 0x1
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Node 0x02 [Audio Output] wcaps 0xd0401: Stereo
  Power: 0x0
Node 0x03 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x0a
Node 0x04 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM: rates 0x160, bits 0x0e, types 0x5
  Connection: 1
     0x08
Node 0x05 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM: rates 0x1e0, bits 0x0e, types 0x5
Node 0x06 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
Node 0x07 [Audio Selector] wcaps 0x300901: Stereo
  Connection: 3
     0x02* 0x08 0x0a
Node 0x08 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN EAPD Detect
  Pin Default 0x40c001fb: [N/A] SPDIF In at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Power: 0x0
Node 0x09 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x00451140: [Jack] SPDIF Out at Ext N/A
    Conn = Optical, Color = Black
  Pin-ctls: 0x40: OUT
  Connection: 2
     0x05* 0x0a
Node 0x0a [Audio Selector] wcaps 0x30090d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 1
     0x0c
Node 0x0b [Audio Selector] wcaps 0x300105: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x17 0x17]
  Connection: 1
     0x07
Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Connection: 5
     0x10* 0x0f 0x0e 0x0d 0x12
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP Detect
  Pin Default 0x0321401f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Green
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0b
Node 0x0e [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP Detect
  Pin Default 0x90100110: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x0b
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT Detect
  Pin Default 0x03a11023: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0b
Node 0x10 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT Detect
  Pin Default 0x03811020: [Jack] Line In at Ext Left
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0b
Node 0x11 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00]
  Pincap 0x0810: OUT
  Pin Default 0x401001fd: [N/A] Speaker at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x13
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x409001fc: [N/A] Aux at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x13 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x07
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]

```

---

### Post by capriccio on 2006-08-08
Same problem here with nearly identical hardware.  I have a Dell Inspiron B130 (aka 1300).  Comparing my amixer output, you seem to have one additional control: Simple mixer control 'IEC958',0.  Nonetheless, the symptoms are identical.  Using every possible alsamixer setting, the mic will still not pick up; and trying your suggestion to switch the input setting to 'line' yields the same result:  I can record but only at a very, very low volume.

I tried:
1. setting capture playback, capture & capture mux all to 100% & unmuted.  result: only works when input set to 'line' instead of 'mic'. 
2. turning off capture playback, setting capture & capture mux to 100% unmuted.  result: nothing gets recorded.
3. turning off capture, setting playback to 100% & mux to 100%.  result: nothing gets recorded.

4. d/ling a new kernel image 2.6.17 + the 1.0.11 release of the alsa libs, drivers, etc.  result: nothing.

5. d/ling and burning an ISO of the latest Ubuntu edgy release that has the latest alsa 1.0.12rc1 drivers and 2.6.17 kernel.  result: nothing.

Looking through the changelogs on the alsa dev site, it appears that a lot of bugfixes were made for the STAC 92xx chipset, including one specifically for capture, but still... no dice.

Let me know if you come up with anything.  I'm going to tinker around some more with alsa and maybe even try the OSS commercial drivers.  I'll post here, since of all the threads I've seen on this particular subject, this has been the most informative and has gone beyond: upgrade to the latest alsa build or unmute capture in alsamixer.

That's all, back to hacking.

---

### Post by capriccio on 2006-08-09
Just fixed this on my machine - but I believe that the fix will work for anyone with this particular mic/input problem that has the SigmaTel STAC9200, 922x or 927x chipset for Intel HDA.  Ok, here's what you do:

1. backup your existing /etc/modprobe.d/alsa-base
2. append the following to the end of the file:

options snd-hda-intel model=ref

Done.
Now reload your modules or reboot.  Go into alsamixer.  If everything went as expected, you should see some new options, eg - 'front mic' as an input source and IEC958 (S/PDIF) settings.  Play with these freely *later* - they have nothing to do with the mic problem.  Anyway, make sure the input is set to **mic** and nothing else.  Turn your capture setting all the way up to 100%, capture playback at maybe 50%; tweak these to your tastes.  Now, record something using your favorite audio recording utility.

eg - arecord -f cd TheSoundOfSuccess.wav

Play it back.  Hopefully, everything is good and nice.

If you're curious, I came upon this fix after reading a few threads about setting the model  in '/etc/modprobe.d/alsa-base' if alsa was unable to correctly detect it.  It referred you to the file 'alsa-kernel/Documentation/ALSA-Configuration.txt' within the alsa-driver sources.  Interestingly enough, there was no reference to any STAC 92xx codecs.  So I dug into the 'sound/pci/hda' directory and came upon the 'patch_sigmatel.c' source file.  In this file, all the STAC 92xx codecs were referenced by the model identifier 'ref' which the hda driver uses to load manufacturer specfic presets (SigmaTel, Realtek, etc.).  Looking at the main hda_codec.c source, these presets should theoretically be loaded automatically by using the device's vendor id for identification, but it just doesn't seem to be.  Anyway, if this works for you, bump this thread with a response so that it might help someone else with the problem.

peace.

---

### Post by extremecarver on 2006-08-09
edited:
Well now I found the problem. When I switch to microphone it oversteers so much that upon playback I can only here crackling noise. The volume I set under capture has to be around 25% in order to be pretty much allright. 

However the quality is really bad. I here an awful amount of noise besides it. Even if my micro is bad - under windows it works pretty good.
So there is still a lot of work to do.

Under skype this gets so bad that I can't understand what I sad when I call skype test!!!!!!!!

Thank you very much for this fix, but at this quality it is absolutely bullocks to use the micro for phoning. 

I will upload an ogg file soon, just do some more tests before - maybe this helps someone?


Old Text:
Well now I've got front micro too.
Result is somehow better - but not fixed. Line and Frontmicro give me a very low volume - for the first time I can understand something however - though only when shouting in my micro.

Micro gives me loud crackling noise as before.

However I can't seem to get alsa driver compiled with my vanilla kernel. So I'm still on 1.0.11rc4 - In rc5 the changes for volume were made. Will try it with standard ubuntu kernel now.

---

### Post by extremecarver on 2006-08-09
obsolete

---

### Post by extremecarver on 2006-08-09
edited - obsolete

---

### Post by extremecarver on 2006-08-09
Here are two testrecords - both are well very bad and unusable - even for Ekiga - Skype got it wrong alltogether - I can't even understand my recorded text anymore.

Step1 solved.
Step2 - get proper quality - in process](*,) 

Here are two testrecords - The quality under windows is very good - no noise at all. I don't know why, but I get very different quality from the two recorders. 
QaRecord was around 25% capture volume. Soundrecorder 10% capture volume. Everything else would blow my ears out with crackling noise.  


qaRecord
[http://rapidshare.de/files/28791891/qaRecord.wav.html](http://rapidshare.de/files/28791891/qaRecord.wav.html)

SoundRecorder
[http://rapidshare.de/files/28791557/soundrecorder_ubuntu_2.4.12.ogg.html](http://rapidshare.de/files/28791557/soundrecorder_ubuntu_2.4.12.ogg.html)

---

### Post by nisseman on 2006-08-09
I seem to have the exact same problem with an Intel 82801DB sound card...

- When I turn on both capture and unmute Capture and set it at 100% I get very very low sound recorded with very much noise. (It doesn't matter what capture and mute setting for all other things are set to, that changes nothing).
- If I turn of capture and mute for Capture and turn on capture and unmute for Microphone I get absolute silence, nothing recorded at all. ](*,) 

This is with +20dB Mic Boost enabled, if it isn't no sound at all.
To me it seems as the reason why there is a little sound when using Capture is because it gets the mono output, I have the option to select mono output to either Mic or Mix, and I hear a slight change in the recording when changing between those two.

I also have the option to select either Mic1 or Mic2, I thought this was because I have a build in mic and a jack, but when using either of them the setting has to be Mic1 or else no sound at all.

The built in mic and an external seem to behave exactly alike.

Any sugestions? If anyone wants me to try something for a test, then just post, I'm ready...

---

### Post by capriccio on 2006-08-09
can you post the output of amixer?  i listened to both test files you recorded and i would agree that the buzzing in the background is annoying, but the recording itself is fairly clear and audible.  have you tried muting the capture playback?  when i did this, the sound was crystal clear--no feedback--but the recording itself was hardly audible.

how about playback of regular audio?  has using this fix introduced any new problems with normal mp3 or ogg playback?

also are you testing from a desktop or notebook?  headset or standalone mic?  how many input jacks do you have?

---

### Post by extremecarver on 2006-08-10
PROBLEM: HARDWARE PROBLEM - GROUNDING? - ONLY SLIGHTLY PRESENT ON BATTERY

Both Ogg and Mp3 playback is 1a quality. About on level with Asio playback in foobar2k v9 under MS windows.

Im on a Dell630m Laptop (Centrino base)
I only have one jack for LineIn and Micro. And only one output jack. Plus of course the SPdif - which I don't use however. Oh and a very cheap 3€ Micro gets a lot less affected by this. Will retunrn my 20€ battery powered  Microphone. 

I found the problem: Its a lot worse on Dell standard kernel than on my patched 2.6.17.7beyond3 undervolted. 
I HAVE A GROUNDING PROBLEM WITH MY LAPTOP. AS SOON AS I PLUG OUT THE POWER CABLE - THE BIG BUZZING GOES AWAY, AND ONLY A VERY FINE BUZZING STAYS WHICH I CAN LIVE WITH. 

Will a USB micro get rid of this problem?

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 2 [13%] [3.00dB] [on]
  Front Right: Capture 2 [13%] [3.00dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 3 [75%]
  Front Right: 3 [75%]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

---

### Post by d3dtn01 on 2006-08-14
Thank you, Capriccio! I've spent months trying to get my mic to work and all that I needed was that short line in alsa-base. My mic works like a charm, even in Skype. Now I'm a fully content Ubuntu user.

-d

---

### Post by capriccio on 2006-08-15
> **extremecarver said:**
> 
Im on a Dell630m Laptop (Centrino base)
I only have one jack for LineIn and Micro. And only one output jack. Plus of course the SPdif - which I don't use however. Oh and a very cheap 3€ Micro gets a lot less affected by this. Will retunrn my 20€ battery powered  Microphone. 

I found the problem: Its a lot worse on Dell standard kernel than on my patched 2.6.17.7beyond3 undervolted. 
I HAVE A GROUNDING PROBLEM WITH MY LAPTOP. AS SOON AS I PLUG OUT THE POWER CABLE - THE BIG BUZZING GOES AWAY, AND ONLY A VERY FINE BUZZING STAYS WHICH I CAN LIVE WITH. 

Will a USB micro get rid of this problem?


I would first rule out electromagnetic interference generated by the transformer on your Dell power supply.  Your 20€ mic generates more noise because it's powered and thus amplifying that interference.

Move your power supply as far as possible from your system and all connected equipment to see if the situation improves without actually disconnecting it.  Are any of your inputs/outputs connected on separate power sources?  I'm not sure I see how a ground loop could be introduced so long as everything is connected to the same source; someone could probably tell you more about this than I.

Your amixer settings look good.  You should be able to safely increase the capture levels without reducing recording quality; it's the capture playback settings that introduce a whole lot of lousy into your recordings.

---

### Post by capriccio on 2006-08-15
> **d3dtn01 said:**
> Thank you, Capriccio! I've spent months trying to get my mic to work and all that I needed was that short line in alsa-base. My mic works like a charm, even in Skype. Now I'm a fully content Ubuntu user.

-d

You're very welcome - I'm usually the one getting the help more than giving it though.  These boards offer a wealth of useful information.  Like this one:

[http://ubuntuforums.org/showthread.php?p=1041769#post1041769]("http://ubuntuforums.org/showthread.php?p=1041769#post1041769")

Makes fonts look amazing in X if you're using an LCD *and* like the look of ClearType in XP, for example.  If you like your fonts crisp but jagged, this isn't for you.  Anyway, have a look at some of the before/after screenshots on the thread.

---

### Post by hydronucleus on 2006-08-17
Good for you, you got your fix. But I have the same problem, and I've been searching all afternoon for a fix.

I have just an old SoundFusion cs46xx card on a Dell Precision 420. I've used amixer, alsamixer, kmix, blah blah blah, you name it, I've used it.

I've set capture on the capture, and the mic, mic 1. I've done it all. Still, with arecord, sound-recorder, audacity, jackd and whatever, all I get is slient files of the proper length.

If I don't mute the mic, I can hear it in my headphones, and vary its volume with the mic volume, master volume, etc. So, the mic is good, the speakers are good. Is the card really shot?

This seems as with your problem it might be a "missing" codec problem? How does one solve that for the cs46xx?

This is what I have:
54% cat /proc/asound/cards
0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                     Sound Fusion CS46xx at 0xf6ffe000/0xf6e00000, irq 18

on Brezy Badger with all the updates.

Any help would be appreciated.  Of course this all for getting gizmo and skype working. For music, I deal with my Mac.

THanks

---

### Post by hydronucleus on 2006-08-17
modifed above message

---

### Post by Zarate on 2006-08-30
Hi all,

After 2 days of reading hundreds of posts about how to fix the microphone problem, finally capriccio made it work : ) A really *huge* thank you! I'm getting a lot of noise as well, but at least I can talk trough Skype. I have a Dell Inspiron 630m, by the record.

Thanks again, now I have time to fix everything else!

Cheers,

Zarate

ps: First post here, and first serious attempt to jump into GNU/Linux : )

---

### Post by extremecarver on 2006-11-02
I found out the problem  of the noise by lucky chance.

IT WAS THE Internal Modem, situated next to the bluetooth receiver. I unplugged it and since then I have no more noise. I don't use that modem anyhow. Take it out and save a few gramms.

---

### Post by z0r on 2006-12-15
My unpowered microphone is also very noisy when I'm running on AC power. It's usable running on battery, but barely.

> **extremecarver said:**
> IT WAS THE Internal Modem, situated next to the bluetooth receiver. I unplugged it and since then I have no more noise. I don't use that modem anyhow. Take it out and save a few gramms.

I tried removing my modem too: it had no effect at all.

My system: a Dell Inspiron 6400
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

My modem doesn't seem to show up in the output of lspci. Maybe it's a serial modem.

Between the crummy recording quality and software switching of the headphone and microphone jacks, this seems like a pretty dodgy sound card.

---

### Post by qiemem on 2006-12-22
Hey all,
Great thread! There's so many depressing 0 reply ones out on this problem... Ah well...

Anyway, tried capriccio's excellent suggestion but no success. I feel like I'm doing something really dumb, but I think I've working on this for too long...

Here's my amixer:
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 27 [87%] [on]
  Front Right: Playback 27 [87%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 18 [58%] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 26 [84%] [on]
  Front Right: Playback 26 [84%] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [on]
  Front Right: Playback 19 [61%] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [on] Capture [off]
  Front Right: Playback 31 [100%] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [on]
  Front Right: Capture 15 [100%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
headb@headb-laptop:~$ amixer|grep capture
headb@headb-laptop:~$ amixer|grep Capture
  Capture channels: Mono
  Capture channels: Mono
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Playback 31 [100%] [on] Capture [off]
  Front Right: Playback 31 [100%] [on] Capture [off]
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
  Capture channels: Mono
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]

```

Here's sound card info:
```

$ cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with STAC9750,51 at 0xdffffe00, irq 169
 1 [default        ]: USB-Audio - AK5370          
                      AKM              AK5370           at usb-0000:00:1d.3-1, full speed

```

Anyone see anything I might be missing?

---

### Post by extremecarver on 2006-12-22
> **z0r said:**
> My unpowered microphone is also very noisy when I'm running on AC power. It's usable running on battery, but barely.



I tried removing my modem too: it had no effect at all.

My system: a Dell Inspiron 6400
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

My modem doesn't seem to show up in the output of lspci. Maybe it's a serial modem.

Between the crummy recording quality and software switching of the headphone and microphone jacks, this seems like a pretty dodgy sound card.

Did you take out the actual modem, which is situated beneath the bluetooth slot? Its a chip of about 2x2cm.

---

### Post by econobeing on 2007-06-05
the mic not working was the only thing that was keeping me from taking windows off of my computer. but Capriccio's solution worked :D that made my week when my friend said "yeah i can hear you" on skype.

---

### Post by oxygenws on 2007-09-13
check this out: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
maybe "Update to the latest version of alsa" and "Manually Specify Module Parameters" sections are useful

---

### Post by hippz-420 on 2007-10-23
I have the same problem!

My line in ***nor*** my microphone will not work! Both worked perfectly off of Windows (as much as I hate to say it), but no matter what I do it won't work on Ubuntu. I have an HDA Intel STAC92xx chipset on a Dell Inspiron B120 Notebook, if that helps. On the side there is one line in/mic and one headphone jack. That might help too.

Anyone have the solution?

*PS, the mic I have was just a $9.00 Logitech microphone at future shop.

---

### Post by brucealdridge on 2007-10-24
works  for me :)

---

### Post by tweston on 2007-11-16
Sound capture with microphones is *definitely* a linux weak point. I've had trouble before and now with Gusty on a new desktop (Audio device: Intel Corporation 82801G), I can't get the microphone working. Everything else works great. Oh well, I can live w/o voip.

---

### Post by Yellow Pasque on 2007-11-17
For those having problems with mics in ALSA, check out OSS. That might support your audio card better than ALSA (I know OSS supports my M-Audio Revo input and headphone output jack while ALSA does not.) See my sig for OSS details.

---

### Post by Sspankyy on 2008-04-04
THANKS!
   B130 Same prob!  Fixed!  Thanks!

---

### Post by Warbo on 2008-07-02
Finally got my microphone going, thanks a lot! Next thing to get running is a Free softphone :P I'm looking at Empathy, Gizmo and Ekiga :)

---

