---
title: "Headphone Jack Sense - ALC883"
date: 2009-12-15
forum: Multimedia Software
---

### Post by verbal.kint on 2009-12-15
Is anyone experiencing the headphone jack sense problem since updating to 9.10?

Ive just installed Mint 8 and the jack sense has stopped working. I had this same issue in ubuntu 7.10 but it was fixed in 9.04.

Its a Realtek ALC883 sound card.

It's one of the most frustrating things that you can never quite be sure that bugs arent going to re-appear.

---

### Post by verbal.kint on 2009-12-15
So I ran through the ["Is ALSA using the correct model?"]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") steps in this troubleshooting guide

This is my soundcard info from the *lspci -v | less* command
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Packard Bell B.V. Device c016
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at a6340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```



This is my info from the alsa information script that it said to run: [HTML]http://www.alsa-project.org/db/?f=e8aca9c0910f3c8482019c0078ee9d6944e15ff6[/HTML]


I found the section in the [ALSA-Configuration.txt]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=e0e54a27fc10905a62bd649605ad2dbe8f8bfdbf;hb=ba283e5ded21f6585b1f15254d6b4df94638eac2") that matched my soundcards codec(ALC883)

and proceeded to put the different models into the alsa-base.conf file

These are the models that were listed:```

 895         ALC883/888

 896           3stack-dig    3-jack with SPDIF I/O

 897           6stack-dig    6-jack digital with SPDIF I/O

 898           3stack-6ch    3-jack 6-channel

 899           3stack-6ch-dig 3-jack 6-channel with SPDIF I/O

 900           6stack-dig-demo  6-jack digital for Intel demo board

 901           acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)

 902           acer-aspire   Acer Aspire 9810

 903           medion        Medion Laptops

 904           medion-md2    Medion MD2

 905           targa-dig     Targa/MSI

 906           targa-2ch-dig Targs/MSI with 2-channel

 907           laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)

 908           lenovo-101e   Lenovo 101E

 909           lenovo-nb0763 Lenovo NB0763

 910           lenovo-ms7195-dig Lenovo MS7195

 911           lenovo-sky    Lenovo Sky

 912           haier-w66     Haier W66

 913           3stack-hp     HP machines with 3stack (Lucknow, Samba boards)

 914           6stack-dell   Dell machines with 6stack (Inspiron 530)

 915           mitac         Mitac 8252D

 916           clevo-m720    Clevo M720 laptop series

 917           fujitsu-pi2515 Fujitsu AMILO Pi2515

 918           3stack-6ch-intel Intel DG33* boards

 919           auto          auto-config reading BIOS (default)
```


And this is my alsa-base.conf file:```
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N

#options test to get headphone jack sense working
options snd-hda-intel model=6stack-dig
```

 the line I was entering is the last line of code, I was substituting "6stack-dig" for the other models, saving the file then running *sudo alsa-force reload* command at the terminal and then trying the headphones


....unfortunately it didn't work, there was absolutely no difference for each of the model types I tried which got me wondering was I doing it correctly? 

Also I noticed in the alsa information script there was no library listed for the alsa version, is this something I should be worried about, there was one listed in the guide

```
!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    
Utilities version:  1.0.20

```

Does anyone have any suggestions?

---

### Post by markbuntu on 2009-12-16
Did you look in here:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

These problems are very hardware specific.

---

### Post by verbal.kint on 2009-12-17
I'll give some of them options a shot when I get home


If i know that it works in 9.04 could I boot into the live cd and extrapolate any information from that? Would the option be configured correctly in the alsa-base file?

---

