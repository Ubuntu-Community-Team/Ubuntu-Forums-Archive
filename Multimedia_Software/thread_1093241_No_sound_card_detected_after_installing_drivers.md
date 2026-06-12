---
title: "No sound card detected after installing drivers"
date: 2009-03-11
forum: Multimedia Software
---

### Post by raul_7 on 2009-03-11
Hi all,
I am new to ubuntu/linux. I am a happy ubuntu user for last 3 weeks. Untill yesterday, my sound card was working fine but with relatively low volume at max level, so I decided to install Asus mobo audio drivers from Asus site, after installing and rebooting my sound card is not detected. I tried lot of solution after goofgling, but no use.

Please help me in this case since I dont want to reinstall ubuntu for this reason.

Thanks

this error I got while installing alsa drivers from asus

"'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #3 succeeded at 63 with fuzz 2.
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #10 succeeded at 1057 (offset -1 lines).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Leaving directory `/home/raul/Public/alsa/alsa-driver-1.0.14/usb/usx2y'
make[2]: Leaving directory `/home/raul/Public/alsa/alsa-driver-1.0.14/usb'
make[2]: Entering directory `/home/raul/Public/alsa/alsa-driver-1.0.14/pcmcia'
make[3]: Entering directory `/home/raul/Public/alsa/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/raul/Public/alsa/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/raul/Public/alsa/alsa-driver-1.0.14/pcmcia/vx'
make[3]: Leaving directory `/home/raul/Public/alsa/alsa-driver-1.0.14/pcmcia/vx'
make[2]: Leaving directory `/home/raul/Public/alsa/alsa-driver-1.0.14/pcmcia'
make[1]: Leaving directory `/home/raul/Public/alsa/alsa-driver-1.0.14'
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/raul/Public/alsa/alsa-driver-1.0.14 CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/raul/Public/alsa/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [/home/raul/Public/alsa/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/home/raul/Public/alsa/alsa-driver-1.0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [compile] Error 2
if [ -L /usr/include/sound ]; then \
rm -f /usr/include/sound; \
ln -sf /home/raul/Public/alsa/alsa-driver-1.0.14/include/sound /usr/include/sound; \
else \
rm -rf /usr/include/sound; \
install -d -m 755 -g root -o root /usr/include/sound; \
for f in include/sound/*.h; do \
install -m 644 -g root -o root $f /usr/include/sound; \
done \
fi
find /lib/modules/2.6.27-11-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.27-11-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
make[1]: Entering directory `/home/raul/Public/alsa/alsa-driver-1.0.14/acore'
mkdir -p /lib/modules/2.6.27-11-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.27-11-generic/kernel/sound/acore
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/raul/Public/alsa/alsa-driver-1.0.14/acore'
make: *** [install-modules] Error 1
Alsa driver compiling failed!"

Any help will be much appreciated !Hi all,
 this reason.

Thanks

---

### Post by joplass on 2009-03-11
Check your volume control beside that is what you should have done before install the driver.  Anyway check the volume control preference and chose pulseaudio to control your audio.  See if that helps.

---

### Post by raul_7 on 2009-03-11
Thanks for the reply. 
But right now when I type "aplay -l". No sound card is detected. I tried couple of solutions mentioned in sticky but does not work. After typing "lspci -v", I get following info
> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 8290
	Flags: bus master, slow devsel, latency 64, IRQ 5
	Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel



My setup is AMD+ati hd 4670 with asus motherboard.

Everything was working fine untill I installed asus audio drivers which removed original settings. 
The error report of which is posted in 1st post


Hope this helps

---

### Post by raul_7 on 2009-03-11
No help guys?
I have been asking this question for last 2 days.
Anyway can someone will tell me equivalent alsa drivers for ATI HD 4670 chipset.

Thanks

---

### Post by markbuntu on 2009-03-12
Obviously that asus driver is not working out for you so...you should remove and reinstall alsa to get things back the way they were for now


(1) Remove the ALSA packages

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

(3) Reboot.

---

### Post by raul_7 on 2009-03-13
> **markbuntu said:**
> Obviously that asus driver is not working out for you so...you should remove and reinstall alsa to get things back the way they were for now


(1) Remove the ALSA packages

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

(3) Reboot.
Thanks for the reply.
I tried the steps mentioned above, before as well. Also one more time after you mentioned.
But still no sound card detected....

---

