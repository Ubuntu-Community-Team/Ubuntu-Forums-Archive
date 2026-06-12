---
title: "No Sound with ENS1371 Card on Dell Dimension 4100"
date: 2010-08-07
forum: Multimedia Software
---

### Post by ZRTMWA on 2010-08-07
Something about my sound setup does not agree with Linux. I couldn't get sound on Puppy Linux and I can't get sound with Ubuntu either. I'm trying to use speakers through the headphone jack at the front of the tower (system unit, whatever you call the thing that houses the motherboard/ CD Drive etc.)

I tried the basic sound troubleshooting from this guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Since I still have the links up from it, I might as well share them with you.

1. This is the ALSA Information Script tailored to my settings: [http://www.alsa-project.org/db/?f=004e17869555c114d55b6e7827b445ee28f67529](http://www.alsa-project.org/db/?f=004e17869555c114d55b6e7827b445ee28f67529)

2. This is the ALSA Driver Configuration Guide. Scroll down to Line 587 for my card ( Module snd-ens1371): [http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bf24429b7a8f22711ac7a4b9ccce4ad26b50b8bd;hb=1cdf06bcd91e0c180efbc43f03ce0a1cf68ae8ec](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bf24429b7a8f22711ac7a4b9ccce4ad26b50b8bd;hb=1cdf06bcd91e0c180efbc43f03ce0a1cf68ae8ec)

3. This is just some general Hardware info:
> chris-desktop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 244MiB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.6
          size: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82815 815 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fc900000-fe9fffff memory:e4600000-f46fffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:11 memory:fd000000-fdffffff memory:e8000000-efffffff(prefetchable) memory:fe9f0000-fe9fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff memory:f4700000-f47fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: SMC2-1211TX
                vendor: Accton Technology Corporation
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth0
                version: 10
                serial: 00:04:e2:05:52:6b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:3 ioport:d800(size=256) memory:feaffc00-feaffcff memory:f4700000-f470ffff(prefetchable)
           *-multimedia
                description: Multimedia audio controller
                product: ES1371 [AudioPCI-97]
                vendor: Ensoniq
                physical id: c
                bus info: pci@0000:02:0c.0
                version: 09
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12
                resources: irq:9 ioport:df00(size=64)
           *-communication
                description: Serial controller
                product: 56K FaxModem Model 5610
                vendor: 3Com Corp, Modem Division
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=serial latency=0
                resources: irq:11 ioport:dff0(size=8)
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-usb
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:ef80(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0(size=16)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:eb:bb:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg


Hopefully someone out there is willing to decipher the gobs of info I have thrown at you and can tell me what's wrong. I did search for thread with the same card as mine but I couldn't find many very helpful ones.

[SIZE="5"]THANKS ;)[/SIZE]

---

### Post by ZRTMWA on 2010-08-07
Ugggh I must've screwed something up last night because now ALSA isn't even finding my soundcard. There's no input and the only output is "dummy". My volume indicator now has three dashes in front of it instead of sound waves. How to fix this and get sound?

---

### Post by ZRTMWA on 2010-08-08
Bumpitty

---

### Post by lidex on 2010-08-08
My suggestion is to upgrade your alsa install. Follow the alsa-upgrade link in my sig. Make sure to remove alsa-backports first, if installed.

---

### Post by Yellow Pasque on 2010-08-08
Try the latest ALSA. [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

You could also try OSS4: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

EDIT: lidex beat me to it because I forgot to click 'Post' before eating lunch :\

---

### Post by ZRTMWA on 2010-08-10
lidex: I downloaded the ALSA upgrades but and when I typed "aplay -l" into the terminal, it said that it couldn't find any soundcards. This is supported by the fact that my Speaker icon in the top right corner still has the three dashes in front of it and no card is listed in "Preferences". Also I didn't know what or how to delete backports before I installed do I just installed. What now?

Temüjin: I don't see my soundcard in the list of supported hardware for OSS4.

---

### Post by lidex on 2010-08-11
> **ZRTMWA said:**
> lidex: I downloaded the ALSA upgrades but and when I typed "aplay -l" into the terminal, it said that it couldn't find any soundcards. This is supported by the fact that my Speaker icon in the top right corner still has the three dashes in front of it and no card is listed in "Preferences". Also I didn't know what or how to delete backports before I installed do I just installed. What now?

Temüjin: I don't see my soundcard in the list of supported hardware for OSS4.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by lidex on 2010-08-11
> **Temüjin said:**
> 
EDIT: lidex beat me to it because I forgot to click 'Post' before eating lunch :\

Try putting the twinkies in/on your desk instead of in the freezer - it will save some time :p

---

### Post by ZRTMWA on 2010-12-12
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

Sory Lidex, I must've not seen this post. Here's the detailed info you requested:

[http://www.alsa-project.org/db/?f=64ef9f48eb0a024b2fc8176c7c3b47ce684ea4c9](http://www.alsa-project.org/db/?f=64ef9f48eb0a024b2fc8176c7c3b47ce684ea4c9)

In case you've forgotten, no sound cards are recognized, I've never had sound with ubuntu. The volume indicator has three dashed lines and it isn't muted. Thanks.

---

### Post by lidex on 2010-12-12
You have some added .conf files somewhere? Remove them.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
Remove this from alsa-base.conf or where ever you put it:
```
options snd-ens1371model=SoundBlaster PCI 64
```
Are you using the latest kernel:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot.**
Now this:
```
sudo modprobe snd-ens1371
```
Next post this output:
```
aplay -l
```

---

### Post by Yellow Pasque on 2010-12-12
> **lidex said:**
> Try putting the twinkies in/on your desk instead of in the freezer - it will save some time :p
I usually have medication for lunch :\ (and I abhor the existence of twinkies).

---

### Post by ZRTMWA on 2010-12-13
> **lidex said:**
> You have some added .conf files somewhere? Remove them.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
Remove this from alsa-base.conf or where ever you put it:
```
options snd-ens1371model=SoundBlaster PCI 64
```
Are you using the latest kernel:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot.**
Now this:
```
sudo modprobe snd-ens1371
```
Next post this output:
```
aplay -l
```

I'm having trouble finding the files I have to delete (first step). This is a screenshot of a search I didfor ens1371, the soundcard file in the wrong place. You'll probably have to zoom in 100% (default is 60%) to see read items:

[http://s779.photobucket.com/albums/yy80/ZRTMWA/?action=view&current=SoundScreenshot2.png](http://s779.photobucket.com/albums/yy80/ZRTMWA/?action=view&current=SoundScreenshot2.png)

Which of these do I delete?

Thanks.

---

### Post by lidex on 2010-12-14
No need to worry about those files, leave them alone in fact. The command given does the trick.

---

### Post by ZRTMWA on 2010-12-14
> **lidex said:**
> No need to worry about those files, leave them alone in fact. The command given does the trick.

The first set of code? I put it into the terminal and it said "rm: cannot remove `/home/chris/.asound*': No such file or directory"

and

"rm: cannot remove `/etc/asound.conf': No such file or directory"

so I don't know whats up.

---

### Post by lidex on 2010-12-14
> **ZRTMWA said:**
> The first set of code? I put it into the terminal and it said "rm: cannot remove `/home/chris/.asound*': No such file or directory"

and

"rm: cannot remove `/etc/asound.conf': No such file or directory"

so I don't know whats up.

Those two files are not in a default install but can be added to further tweak audio config. Terminal is telling you they don't exist, which is fine.

---

### Post by ZRTMWA on 2010-12-15
Sorry if I'm not understanding, like I mentioned earlier I'm a Linux (and computer) n00b, but it seems we've come full circle.

How do I get Ubuntu to recognize my sound card and get sound?

---

### Post by lidex on 2010-12-16
Open a terminal and run these commands:
```
sudo modprobe snd-ens1371
```
Next post this output:
```
aplay -l
```
(copy and paste the terminal output into your next post)

---

### Post by ZRTMWA on 2010-12-18
This is what it said after the first command:
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
FATAL: Error inserting snd_ens1371 (/lib/modules/2.6.32-21-generic/kernel/sound/pci/snd-ens1371.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And this was after the second:


aplay: device_list:235: no soundcards found...

---

### Post by lidex on 2010-12-20
> **ZRTMWA said:**
> This is what it said after the first command:
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
FATAL: Error inserting snd_ens1371 (/lib/modules/2.6.32-21-generic/kernel/sound/pci/snd-ens1371.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And this was after the second:


aplay: device_list:235: no soundcards found...

Run the first command again and then immediately after run this and post the output:
```
dmesg | tail
```

---

### Post by ZRTMWA on 2010-12-29
> **lidex said:**
> Run the first command again and then immediately after run this and post the output:
```
dmesg | tail
```

Sorry my correspondence has been so choppy.

chris@chris-desktop:~$ dmesg | tail
[879879.855665] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[912906.517538] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[913023.144072] wlan0: direct probe to AP 00:1c:10:19:2a:fc (try 1)
[913023.147624] wlan0: direct probe responded
[913023.147640] wlan0: authenticate with AP 00:1c:10:19:2a:fc (try 1)
[913023.150858] wlan0: authenticated
[913023.150934] wlan0: associate with AP 00:1c:10:19:2a:fc (try 1)
[913023.154161] wlan0: RX AssocResp from 00:1c:10:19:2a:fc (capab=0x411 status=0 aid=1)
[913023.154173] wlan0: associated
[917754.724344] snd_ens1371: Unknown parameter `model'
chris@chris-desktop:~$

---

### Post by lidex on 2010-12-29
It's still picking up that model switch. Did you delete it from alsa-base.conf?

What are these outputs:
```
cat /etc/modprobe.d/alsa-base.conf
dmesg | grep -i dmi
```

---

### Post by Jose Catre-Vandis on 2010-12-30
I'm going to chip in here with exactly the same problem. Dell Dimension 4100 with Ensoniq soundcard.  Setup was with Xubuntu ALTCD and with openbox WM.

aplay -l says no soundcards. There is no .asoundrc on my system, no pulseaudio, and alsa-base.conf is as standard install. dmesg | grep -i dmi gives:
```
[    0.000000] DMI 2.3 present
```

---

### Post by cascade9 on 2010-12-30
> **ZRTMWA said:**
> Something about my sound setup does not agree with Linux. I couldn't get sound on Puppy Linux and I can't get sound with Ubuntu either. I'm trying to use speakers through the headphone jack at the front of the tower (system unit, whatever you call the thing that houses the motherboard/ CD Drive etc.)

The 1371 sound card has front panel connectors, so AFAIK you cant get sound from a front panel headphone jack. 

The old 4100s I've seen have no front panel conector anyway, the only headphone jack is on the CD drive. You can get sound from the headphone jack on the CD drive ONLY when you play a CD. 

I know this isnt going to help your problem, sorry.

---

### Post by Jose Catre-Vandis on 2010-12-30
OK have had some success. I moved the PCI card up a couple of slots in the machine, and swapped it over with the network card. After the AGP Video card there is an empty slot, then the sound card, then an empty slot, then the network card, then an empty slot.

```
sudo rmmod snd-ens1371
sudo modprobe snd-ens1371
aplay -l
```

Produces a list of playback devices:
```
card 0: AudioPCI [Ensoniq AudioPCI], device 0:ES1371/1 [ES1371 DAC2/ADC]
Subdevices: 1/1
Subdevices #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1:ES1371/2 [ES1371 DAC1]
```

Adjusted levels with alsamixer

Tested with mp3 and CD, all working fine

Added module to /etc/modules for loading at boot

---

### Post by ZRTMWA on 2011-01-03
> **lidex said:**
> It's still picking up that model switch. Did you delete it from alsa-base.conf?

What are these outputs:
```
cat /etc/modprobe.d/alsa-base.conf
dmesg | grep -i dmi
```

Hahaha that's what I was saying, I never figured out how to delete it. 

This is the output:
**chris@chris-desktop:~$ cat /etc/modprobe.d/alsa-base.conf**
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
**chris@chris-desktop:~$ dmesg | grep -i dmi**
[    0.000000] DMI 2.3 present.
chris@chris-desktop:~$ 

> **cascade9 said:**
> The 1371 sound card has front panel connectors, so AFAIK you cant get sound from a front panel headphone jack. 

The old 4100s I've seen have no front panel conector anyway, the only headphone jack is on the CD drive. You can get sound from the headphone jack on the CD drive ONLY when you play a CD. 

I know this isnt going to help your problem, sorry.

That does help. Like I said, I'm a computer/Linux/Ubuntu n00b. So for now at least, I just have to delete whatever I screwed up with alsa earlier, then connect some speakers.

---

### Post by cascade9 on 2011-01-04
> **ZRTMWA said:**
> That does help. Like I said, I'm a computer/Linux/Ubuntu n00b. So for now at least, I just have to delete whatever I screwed up with alsa earlier, then connect some speakers.

More than I was hoping for. Good luck on fixing your problems ;)

---

