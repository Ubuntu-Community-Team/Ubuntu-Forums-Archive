---
title: "Configuring system for OSS..."
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by blackcoatman on 2006-11-27
Hello people
I have Ubuntu Edgy and the m-Audio Audiophile 2492 soundcard. The sound worked with no problems, but there was no way to monitor the card input and listen at common sound (for example, xmms) at the same time, which is crucial for multitrack recording which I want to use, so as I can hear one channel and listen what I play over it.
Then I found the OSS drivers from [www.open-sound.com](www.open-sound.com). The most recent version supports this simultaneus monitoring feature. Xmms works fine for music too. But when I load a video in totem (totem-xine) or stream one on the net (youtube, apple trailers), there is no sound :/ How do I change core sound configuration so as to have everything playing through the oss drivers i have installed? The gnome sound configuration gives no sound output when testing at any option. But the card works, so are the drivers (as I said I can use both xmms and play the guitar :P). Which steps should I follow?

---

### Post by scoon on 2006-11-27
Hey there, 

The alsa-oss package could be a starting place to getting this worked out for you.

```
**ALSA wrapper for OSS applications**
This package contains a program loader, aoss, which wraps
applications written for OSS in a compatibility library,
thus allowing them to work with ALSA.

There are two ways of getting an application to work with
ALSA if the application was written for OSS. The first way
is to load the special ALSA drivers that emulate the OSS
kernel interface; these allow the application to open
/dev/dsp0 and other OSS device files. The second way is
to wrap the application in the libaoss library provided
in this package; the wrapper causes the application to
access native ALSA device files such as /dev/snd/pcmC0D0c
instead of OSS device files.

Use of the alsa-oss library is recommended over the use of
OSS-emulation drivers if you want to use ALSA's PCM plugin
layer.

ALSA is the Advanced Linux Sound Architecture:
    http://alsa.sourceforge.net
OSS is the free version of the Open Sound System.
```

-scoon

---

### Post by blackcoatman on 2006-11-27
I have this in mind, but I want it to work the other way around. I have alsa-oss and I need Alsa applications to work with OSS and not the other way around.
(btw the alsa drivers do not work - it seems they don't see the card, let alone that modprobing the modules needed - like ice1712 or snd-seq - gives me errors of 'undefined symbol')
Isn't there a file in which the outputs are configured? There is xorg for video, where's the sound configuration one? :P I
'll still look into alsa-oss a bit more.

---

### Post by scoon on 2006-11-27
Hey there, 

Can you post some more information about your system.  Things like, what kernel, cpu, output from lspci, the err msg that you get when trying to insert your cards module?

-scoon

---

### Post by blackcoatman on 2006-11-27
My CPU is Athlon64 3000+ venice socket (but using an x86 OS)

Soundcard is M-Audio Audiophile 2492

lspci output:

```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
05:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
05:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

```

The soundcard I mention is the " 05:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02) "

When I modprobe snd-ice1712 (after installing all drivers and following the directions alsa gives) i get:

```
bcman@all:~$ sudo modprobe snd-ice1712
FATAL: Error inserting snd (/lib/modules/2.6.17-10-generic/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.17-10-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_i2c (/lib/modules/2.6.17-10-generic/kernel/sound/i2c/snd-i2c.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.17-10-generic/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.17-10-generic/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.17-10-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_cs8427 (/lib/modules/2.6.17-10-generic/kernel/sound/i2c/snd-cs8427.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.17-10-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.17-10-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1712 (/lib/modules/2.6.17-10-generic/snd-ice1712.ko): Unknown symbol in module, or unknown parameter (see dmesg)
bcman@all:~$ 

```

... and dmesg gives... too much :P Generally, the sound has been a mess for all the time I'm fiddling with Linux, if things just go smoothly once, i'll be VERY very happy... 
Thanks in advance mate...

---

### Post by scoon on 2006-11-27
Hey there, 

I have had a couple of hard to setup cards in my day.  And to get them working or deciding to move on, this page was invaluable: [http://www.alsa-project.org]("http://www.alsa-project.org")

Searching for your card i found this here: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix")

Hopefully, that will help you as much as it helped me.  But I must tell you, I gave up on the turtle beach and bought a creative card that was supported.

I apologize for going back to alsa, but it really is the the preferred way for kernel sound.     

-scoon

---

### Post by blackcoatman on 2006-11-28
Seems so... but I think i will have to reinstall ubuntu becuase removing oss and installing the alsa drivers doesn't do the trick... they seems a bit ruined. At least I've learned that I needed toem-xine to play quictime in firefox :D I remember Fedora didn't even see the card. But thank for the feedback man :)

---

### Post by scoon on 2006-11-28
Hey there, 

No problem.  Please post back with your results.  I'd be curious to know.

-scoon

---

