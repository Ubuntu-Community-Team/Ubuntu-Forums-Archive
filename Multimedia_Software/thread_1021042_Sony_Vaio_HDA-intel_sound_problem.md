---
title: "Sony Vaio HDA-intel sound problem"
date: 2008-12-24
forum: Multimedia Software
---

### Post by Firebat451 on 2008-12-24
I've been having trouble getting my sound working properly under Ubuntu-8.10.  None of the input or output jacks seem to work except for the center (yellow) jack.  Everything worked fine under windows so it seems to be software.  My first thought was to turn off the external AMP, but I can't find that option anymore under 8.10 in the alsamixer or in the volume control options (I did click preferences and the only channels that are there are master and PCM.)

I then tried following the guide found here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Here were my results:

aplay -l

card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v | less

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 01)
        Subsystem: Sony Corporation Device 81e7
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 902c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I found that the card is supported at alsa-project.org.

I manually installed the drivers according to the instructions but no change in symptoms. Moving on to "ALSA driver compilation, using alsa source" with module assistant.

Things seemed to work until the command 'sudo module-assistant a-i alsa-source'

I get the following error:

Build of the package alsa-source failed! How do you wish to proceed?

And here is the last bit of the build log where the errors took place:

/usr/src/modules/alsa-driver/acore/info.c: In function
‘resize_info_buffer’:
/usr/src/modules/alsa-driver/acore/info.c:90: error: implicit
declaration of function ‘PAGE_ALIGN’ 
make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2

When I go without module assistant I can't find the correct directory for the command:
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<insert driver> --with-oss=yes

The directory 'alsa-driver' does not exist and I can't find any directory with alsa in it where that command runs.  In the end, I have failed to install the drivers and I don't know where to go from here, any help is appreciated.

---

### Post by wolfen69 on 2008-12-24
have you looked at the help files that are specifically for HDA Intel? [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Firebat451 on 2008-12-25
Yes, though I ran into an error almost right from the start.  When I try to set up the instalation directories the command 'sudo cp ~/downloads/alsa* .' fails to work.

cp: cannot stat `/home/richard/downloads/alsa*': No such file or directory

I tried various variations, removing '/alsa* .' (because that is where I downloaded the files), adding the version (1.0.9rc), and I get either the previous error or:

cp: missing destination file operand after `/home/richard/downloads/alsa*'
Try `cp --help' for more information.

This is probably a simple sintax error I realize, but I don't know how to fix it.

---

