---
title: "[B]no sound in breezy with my nm256AV[/B]"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by mosseguello on 2006-07-19
Hi, i've got an acer laptop. It's an old one, a travelmate722TX. I've never achieved any sound with it.. I've read many stuff in spanish and english but i got no success at all. First of all alsamixer is not running properly but i suppose  that's due to having no soundcards at all found.

I've read somewhere that i should have a try with ad1848 drivers as the problem is that

"Sound
Both Sounddriver-families (OSS and ALSA) can be used. With most Linux Distributions the auto-detection fails because the (Neomagic)PCI-Chip emulates an ISA-BUS-Soundcard.

Neomagic MagicMedia 256AV (NM2200) emulates a WSS(Windows Sound System)
if you set it up in the BIOS-Settings.

OSS Sound Driver

Driver "sb" is not working
Driver "es18xx" is not working
Driver "ad1848" & "adlib_card" (WSS) work fine, full-duplex
OSS-Sound must be set up manually and can not be auto-detected.


there's a slackware user saying this:


"Sound on HP 900
I recently used a Hewlett Packard 900 Omnibook with a Slackware based OS and was able to setup sound using alsaconf. The distro was Vector Linux 4.3. I also used Minislack 0.2 and managed sound the same way. Vector Linux 4.3 is based on Slackware 9.1 and Minislack 0.2 is based on Slackware 10.

When running alsaconf from the command line I was presented with a list of two items. The first item was the Neomagic 256 soundcard and the second was for ISA/PNP Legacy cards. I had no luck in selecting the Neomagic 256 soundcard from the list but struck gold when I selected item number two. A list of sound cards was then presented, all of the cards were selected by default. I selected the option to allow alsaconf to probe the cards on the list. After completion of the probe alsconf successfully configured the card as a Crystal Audio CS4232. It worked just fine.

I did experiment with a Fedora Core 1 distro and was able to configure the sound card as a CS4232 using sndconfig.

With Vector Linux 4.3 I had to run alsactl and alsactl store to use audio successfully."

Moreover, though i've got installed alsa-base alsa-utils y alsa-source it seemed i haven't got installed alsaconf. at the end i found a package and i downloaded it(v0.4.2 ). I had to load modules using modconf.

 lspci

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:04.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:04.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:04.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1251A (rev 01)
0000:00:06.1 CardBus bridge: Texas Instruments PCI1251A (rev 01)
0000:00:08.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
0000:02:00.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

lsmod
snd_nm256              67680  0 
snd_ac97_codec         72188  1 snd_nm256
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_nm256,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd                    48644  6 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
opl3sa2                11392  0 
mpu401                 26084  1 opl3sa2
ad1848                 29180  1 opl3sa2
sound                  70444  3 opl3sa2,mpu401,ad1848
soundcore               9184  2 snd,sound


/etc/modules

lp
mousedev
psmouse
irda
irtty-sir
ad1848
opl3sa2

dmesg

[4294671.679000] isapnp: Card 'NeoMagic MagicWave 3DX Sound System'
[4294671.679000] isapnp: 1 Plug & Play card detected total
[4294706.467000] ad1848/cs4248 codec driver Copyright (C) by Hannu Savolainen 1993-1996
[4294706.467000] ad1848: No ISAPnP cards found, trying standard ones...
[4294706.580000] opl3sa2: No PnP cards found
[4294722.765000] nm256: no ac97 is found!
[4294722.765000]   force the driver to load by passing in the module parameter
[4294722.765000]     force_ac97=1
[4294722.765000]   or try sb16 or cs423x drivers instead.
[4294722.765000] ACPI: PCI interrupt for device 0000:01:00.1 disabled
[4294722.765000] NeoMagic 256: probe of 0000:01:00.1 failed with error -6


Cheers 4 having a look

---

### Post by vitalif on 2007-03-12
Try OSS driver cs4232 - exactly cs4232, not snd_cs4232 (it's ALSA and is not compatible with NM256AV). The solution is as follows:
 - download kernel sources for your kernel and install them into /usr/src
 - cd /usr/src/linux
 - make mrproper
 - cp /boot/config ./.config
 - make oldconfig
 - make menuconfig
 - go to 'Device Drivers - Sound - Open Sound System' (and enable it, if it isn't)
 - enable 'OSS sound modules'
 - **disable** 'Microsoft Sound System support' (it conflicts with cs4232)
 - enable 'Crystal CS4232 based (PnP) cards'
 - enable 'Persistent DMA buffers' (it's for allocation of DMA buffers in the first 16 MB of memory - needed for compatibility with old cards)
 - enable 'MPU-401 support'
 - enable 'PSS (AD1848, ADSP-2115, ESC614) support'
 - exit menuconfig (of course, saving new configuration)
 - make && make install && make modules_install
 - edit /etc/modprobe.conf: add the line 'options cs4232 io=0x534 irq=5 dma=1 dma2=0', where 0x534 = 4+0x530, and 0x530, IRQ5, DMA=1 and DMA=0 are taken from the BIOS setup
 - edit /etc/modprobe.conf: add/edit the line 'alias sound-slot-0 cs4232'
 - reboot (-:
 - cat /dev/urandom > /dev/dsp and listen to the beautiful white noise from the speakers :-)

---

