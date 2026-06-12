---
title: "No sound w/ HDA-Intel Realtek ALC883 - tried *everything*"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by lodp on 2006-06-23
EDIT 9/13/06: This thread is about sound output problems with Acer laptops that use the ALC883 or ALC882 sound chip. The problem has been resolved, the latest version of ALSA-Driver (1.0.13rc1 as of now) contains a fix. Just download and compile the package from alsa-project.org (read the comprehensive sound problems guide, or page 5 of this thread for instructions on that).

------------------

Hello everybody,

I'm running Kubuntu Dapper on an Acer 1652 Z with a HDA-Intel card (Realtek ALC883 chipset), and I'm getting no sound. Neither from the internal speakers nor from the headphone jack. The only thing that does work is recording (crappy with internal mic, fine with external).

I've dug through these forums for almost two weeks now, and I feel I've tried everything that anybody ever tried.

Many ppl having trouble with HDA-Intel cards get sound to work by compiling the latest ALSA drivers. Didn't work for me - I tried compiling 1.0.10rc4, 1.0.11rc4, 1.0.11, CVS (always the whole package, ran alsaconf afterwards, restarted), but that didn't change anything (even though the ALC883 chipset is supposed to be supported starting with 1.0.11rc1 according to changelogs). I always made sure th volume settings in alsamixer were turned way up.

I also tried compiling the new 2.6.17 kernel, which has ALSA 1.0.11rc4 built into it; no success.

Here's my lspci:

```
martin@martin-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
**0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)**
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 714a
0000:06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

lsmod | grep snd

```
martin@martin-laptop:~$ lsmod | grep snd
snd_hda_intel          19348  1
snd_hda_codec         143280  1 snd_hda_intel
snd_pcm                89480  2 snd_hda_intel,snd_hda_codec
snd_timer              25348  1 snd_pcm
snd                    55524  6 snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10760  2 snd_hda_intel,snd_pcm

```

cat /proc/asound/cards

```
martin@martin-laptop:~$ cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd000c000 irq 169

```

cat /proc/asound/version

```
martin@martin-laptop:~$ cat /proc/asound/version
**Advanced Linux Sound Architecture Driver Version 1.0.11.**
Compiled on Jun 20 2006 for kernel 2.6.15-25-386.

```

content of /etc/modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
**snd-hda-intel**
```


Is there something obvious that I could have overlooked? Like some huge "Make sound work" checkbox in the system settings? I also tried installing gnome, just to check. but no sound there as well..

---

### Post by lodp on 2006-06-29
*bump*

anybody? i still got no sound, have to boot windows for every little piece of media, which blows. also, (non-linux-convertee) friends are starting to make fun of me. please help before they start flinging empty beercans at me.

it seems there ARE people who've got the ALC883 chip working with kernel 2.6.17 (thus ALSA 1.0.11rc4) -- which i tried, but didn't work for me. so maybe it's not an ALSA problem?

---

### Post by Absurd on 2006-06-30
try this

go into the terminal and enter the following 

```
sudo gedit /etc/group
```

scroll down to where it says

```
audio:x:29
```
if you don't see your user name after "29", then change it to 
```
audio:x:29:<username>
```
reboot, and see if it works

---

### Post by lodp on 2006-07-01
thanks for the tip -- i already checked that some time, re-checked it now. i am part of the audio group, it seems.

i compiled alsa 1.0.12rc1 yesterday -- didn't change anything.

maybe this is relevant also:

when i boot ubuntu (or the gentoo live cd i just downloaded) i get some error messages right after the "uncompressing linux" step. it says

```
Can't allocate resource region 7 of bridge 0000:00:1c.0
```

and the same messages for regions 8 and 9 and bridges 0000:00:1c.1 and 0000:00:1c.2 respectively. could this be related to my problem? repeating here my lspci:

```
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P
rocessor to DRAM Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express R
oot Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High De
finition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P
CI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P
CI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P
CI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                                y) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                                y) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                                y) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                                y) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge                                                                 (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family                                                                ) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus                                                                 Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 714                                                                a
0000:06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controlle                                                                r
0000:06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                                                /8139C+ (rev 10)

```

---

### Post by LordRaiden on 2006-07-02
Are you using SPDIF? If you aren't try muting all references to SPDIF or IEC958 in alsamixer. On top of that, try muting/unmuting External Amplifier (if you have it) and make sure PCM is set to maximum and not muted.

---

### Post by lodp on 2006-07-02
i'm not using SPDIF (i had to look up what it was first, i have to admit), and i muted the IEC958 thing in alsamixer (i didn't couldn't adjust volume -- just mute it). also i didn't find anything about an external amplifier in alsamixer. PCM is turned way up.

didn't change anything, though.

i looked at your guide for troubleshooting sound issues, some really nice work you did there! i went through some of it, and i got "success" results everywhere .. but it's still not working. i really don't know where to go from here. do you think i should re-install kubuntu just to clean up? i really don't know what i might have messed up with all this week-long pointless tinkering ..

thanks for your time!

---

### Post by LordRaiden on 2006-07-02
Thanks for your comments.  I won't really recommend a reinstall, but if you feel that you won't lose anything to a reinstall (data) besides time, and you are willing to try it, go ahead. 

Before that though, part of me is itching to see if installing the intel8x0 module has any effect at all. You would have to install it the same way you did hda-intel except choose intel8x0. If that "does work" then you'll be home free.

---

### Post by lodp on 2006-07-03
i recompiled alsa-driver-1.0.12rc1, this time using the option "--with-cards:intel8x0"

then i did ```
modprobe snd-intel8x0
``` and entered snd-intel8x0 to /etc/modules and restarted. no sound, unfortunately.

lsmod | grep snd

```
snd_intel8x0           34076  0
snd_ac97_codec         94240  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            47776  0
snd_mixer_oss          18944  1 snd_pcm_oss
snd_pcm                81672  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    56292  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10760  2 snd_intel8x0,snd_pcm

```

what's strange is that i ran alsaconf after loading the intel8x0 driver, and it tells me "No supported PnP or PCI card found". Previously, it found the hda-intel card

also, when i try to run alsamixer, i get the following message:

```
function snd_ctl_open failed for default: No such device
```

the ALSA documentation says something about running the ./snddevices script in the course of installing -- i never figured out whether i had to do that or not -- do i?

---

### Post by LordRaiden on 2006-07-03
Your card is definitely hda-intel then. The ./snddevices is only for older version of alsa 0.9.4.

---

### Post by lodp on 2006-07-06
I just filed a bug on the ALSA-project tracker [HERE]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2261"). Browsing through the bugreports, it looks like I'm not the first one having problems getting sound with the ALC883 chip on a hda-intel card.

EDIT: The ALSA-project entertains a HG-repository for the latest development version, which reportedly has some recent modifications for the ALC883 support in it. I managed to download and compile the version, but "cat /proc/asound/version" still tells me I've got version 1.0.12rc1 installed, compiled two days ago. 

what I did was:
```
./hgcompile --with-cards=hda-intel
sudo make install
```

-- which seemed to go through fine. Any ideas?

---

### Post by LordRaiden on 2006-07-06
It makes sense since the HG version is basically a patch into 1.0.12rc1. Does it help any

---

### Post by lodp on 2006-07-07
so you think the HG stuff is installed, even though it still says 1.0.12rc1, and the compilation date hasn't changed?

if so, it didn't help. still no sound. recording on the internal mic works pretty well though. i *think* quality has improved on recording since v. 1.0.10.

bugreporters for ALC883 issues are told by the developers to try the snd-hda-intel module with the different model options to be found in ALSA-Configuration.txt. I found three module options: 3stack-dig, 6stck-dig, auto. What I did for testing them was:
```

sudo modprobe snd-hda-intel model=xxxx
```

then i tried playing a wav file with aplay. also i checked the alsamixer settings. did i do that the right way?

i've got another question: i'm not sure whether this matters at all, but i'm worried about the contents of /etc/modules and various files in /etc/modprobe.d/ - it's so confusing, i don't know how those might interfere with my problem

/etc/modprobe.d/sound

```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

```

/etc/modprobe.d/snd-hda-intel.modprobe
```
options snd-hda-intel
```


 /etc/modprobe.d/alsa-base
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7
# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /lib/alsa/modprobe-post-install snd-emu10k1 ; /sbin/modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /lib/alsa/modprobe-post-install snd-via82xx ; /sbin/modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth /sbin/modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth /sbin/modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a /sbin/modprobe --ignore-install snd-ad1816a $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 /sbin/modprobe --ignore-install snd-ad1848 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ad1848
install snd-adlib /sbin/modprobe --ignore-install snd-adlib $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-adlib
install snd-ad1889 /sbin/modprobe --ignore-install snd-ad1889 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ad1889
install snd-ali5451 /sbin/modprobe --ignore-install snd-ali5451 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 /sbin/modprobe --ignore-install snd-als100 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-als100
install snd-als300 /sbin/modprobe --ignore-install snd-als300 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-als300
install snd-als4000 /sbin/modprobe --ignore-install snd-als4000 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci /sbin/modprobe --ignore-install snd-armaaci $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi /sbin/modprobe --ignore-install snd-asihpi $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp /sbin/modprobe --ignore-install snd-atiixp $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 /sbin/modprobe --ignore-install snd-au1x00 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 /sbin/modprobe --ignore-install snd-au8810 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 /sbin/modprobe --ignore-install snd-au8820 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 /sbin/modprobe --ignore-install snd-au8830 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 /sbin/modprobe --ignore-install snd-azt2320 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 /sbin/modprobe --ignore-install snd-azt3328 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 /sbin/modprobe --ignore-install snd-ca0106 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 /sbin/modprobe --ignore-install snd-cmi8330 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci /sbin/modprobe --ignore-install snd-cmipci $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 /sbin/modprobe --ignore-install snd-cs4231 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 /sbin/modprobe --ignore-install snd-cs4232 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 /sbin/modprobe --ignore-install snd-cs4236 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 /sbin/modprobe --ignore-install snd-cs4281 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx /sbin/modprobe --ignore-install snd-cs46xx $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-cs5535audio /sbin/modprobe --ignore-install snd-cs5535audio $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs5535audio
install snd-darla20 /sbin/modprobe --ignore-install snd-darla20 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 /sbin/modprobe --ignore-install snd-darla24 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x /sbin/modprobe --ignore-install snd-dt019x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g /sbin/modprobe --ignore-install snd-echo3g $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x /sbin/modprobe --ignore-install snd-emu10k1x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 /sbin/modprobe --ignore-install snd-ens1370 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 /sbin/modprobe --ignore-install snd-ens1371 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 /sbin/modprobe --ignore-install snd-es1688 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx /sbin/modprobe --ignore-install snd-es18xx $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 /sbin/modprobe --ignore-install snd-es1938 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 /sbin/modprobe --ignore-install snd-es1968 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 /sbin/modprobe --ignore-install snd-es968 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 /sbin/modprobe --ignore-install snd-fm801 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x /sbin/modprobe --ignore-install snd-fm801-tea575x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 /sbin/modprobe --ignore-install snd-gina20 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 /sbin/modprobe --ignore-install snd-gina24 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic /sbin/modprobe --ignore-install snd-gusclassic $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme /sbin/modprobe --ignore-install snd-gusextreme $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax /sbin/modprobe --ignore-install snd-gusmax $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony /sbin/modprobe --ignore-install snd-harmony $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp /sbin/modprobe --ignore-install snd-hdsp $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm /sbin/modprobe --ignore-install snd-hdspm $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 /sbin/modprobe --ignore-install snd-ice1712 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 /sbin/modprobe --ignore-install snd-ice1724 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo /sbin/modprobe --ignore-install snd-indigo $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj /sbin/modprobe --ignore-install snd-indigodj $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio /sbin/modprobe --ignore-install snd-indigoio $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 /sbin/modprobe --ignore-install snd-intel8x0 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave /sbin/modprobe --ignore-install snd-interwave $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb /sbin/modprobe --ignore-install snd-interwave-stb $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 /sbin/modprobe --ignore-install snd-korg1212 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 /sbin/modprobe --ignore-install snd-layla20 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 /sbin/modprobe --ignore-install snd-layla24 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 /sbin/modprobe --ignore-install snd-maestro3 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia /sbin/modprobe --ignore-install snd-mia $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mia
install snd-miro /sbin/modprobe --ignore-install snd-miro $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart /sbin/modprobe --ignore-install snd-mixart $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona /sbin/modprobe --ignore-install snd-mona $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 /sbin/modprobe --ignore-install snd-mpu401 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle /sbin/modprobe --ignore-install snd-msnd-pinnacle $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav /sbin/modprobe --ignore-install snd-mtpav $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 /sbin/modprobe --ignore-install snd-nm256 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 /sbin/modprobe --ignore-install snd-opl3sa2 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 /sbin/modprobe --ignore-install snd-opti92x-ad1848 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 /sbin/modprobe --ignore-install snd-opti92x-cs4231 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x /sbin/modprobe --ignore-install snd-opti93x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 /sbin/modprobe --ignore-install snd-pc98-cs4232 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp /sbin/modprobe --ignore-install snd-pcsp $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr /sbin/modprobe --ignore-install snd-pcxhr $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf /sbin/modprobe --ignore-install snd-pdaudiocf $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus /sbin/modprobe --ignore-install snd-pdplus $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 /sbin/modprobe --ignore-install snd-portman2x4 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac /sbin/modprobe --ignore-install snd-powermac $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 /sbin/modprobe --ignore-install snd-pxa2xx-ac97 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-pxa2xx-i2sound /sbin/modprobe --ignore-install snd-pxa2xx-i2sound $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pxa2xx-i2sound
install snd-riptide /sbin/modprobe --ignore-install snd-riptide $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-riptide
install snd-rme32 /sbin/modprobe --ignore-install snd-rme32 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 /sbin/modprobe --ignore-install snd-rme96 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 /sbin/modprobe --ignore-install snd-rme9652 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 /sbin/modprobe --ignore-install snd-s3c2410 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 /sbin/modprobe --ignore-install snd-sa11xx-uda1341 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 /sbin/modprobe --ignore-install snd-sb16 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 /sbin/modprobe --ignore-install snd-sb8 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe /sbin/modprobe --ignore-install snd-sbawe $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi /sbin/modprobe --ignore-install snd-serialmidi $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 /sbin/modprobe --ignore-install snd-serial-u16550 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy /sbin/modprobe --ignore-install snd-sgalaxy $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes /sbin/modprobe --ignore-install snd-sonicvibes $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape /sbin/modprobe --ignore-install snd-sscape $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 /sbin/modprobe --ignore-install snd-sun-amd7930 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 /sbin/modprobe --ignore-install snd-sun-cs4231 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri /sbin/modprobe --ignore-install snd-sun-dbri $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident /sbin/modprobe --ignore-install snd-trident $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio /sbin/modprobe --ignore-install snd-usb-audio $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y /sbin/modprobe --ignore-install snd-usb-usx2y $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 /sbin/modprobe --ignore-install snd-vx222 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxpocket /sbin/modprobe --ignore-install snd-vxpocket $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront /sbin/modprobe --ignore-install snd-wavefront $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci /sbin/modprobe --ignore-install snd-ymfpci $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-hda-intel

```

/etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
snd-hda-intel

# Generated by sensors-detect on Sun Jun 25 13:32:30 2006
# I2C adapter drivers
i2c-i801
# I2C chip drivers
eeprom

```

---

### Post by LordRaiden on 2006-07-07
Add the mode=xxxx to  /etc/modprobe.d/snd-hda-intel.modprobe so that the line reads


```
options snd-hda-intel model=xxxx
```

---

### Post by lodp on 2006-07-07
hm .. i don't really know which model option to pick. none of them fits my setup:

> ALC882/883/885
	  3stack-dig	3-jack with SPDIF I/O
	  6stck-dig	6-jack digital with SPDIF I/O
	  auto		auto-config reading BIOS (default)

i don't have a digital out, just regular mic, line, headphone jack. so i figured just leaving it without a model option would be best.

i don't have to put the model option in all of those files and restart for testing that model option, do i? i just did a "modprobe snd-hda-intel model=xxxx"

---

### Post by LordRaiden on 2006-07-07
use the auto option.

---

### Post by Stan83 on 2006-07-17
Hello all,

I am not sure if this is of any revelence, but have a look heare, the sound chip seems to be simular. (exacly the same? )

[http://www.ryanheise.com/LW60/](http://www.ryanheise.com/LW60/)

I have a an identical sound problem with my ACER laptop, I will try to solve it as it is discribed. If you sure I am going to fail please let me know :)

---

### Post by mandrakethepenguin on 2006-07-17
I had the same problem w/ Breezy. Get into Volume Control by right clcking the Speaker Icon next to the time in GNOME and click Volume Control.  Go up to File or Edit and choose properties and make sure 'Front' is checked.  Then close out properties and turn 'Front' all the way up!  You should hear sound now and I apologize if my instructions were too indistinct, my Linux box is back in Ohio, and im in Florida on Windoze.

---

### Post by Stan83 on 2006-07-17
Done it allredy, the fierst thing I did acctually was to unmute everything :) using alsamixer, but anyway thank you.

---

### Post by lodp on 2006-07-28
> **Stan83 said:**
>  the sound chip seems to be simular. (exacly the same? )
[http://www.ryanheise.com/LW60/](http://www.ryanheise.com/LW60/)


the instructions here talk about the snd-azx module, which was replaced by snd-hda-intel, AFAIK. the module doesn't exist anymore in recent releases, and snd-hda-intel doesn't work for us..

---

### Post by LordRaiden on 2006-07-28
Check something
look for a .asoundrc file in your home directory (i.e. /home/lodp). If you find one, delete it, then reboot and try your sound.

---

### Post by agandar on 2006-07-30
hello,

I have an acer aspire 1652z and I have the same problem with hda-intel. I tried all in 'Comprehensive Sound Problem Solutions Guide v0.5e', but unsuccesfully.

I'm forcing to use often windows.

I haven't much hope that I can resolve this problem quickly and I'm thinking  to install another linux distro, but I like ubuntu!

---

### Post by Stan83 on 2006-07-30
> **agandar said:**
> 
I haven't much hope that I can resolve this problem quickly and I'm thinking  to install another linux distro, but I like ubuntu!

Well, I think it will not resolve your problem, since from what I know the problem is not with Ubuntu, but with the ALSA driver, but if you manage to solve it, please let us know :D

I have tried SUSE, since it has an opinion of doing well with laptops, but it was to no effect.
And before I even installed Ubuntu, I have tried FC5, since FC is what I normally use, or used to use.

---

### Post by lodp on 2006-07-31
> **LordRaiden said:**
> Check something
look for a .asoundrc file in your home directory (i.e. /home/lodp). If you find one, delete it, then reboot and try your sound.

didn't find a (-hidden, right?) file like that. anybody else?

---

### Post by jackphil on 2006-08-01
i tried everything too! and now i want to give up. the life is too short at all.

i wish, one day i waked up, dist-upgrade, then everything is right.

---

### Post by agandar on 2006-08-03
Today I have upgraded ubuntu and something changed.

The volume regulation doesn't work, it says there isn't a GStreamer plugin or a device for volume regulation.

I go to resources-preference-sound but there isn't any audio card.

?

---

### Post by lodp on 2006-08-04
are you talking about a hda-intel card (ALCXXX codec)? if not, i'm afraid this thread is the wrong place for your problem..

---

### Post by agandar on 2006-08-04
yes, hda-intel.

I have an acer aspire 1652 z

---

### Post by lodp on 2006-08-05
oh, sorry, i see you posted here before..

what does ```
cat /proc/asound/cards
```
tell you, and can you control the volume in alsamixer? by control the volume i mean: does alsamixer recognize a card - you don't actually have any sound, right?

---

### Post by agandar on 2006-08-05
cat /proc/asound/cards
--- no soundcards ---

alsamixer: function snd_ctl_open failed for default: No such device

before I updated ubuntu alsamixer worked, and recognized an hda-intel card, but I had no sound.

I don't remember what synaptic install the last time.

---

### Post by lodp on 2006-08-09
i think alsa comes with a script called snddevices, which is supposed to create sound devices. might want to try that -- unfortunately i haven't got much experience with that..

---

### Post by KLineD on 2006-08-09
My laptop comes with hda-intel card also. The weird thing is that sound was working from the first time I installed till yesterday. I was listening to some mp3s just fine, then I turned off the laptop. When I turned it on I didn't heard the drums sound and from there no sound at all.

I'm sure the volume is up both in the gnome panel and in alsamixer.  As soon as I get home I'll try some of the sugestions here and see what happens. I'll post my results.

---

### Post by KLineD on 2006-08-09
More weirdness... today I restarted my laptop to get some work done and no sound as always, but then when I was home, I started it again and the drums were there, and now there's sound everywhere.

I wish I knew what happened...:?:

---

### Post by lodp on 2006-08-10
KlineD, do you know which chipset you're using? can you post the output of

```
aplay -l
```

and

```
cat /proc/asound/card0/codec#0
```

and

```
cat /proc/asound/version
```

agandar, can you post the output of

```

lsmod|grep snd
```

---

### Post by capriccio on 2006-08-10
if you're losing your sound settings between reboots, make sure that after you've run alsaconf or whenever it is that your sound is working properly, that you store the settings: alsactl store.

---

### Post by sitedesign on 2006-08-10
I had the same problem, but I went into synaptic searched for alsa and selected re-install on them all. Done that then rebooted and now it all works fine again.


Just seems that maybe a config got broke during some updates.

Hope that helps.

---

### Post by KLineD on 2006-08-11
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

codec#0 stuff
```
Codec: SigmaTel ID 7634
Address: 0
Vendor Id: 0x83847634
Subsystem Id: 0x107b0461
Revision Id: 0x100101
Default PCM: rates 0x7e0, bits 0x0e, types 0x1
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Node 0x02 [Audio Output] wcaps 0xd0401: Stereo
  Power: 0x0
Node 0x03 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x14
Node 0x04 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM: rates 0x160, bits 0x0e, types 0x5
  Connection: 1
     0x07
Node 0x05 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM: rates 0x1e0, bits 0x0e, types 0x5
Node 0x06 [Audio Selector] wcaps 0x300901: Stereo
  Connection: 3
     0x02* 0x07 0x14
Node 0x07 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN
  Pin Default 0x40c003f0: [N/A] SPDIF In at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Power: 0x0
Node 0x08 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x424503f2: [N/A] SPDIF Out at Ext Front
    Conn = Optical, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 2
     0x05* 0x14
Node 0x09 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 1
     0x0f
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP
  Pin Default 0x01813022: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x00:
  Connection: 1
     0x0e
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x02a19021: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0e
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x90a70320: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0e
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x083f: IN OUT HP
  Pin Default 0x02214210: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x0e
Node 0x0e [Audio Selector] wcaps 0x300105: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x19 0x19]
  Connection: 1
     0x06
Node 0x0f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Connection: 5
     0x0b* 0x0c 0x0d 0x0a 0x11
Node 0x10 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00]
  Pincap 0x0810: OUT
  Pin Default 0x400003f1: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x12
Node 0x11 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x9033032e: [Fixed] CD at Int N/A
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x12 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x06
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Selector] wcaps 0x30090d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x09

```

/proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
```

Hope it helps

---

### Post by johan.t on 2006-08-19
Well, since I seem to have the same problem as the author of this thread, maybe I should post my specs as well? ](*,) 

```
johan@linux:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
kort 0: Intel [HDA Intel], enhet 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kort 0: Intel [HDA Intel], enhet 2: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
johan@linux:~$ cat /proc/asound/card0/codec#0
Codec: Realtek ALC883
Address: 0
Vendor Id: 0x10ec0883
Subsystem Id: 0x1025160d
Revision Id: 0x100002
Default PCM: rates 0x560, bits 0x0e, types 0x1
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  PCM: rates 0x560, bits 0x0e, types 0x1
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  PCM: rates 0x560, bits 0x0e, types 0x1
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  PCM: rates 0x560, bits 0x0e, types 0x1
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  PCM: rates 0x560, bits 0x0e, types 0x1
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  PCM: rates 0x560, bits 0x1e, types 0x1
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1e 0x1e]
  PCM: rates 0x160, bits 0x06, types 0x1
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  PCM: rates 0x160, bits 0x06, types 0x1
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  PCM: rates 0x560, bits 0x1e, types 0x1
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x9f 0x9f] [0x00 0x00] [0x1f 0x1f] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x083e: IN OUT HP
  Pin Default 0x0121111f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083e: IN OUT HP
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083e: IN OUT HP
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083e: IN OUT HP
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08173e: IN OUT HP
  Pin Default 0x01a19930: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x24: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08173e: IN OUT HP
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08173e: IN OUT HP
  Pin Default 0x01813131: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08173e: IN OUT HP
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x9983013f: [Fixed] Line In at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x99430120: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  PCM: rates 0x560, bits 0x0e, types 0x1
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b

```

```
johan@linux:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

```

```
johan@linux:~$ lsmod|grep snd
snd_hda_intel          18964  1
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

```

Really looking forward to a solution to this one!

---

### Post by snofix on 2006-08-22
Hi,

there is a patch available on the alsa-site to solve this ALC833 problem - it worked fine for me.
Just have a closer look at this thread:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104)

The patch file can be found in this thread:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2378](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2378)

---

### Post by mike4ubuntu on 2006-08-22
I have a similar problem with my Lenovo laptop.  Had sound working ok up until yesterday or so.  Where did you get alsaconf?  I don't have that program:

$ which alsaconf
$

$ sudo apt-cache show alsaconf
W: Unable to locate package alsaconf
E: No packages found

$ lspci | grep audio
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (
rev 04)

$ lsmod | grep snd
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_rawmidi            25504  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd                    55268  12 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,
snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

---

### Post by johan.t on 2006-08-22
> **snofix said:**
> Hi,

there is a patch available on the alsa-site to solve this ALC833 problem - it worked fine for me.
Just have a closer look at this thread:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104)

The patch file can be found in this thread:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2378](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2378)

Great new! But how do I do this? Sorry, but I don't have a clue how to apply this patch... ](*,)

---

### Post by lodp on 2006-08-22
[COLOR="Blue"][SIZE="6"]IT WORKS![/SIZE][/COLOR]

AWESOME! I just had sound for the first time in weeks. can't friggin believe it.

here's how i aplied that patch (there may be ways to do it without recompiling alsa-driver, but i couldn't figure that out right now):

1. i downloaded alsa.patch from [Here]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2378")
2. i downloaded and unpacked alsa-driver 1.0.12rc3 from alsa-project.net, unpacked it
3. i did
```
patch -p1 < /path/to/acer.patch
```
and when prompted for the file to patch i entered
```
/path/to/alsa-driver-1.0.12rc3/alsa-kernel/pci/hda/patch_realtek.c
```

4. i compiled the driver:

```

cd /path/to/alsa-driver-1.0.12rc3
./configure --with-cards=hda-intel
make
sudo make install
```

5. i added to /etc/modules:

```
snd-hda-intel model=ACER
```

to /etc/modprobe.d/snd-hda-intel.modprobe i added
```

options snd-hda-intel model=ACER
```

to /etc/modprobe.d/alsa-base i added:

options snd-hda-intel model=ACER

(there may be some redundancy in these entries)

5. i rebooted (unloading and reloading the modules didn't do the trick for some reason)

i guess the patch will be added to the next release candidate of ALSA, so there's an end to this nightmare..

EDIT 09/13/06: Alsa driver 1.0.13rc1 from alsa-project.org does indeed containt the modifications in the patch, according to the changelog. so you can skip steps 1 and 3, just download and compile the latest alsa driver. you probably won't even have to add the model option "acer" to all those files, like i did -- your card will probably be detected automatically.

---

### Post by the_stranger on 2006-08-22
I have no sound also maybe one of you could help me. I'm using the live CD right now. Once I the sound working I'll install it permanently.

here's some data:

lspci
```
ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 01)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:03:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
```

lsmod|grep snd
```
ubuntu@ubuntu:~$ lsmod|grep snd
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd_timer              25220  1 snd_pcm
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
```

aplay -l
```
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/asound/version
```
ubuntu@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
```

cat /proc/asound/card0/codec#0
```
ubuntu@ubuntu:~$ cat /proc/asound/card0/codec#0
cat: /proc/asound/card0/codec#0: No such file or directory
```

I'm guessing this last one might be the problem. Anybody have a solution? Please be as detailed as possible, my experience with Linux is only a couple of hours long. I'm still getting my bearings.

---

### Post by lodp on 2006-08-22
this thread is about sound problems with the ALC883 chip -- you better start a new thread with your problem...

that said, it really looks like the last one's your problem -- but i can't tell why there's no codec. you probably won't get rid of the problem dealing with the livecd. try the comprehensive sound problems solutions guide (sticky in this forum).

---

### Post by the_stranger on 2006-08-22
Sorry about hijacking your thread. I did start a my own, but it fell of the forum with no replies. I thought I might get a better response if I post in an existing thread.

I'm a little hesitent doing a permanent install before clearing up the sound problem. If it turns out the sound problem can't be fixed, then I would have to spend a huge amount of time reinstalling XP and all the programs I have right now.

---

### Post by iradi8 on 2006-08-23
Thanks be to the 'puter gods! For the first time since I got my Acer Aspire 1640z I have sound! Blessings be upon you and your electronic endeavors for posting the solution to this vexing problem!

---

### Post by lodp on 2006-08-24
i just read that the patch won't make it into ALSA 1.0.12 final, but it's likly going to be part of 1.0.13rc1.

ubuntu is lagging far behind in terms of alsa - dapper came with 1.0.10 or somthing -- this means a whole lot of acer laptops aren't going to work with ubuntu out-of-the-box for a long time, i guess...

---

### Post by Culito on 2006-08-24
I'm having sound problems too, and I've heard mention of a snddevices and alsaconf script.  I can't find either on my system.  Where are these scripts?

This is my annoying thread - I've been without sound for a couple of weeks now:
[http://ubuntuforums.org/showthread.php?t=238446](http://ubuntuforums.org/showthread.php?t=238446)

---

### Post by agandar on 2006-08-27
I have sound!

I used alsa.patch and alsa-driver 1.0.12rc3 from alsa-project.net, and now all works.

---

### Post by johan.t on 2006-08-29
lodp: You are my HERO!!! Thx! Everything seems to work after doing exactly what you wrote! Thx Thx! Thx! :-D  :-D  :-D

---

### Post by Helio Azevedo on 2006-08-30
Hi

I had the same problem that you describe. When I was giving up I have made a last try.

In start "System Setting" at KDE start menu. After that I access the tab "Hardware" present in "Sound System Configuration". At this tab I change "Select the audio devide" to "Open Sound System" and the sound came up.

in fact the sound is not good, bat I is bether than nothing. 

Do you find a more robust solution ?

Thanks

---

### Post by fern on 2006-08-30
Gosh!

Is this a joke?  None of the buntos can see my sound card in my laptop. Isn't Ubuntu the "polished and professional" operating system that will make Uncle Bill cry, the Linux for human beings?

Either this thing picks up my sound card and camera and it works or it doesn't.  I don't want to be running alsas, utils and whatever else hackers do.  Nothing against hackes, I love them, but I am just not one.

So, do I have to be a hacker to make this Ubuntu, Kubunto, Xubunto, Whateverbunto work?

Thanks

F

---

### Post by quail-linux on 2006-08-31
Hi lodp,
Thx for the great howto, it worked like a treat on my acer aspire 5601AWLMi laptop

---

### Post by StGeorge on 2006-09-08
Well this Post has been interesting.
It seems Ubuntu has a sound problem with laptops in general.
I am posting on this thread as I have a problem on my IBM Thinkpad 770X. As do other IBM users.
I have made my own post see:

[http://www.ubuntuforums.org/showthread.php?p=1425656#post1425656](http://www.ubuntuforums.org/showthread.php?p=1425656#post1425656)

I have had no replies yet and I am resigned to removing Ubuntu from my Laptop.

---

### Post by clearnitesky on 2006-09-12
I was following the instructions on the previous page, downloaded alsa, patched it, all good so far... I then run the configure script for alsa and get told:

```
checking for built-in ALSA... yes
configure: error: You have built-in ALSA in your kernel.
```

which makes sense... so does this mean I have to compile my own kernel or what? Being ubuntu I can't just uninstall the alsa-related packages because it wants to remove loads of other essential stuff that's dependant on it.

Anyone know what I'm meant to do?

---

### Post by mrojas73 on 2006-09-15
lodp, thanks to this thread I was able to make the sound on my new Acer Aspire 5601 AWLMI work.  There are a few steps that if added would make and excellent howto.  For example, one of the first problems I encountered was that I didn't have the kernel headers installed so I had to do a: sudo aptitude install linux-headers-`uname -r`.

The other problem was with the C++ compilers, I think that they have to be installed and they can be found in Synaptic Package Manager.

The link to the patch works great, but for different driver versions I found this nice place:[http://public.planetmirror.com/pub/alsa/driver/?sort=name&order=desc]("http://public.planetmirror.com/pub/alsa/driver/?sort=name&order=desc")

I think that you could make a very nice howto for new users with these chipsets.

I am sure that you know all of this already, but I didn't and I am sure that I lot of new user don't and may find your research very useful.

I hope that you put it together (the howto for 82801G Intel chipsets, acers) , and thank you very much for your instructions.

---

### Post by rosho on 2006-09-20
I thought the howto from the previous page didn't work but I forgot to install the **kernel headers** on my new install.
> sudo apt-get install linux-headers-686
(or with Synaptic)
So, yo must have the kernel headers package installed on the system and then you have to download the **alsa-driver-1.0.13rc2.tar.bz2** unpack it and just make the following:
> cd /path/to/your/directory/alsa-driver-1.0.13rc2
./configure
make
sudo make install
Without any patch or anything else.
Then I rebooted the laptop.
It worked on reboot.
That's it!
**[The laptop is an Acer Aspire 5601 AWLMi]**

---

### Post by ahiroito on 2006-09-25
hi, i had this same problem on my acer 3651 laptop. no sound with a realtek alc883 chip. it got "fixed" by installing the linux drivers from realtek (in case that helps somebody). "fixed" because i could hear sound, but only wavs and mp3s (oddly no oggs), and, what was more frustrating, looping endlessly the first 500 millisecs or so, until issuing "killall artsd" (nothing else would stop the horrid loop). so i came upon this thread and tried what lodp suggested, full of hope (actually all what was suggested). it didn't work, however. i realize my latter problem does not belong to the thread, but the problem i started with does. i'm hoping someone can redirect me to an answer before creating a thread, because i've tried several searchs (i'm starting to feel like lodp: "tried *everything*") and only found one similar posting on a mepis forum, without usable replies.
thanks in advance

---

### Post by lodp on 2006-09-26
so you successfully installed the VERY latest alsa-driver and it didn't work? (forget about the patching stuff that was on before -- the latest release contains the fix). 
if you've indeed got an alc883 chip, that's very surprising. have you made sure you haven't got channels muted in alsamixer? 

you should file a bug at the alsa-project, then.

---

### Post by ahiroito on 2006-09-26
that's right, the very latest (as for yesterday). but you got me wrong. before installation, i have no sound. after installation, i do have, as proven by the endless loop of the first millisecs of any wav or mp3. so you see, my problem ends differently, but starts like yours. i thought they could be related, but maybe i should start a new thread.

---

### Post by lodp on 2006-09-27
and you're positive you've got the ALC883 chip? sounds like you probably better file a bugreport at alsa-project.net...

did you try playing a .wav file with aplay <file>?

---

### Post by dannystaple on 2006-10-05
Have any of you guys patching it, complaining, or fixing it actually filed an ubuntu launchpad bug report against dapper? The bug fixers really dont view threads, and if something is so broken only a donwload or hackery will fix it, that is a bug report, which means that it would eventually end up fixed for real.

If you start here [http://launchpad.net/distros/ubuntu](http://launchpad.net/distros/ubuntu) then you will be able to report bugs there.

If you have filed upstream bugs (to alsa) then also do make sure you mention that in the report, as well as the patch you have found.

Cheers
Danny

---

### Post by ahiroito on 2006-10-10
to close my episode: i installed debian testing (etch) and the sound worked like a charm with the weekly snapshot (i tried first the beta 3 release but that didn't work either). i know it' s not exactly a solution, but it's what got my acer laptop working (sounding?). strangely, this debian reports the audio device as "ATI Technologies Inc SB450 HDA Audio (rev 01)", whereas for ubuntu and windows it's the realtek alc883 :S
thanks anyway lodp.

---

### Post by fhonny on 2006-10-13
Hello,
i dont read all pages for this post, but it seems you didn't forward a lot with this mm ?

As i was searching what audio drivers to use with ALC883 on an atx MSI K9N-Neo, i found this forum, and i also found that : [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I dont know if using realtek's drivers is the only way but...
I try it know

---

### Post by Chxta on 2006-10-14
Hi all, I just got an Aspire 1640z yesterday and came across this problem. Saw Lodp's post and followed it every step of the way. But I still can't hear anything!

Any tips please?

---

### Post by Chxta on 2006-10-17
[Chxta's World]("http://chxta.blogspot.com/2006/10/ubuntu-rocks.html")

I knew that the open source community can't fail me, and they never do. Sound problem solved, and an up to speed distro to the bargain.

What I did?

In my terminal, I ran: *gksu “update-manager -c -d”*

Waited for 28 minutes while it upgraded the distro, and voila. I'm runnning Ubuntu 6.10 Edgy Eft with crystal clear sound!

For the support I have to thank [The HowTo Geek]("http://www.howtogeek.com").

---

### Post by emuzesto on 2006-10-29
I just dist-upgraded my Acer Aspire 3680 from Dapper to Edgy, which worked perfect. The only thing that did not work was the sound. Will this fix work for Edgy too?

---

### Post by Memilen on 2006-11-01
Hi! 

Thanks for the solution for this problem. 
The sound on my Lenovo 3000 V100 worked just fine with dapper, but went quiet with edgy eft. 
This solution worked just fine, just downloaded latest alsa-drivers (1.0.13) and it worked wonders.

/Fredrik

---

### Post by emuzesto on 2006-11-02
Problem solved. My headphones got sound (something they didn't have in Dapper) and that is even better as I can listen with headphones when working at school.

---

### Post by viking777 on 2006-11-18
Hi all, I am a relative newcomer to Ubuntu and this is my first post on the forums.

I have exactly the same problem with the ALC883 soundcard as described by lodp, but I couldn't make his solution work. When I try to configure the alsa driver (I have 1.0.13rc3 and it is unpacked in the /opt/ directory) I get the following error message:

"The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)".

At my present level of knowledge I have no idea what to do about this, are they asking me to compile kernels? I sure hope not because that is way above my level of expertise. 

Anyway if any of you know a way around this I would sure like to know.

Incidentally I must say that in every other respect the Ubuntu 6.06 install went extremely smoothly, far and away the easiest I have ever done and certianly quicker than windows! 

I don't know if this is of any import, but I am using an Intel dual core 64 bit processor and a 64 bit version of Kubuntu.

---

### Post by viking777 on 2006-11-18
I had a go at upgrading to Edgy as others have done but all I get is:

extracting '/tmp/tmpSjxfIH/edgy.tar.gz'
authenticate '/tmp/tmpSjxfIH/edgy.tar.gz' against '/tmp/tmpSjxfIH/edgy.tar.gz.gpg'
can't find DistUpgradeViewGtk


Another dead end (for me anyway).

---

### Post by viking777 on 2006-11-18
OK I have got a couple of stages further down the road to sound but have reached another stumbling block. 

I now have the kernel headers installed and have configured the alsa-driver as instructed but when I issue the 'make' command I just get 'make: command not found'.

So what have I to do about that?

I will tell you what I do about that I install the 'make' utility with aptitude. I then complete the make and make install routine on the sound driver and I still dont have any sound!

Oh well.

---

### Post by quail-linux on 2006-11-18
> **viking777 said:**
> OK I have got a couple of stages further down the road to sound but have reached another stumbling block. 

I now have the kernel headers installed and have configured the alsa-driver as instructed but when I issue the 'make' command I just get 'make: command not found'.

So what have I to do about that?

I will tell you what I do about that I install the 'make' utility with aptitude. I then complete the make and make install routine on the sound driver and I still dont have any sound!

Oh well.

have you installed "build-essential" ?  if not type:
> sudo apt-get install build-essential

HTH

---

### Post by viking777 on 2006-11-19
Hi quail-linux and thanks for the reply.

> **quail-linux said:**
> have you installed "build-essential" ?  if not type:


HTH



I did that (it returned a lot of errors relating to clam antivirus, though I dont know what that has to do with it).

Then what? I still have no sound.

---

### Post by viking777 on 2006-11-19
Well I just updated from 6.06 to 6.1 and that has made no difference either, I still have no sound.

I just tried the build-essential command again as well, it says I have the latest version already.

---

### Post by viking777 on 2006-11-27
I am beginning to wonder if my problem with sound is simply to do with the sound being muted and not being able to unmute it. 

At the end of the alsa-driver install it warns you about this and says that you can unmute the sound by using alsamixer or amixer which are both part of the alsa-utils package. I didn't bother with this because I thought that unmuting would simply be a matter of opening kmix and turning up the volume. I now believe there may be more to it than this. I compared kmix on my new laptop with that of my old setup and found that the new one has no master channel, what I was turning up up using the tray icon was the PCM channel.

I therefore set about installing alsa-utils, and after a huge batltle with unresolved dependencies I finally got it installed (as well as alsa-lib).

I then tried running the mixer controls and got:

"sudo /usr/src/alsa-utils-1.0.13/alsamixer/alsamixer"

"alsamixer: function snd_ctl_open failed for default: No such device"

and:

"sudo /usr/src/alsa-utils-1.0.13/amixer/amixer"
"amixer: Mixer attach default error: No such device"

So if muted sound is indeed the problem (and I am still not certain of that) then I can't unmute it anyway.

Does anyone have any idea as to where I might go from here?

---

### Post by baserg on 2006-11-28
This is working
[http://dev-board.com/?p=16](http://dev-board.com/?p=16)

---

### Post by viking777 on 2006-11-28
> **baserg said:**
> This is working
[http://dev-board.com/?p=16](http://dev-board.com/?p=16)

Thanks for the reply.

I already had all 3 alsa packages installed and when I ran the patch it said that it was already installed as well (though I don't know when that happened!)

I recompiled alsa-driver in the manner stated (the only difference to the way I had done it before was the --with-oss=yes option),I ran alsaconf and I added the extra line to /etc/modprobe.d/alsa-base (since I don't have etc/modprobe.conf or /etc/modules.d/alsa which were the two files given in the article) I rebooted and _ _ _ _ ???

Nothing:( 

Never mind at least it gave me some hope for a while!!

---

### Post by baserg on 2006-12-01
> **viking777 said:**
> Thanks for the reply.

I already had all 3 alsa packages installed and when I ran the patch it said that it was already installed as well (though I don't know when that happened!)

I recompiled alsa-driver in the manner stated (the only difference to the way I had done it before was the --with-oss=yes option),I ran alsaconf and I added the extra line to /etc/modprobe.d/alsa-base (since I don't have etc/modprobe.conf or /etc/modules.d/alsa which were the two files given in the article) I rebooted and _ _ _ _ ???

Nothing:( 

Never mind at least it gave me some hope for a while!!

I'm using pardus linux version  1.1 ([http://www.pardus.org.tr/eng/index.html]("http://www.pardus.org.tr/eng/index.html")) on Asus a3e it's working.Your  problem is maybe "etc/modprobe.conf"

---

### Post by kurashige on 2007-01-10
hey, I have ACER Travelmate Laptop, I have no problem regarding the sound becoz its running fine with the laptop speakers. But the only problem i everytime I put the headphone/headset (the laptop speaker automatically turns off and the laptop detects the jack because in the tray it says "A Jack has been plugged.")  but the problem is, ther's no sound coming out of the headset/headphone.  ](*,) 

what seems to be the problem? I tried it n three different headphones but still the same problem occurs (the problem is not the headset)

I also check the hardware and drivers of my laptop (no question mark "?" on the drivers) so that means its not the driver. And also, my first time I tried to use my headphone and watch a movie and is working but after almost two weeks now, its not working with the headphone.... help me please. thanks!

I am thinking if does microsoft update affects the drivers or hardware of my laptop because its working fine on my first try to use the headphone slot, but between that day until now, the only thing I did was update all the security update of my laptop. andnothing more. :-k  help please...

---

### Post by Mateo on 2007-01-25
My headphone slot got switched with my microphone slot somehow.  So I get headphones out of the mic slot fine.  It's not a big deal... I'd like to switch if possible, but it's not a big deal.  I know that it did switch, because if I untoggle the headphones in Volume Control the sound turns off of the mic slot.

---

### Post by Trippen Out on 2007-02-11
i have this chip on my motherboard .. gigabyte 965p s3 and id like to use the spdif on it but the red light is not on i dont have any other way to hook up this card except via spdif .. so how do i turn it on :)

---

### Post by undy on 2007-03-05
> **emuzesto said:**
> I just dist-upgraded my Acer Aspire 3680 from Dapper to Edgy, which worked perfect. The only thing that did not work was the sound. Will this fix work for Edgy too?

I've just bought an Acer Aspire 3680 (3683WXMi). I found that headphones worked but the built-in speakers didn't work with Edgy Eft. I upgraded to ALSA 1.0.13 and added the suggested entry to /etc/modules, but still no joy. Then I tried ALSA 1.1.14rc2 and still no joy.

Whilst playing around with ALSAMIXER, I realised that some of the playback options were muted - unmuting "surround" fixed up the problem with the pc speakers ("pc speaker" has no effect). Its possible that this was my problem all along and I didn't need to upgrade my alsa.

Andy

---

### Post by The_Tankengine on 2007-03-06
> **Trippen Out said:**
> i have this chip on my motherboard .. gigabyte 965p s3 and id like to use the spdif on it but the red light is not on i dont have any other way to hook up this card except via spdif .. so how do i turn it on :)

I have the same motherboard and my sound doesn't work at all.  I tried to install the realtek-linux-audiopack-4.05f, and it seemed like everything was fine.  Then it opened alsaconf and says "No supported PnP or PCI card found.  Would you like to probe legacy ISA sound cards/chips?"  So I hit yes, then it just says "ok" and thats it.  What can i do to get sound working?

I have the latest feisty upgrades and the 2.6.20.1 kernel as well.

---

### Post by david2b on 2007-03-07
Sound is working with my Lenovo 3000 v100, with Feisty Herd 4. I've just have to activate the modem in bios. Boot sequence is longer, but it's worth being patient!

---

### Post by topgi on 2007-03-10
Undi,
it works indeed ! There is no need to install Alsa 1.0.13 in Edgy. The current driver 1.0.11, works like a charm if you enable the "Surround".

Thanks,

---

### Post by amerinero on 2007-03-15
The same for me. After trying with different Alsa versions it didn't work until I enabled the "Surround" channel. 

[COLOR="SeaGreen"][SIZE="5"]But finally works!!!
[/SIZE][/COLOR]

---

### Post by iamaqbot on 2007-04-13
> **rosho said:**
> I thought the howto from the previous page didn't work but I forgot to install the **kernel headers** on my new install.

(or with Synaptic)
So, yo must have the kernel headers package installed on the system and then you have to download the **alsa-driver-1.0.13rc2.tar.bz2** unpack it and just make the following:
cd /path/to/your/directory/alsa-driver-1.0.13rc2
./configure
make
sudo make install

Without any patch or anything else.
Then I rebooted the laptop.
It worked on reboot.
That's it!
**[The laptop is an Acer Aspire 5601 AWLMi]**

Regarding this post.

I installed the linux headers and tried to run the alsa-driver 1.0.13.rc2.tar.bz2 and this is what happened:
timmy@timmy-laptop:~$ cd /tmp/alsa-driver-1.0.13rc2
timmy@timmy-laptop:/tmp/alsa-driver-1.0.13rc2$ ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I've tried to find similarly named C++ items but only found gcc and installed it but i'm still getting a no when it checks for all of these

any ideas? I feel like i'm almost there, if someone could help me out that would be great

---

### Post by xpax on 2007-04-27
i found a link [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Perhaps somebody can explain it..


AC'97 Audio Codecs (Software)


	RTL8100B(L)/RTL8100C(L)/RTL8101L/RTL8139C(L)
RTL8139C(L)+/RTL8139D(L)/RTL8100(L)
RTL8130/RTL8139B(L) (Software)
	High Definition Audio Codecs (Software)

---

### Post by neoyahuu on 2007-05-03
i do this but still no luck. But finally i try enable surround channel
[http://www.opocot.com/ubuntu-feisty-sound-problem-solved/](http://www.opocot.com/ubuntu-feisty-sound-problem-solved/)
and WORKS fine.

---

### Post by Nighto on 2007-05-15
Hi, i have an Acer Travalmate 2480 with ALC883, pc speakers works good with Surround activated, but i got no sound at all in headphone jack (which is very bad because this speakers sucks). Any clues?

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0b:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

---

### Post by Nighto on 2007-05-15
> **Nighto said:**
> Hi, i have an Acer Travalmate 2480 with ALC883, pc speakers works good with Surround activated, but i got no sound at all in headphone jack (which is very bad because this speakers sucks). Any clues?

googling around, i found this in a *windows*-users forum:
> I have the same problem like you.
I have acer travelmate 2480. In my situation ,for restart audio jack, select "standby" windows. After , "on" my computer, and the audio jack is ok.
i tried the same here in ubuntu... and it worked!
:guitar:

---

### Post by gunbladeiv on 2007-06-02
try this.

download this version of alsa alsa-driver-1.0.14rc2.tar.bz2
compile it from source.then do command alsamixer on the konsole

then unmute all the item. to un mute it press M.it works for me.

:popcorn:

---

### Post by viniciuscarvalho on 2007-11-11
Hello there! I've just got a new notebook from the company and sound is not working. I tried to use the guide at page 6, but I'm getting errors on compiling the driver. I've installed the linux headers and libc6-dev, it passes configure but make throws errors. Also, the command patch -p1 < /path/to/acer.patch is not asking for any files to patch it seems to be patching the correct one, dunno how it found it though.




```

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
checking for current directory... /home/vinicius/alsa-driver-1.0.12rc3
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.22-14-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.22-14-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
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
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.22-14-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
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
checking for video_get_drvdata... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.12rc3
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... hda-intel
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...

```

make output

```

vinicius@cybertron:~/alsa-driver-1.0.12rc3$ make
make dep
make[1]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/acore'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/ioctl32'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/ioctl32'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/oss'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/oss'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/seq'
make[4]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/seq/instr'
make[4]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/seq/instr'
make[4]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/seq/oss'
make[4]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/seq/oss'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/acore/seq'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/acore'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/i2c'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/i2c/other'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/i2c/other'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/i2c'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/mpu401'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/mpu401'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/opl3'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/opl3'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/opl4'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/opl4'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/pcsp'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/pcsp'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/vx'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers/vx'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/drivers'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/ad1816a'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/ad1816a'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/ad1848'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/ad1848'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/cs423x'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/cs423x'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/es1688'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/es1688'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/gus'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/gus'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/msnd'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/msnd'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/opti9xx'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/opti9xx'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/sb'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/sb'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/wavefront'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa/wavefront'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/isa'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/synth'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/synth/emux'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/synth/emux'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/synth'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ac97'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ac97'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ali5451'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ali5451'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/asihpi'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/asihpi'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/au88x0'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/au88x0'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ca0106'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ca0106'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/cs46xx'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/cs46xx'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/cs5535audio'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/cs5535audio'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/echoaudio'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/echoaudio'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/emu10k1'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/emu10k1'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/hda'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/hda'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ice1712'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ice1712'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/korg1212'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/korg1212'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/mixart'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/mixart'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/nm256'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/nm256'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/pcxhr'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/pcxhr'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/pdplus'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/pdplus'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/riptide'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/riptide'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/rme9652'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/rme9652'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/trident'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/trident'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/vx222'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/vx222'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ymfpci'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci/ymfpci'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pci'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/usb'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/usb/usx2y'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/usb/usx2y'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/usb'
make[2]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pcmcia'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/vinicius/alsa-driver-1.0.12rc3/pcmcia/vx'
make[3]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pcmcia/vx'
make[2]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3/pcmcia'
make[1]: Leaving directory `/home/vinicius/alsa-driver-1.0.12rc3'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/vinicius/alsa-driver-1.0.12rc3  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.o
In file included from /home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.c:1:
/home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.inc:13,
                 from /home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.c:1:
/home/vinicius/alsa-driver-1.0.12rc3/include/adriver.h:721: error: static declaration of ‘jiffies_to_msecs’ follows non-static declaration
include/linux/jiffies.h:264: error: previous declaration of ‘jiffies_to_msecs’ was here
/home/vinicius/alsa-driver-1.0.12rc3/include/adriver.h:740: error: static declaration of ‘msecs_to_jiffies’ follows non-static declaration
include/linux/jiffies.h:266: error: previous declaration of ‘msecs_to_jiffies’ was here
In file included from /home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.inc:13,
                 from /home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.c:1:
/home/vinicius/alsa-driver-1.0.12rc3/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/vinicius/alsa-driver-1.0.12rc3/include/adriver.h:1077: error: too many arguments to function ‘pci_save_state’
/home/vinicius/alsa-driver-1.0.12rc3/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/vinicius/alsa-driver-1.0.12rc3/include/adriver.h:1081: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/vinicius/alsa-driver-1.0.12rc3/acore/memalloc.o] Error 1
make[2]: *** [/home/vinicius/alsa-driver-1.0.12rc3/acore] Error 2
make[1]: *** [_module_/home/vinicius/alsa-driver-1.0.12rc3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2


```


Any suggestions?

Best regards

---

### Post by pus on 2007-11-14
same problem as viniciuscarvalho

---

### Post by Yellow Pasque on 2007-11-14
I solved my audio problems by using OSS and removing that cursed ALSA. See my signature for more detail.

---

### Post by kobudodave on 2007-12-20
I found this and it got me up and running... Well worth your time I think as it has a GOOD chance of working:

[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html")


Hope it works.

---

### Post by AlecJ on 2008-01-11
I have the same sound card, it works with Gutsy but no surround.

I followed this howto and it works great.

Upgrade to the alsa-1.0.15 driver

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This works great on Gutsy but NOT on mythbuntu?? will kill all sound and lose the ident of any sound card, work in progress

---

### Post by lucas5800 on 2008-04-03
You should go to [http://www.realtek.com.tw/downloads/downloadsView.aspx](http://www.realtek.com.tw/downloads/downloadsView.aspx)
?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false
an install the linux driver and the update. It should fix it. I'm having the same problem with the same sound card but sound works in KDE not in GNOME. Confusing setup still trying 
to set up the driver.
](*,)

---

### Post by warp99 on 2008-04-03
> **AlecJ said:**
> 
This works great on Gutsy but NOT on mythbuntu?? will kill all sound and lose the ident of any sound card, work in progress

Would you like to know the reason why? Kernel modues cx88-alsa and saa7134-alsa for certain analog tuner cards are from ALSA included with the driver build package, but they have to be compiled as kernel modules. Since the kernel modules were not compiled the analog tuner cards will not work with the updated drivers.

---

### Post by areksz on 2008-04-03
I've problem with this sound card too. When i try to mute front speakers, headphones mute too, do You know what I should do to repair it??

---

### Post by Yellow Pasque on 2008-04-03
> **areksz said:**
> I've problem with this sound card too. When i try to mute front speakers, headphones mute too, do You know what I should do to repair it??
I would try upgrading ALSA and making sure alsa-base file is configured properly. See [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by estaticd on 2008-04-08
sudo apt-get install gnome-alsamixer and unmuting the front/center/surround channels fixed my problem... this is on a gigabyte p965-ds3 with realtek 883 chipset running ubuntu hardy heron beta.

---

