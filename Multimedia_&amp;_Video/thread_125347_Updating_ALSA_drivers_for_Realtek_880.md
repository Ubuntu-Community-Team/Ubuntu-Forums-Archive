---
title: "Updating ALSA drivers for Realtek 880"
date: 2006-02-03
forum: Multimedia &amp; Video
---

### Post by jwdeff on 2006-02-03
I have a MSI K8NGM2-FID (with the Geforce 6150 / nForce 430 chipset). It uses the Realtek 880 HD audio chip (aka snd-hda-intel, aka Azalia, aka ALC880). I've found people on other distributions that were able to get it to work by installing the 1.0.11rc3 ALSA drivers.  I've tried a whole mess of things to get these drivers installed. Not knowing what I'm doing has made it a bit more difficult. Any advice on getting these drivers installed and working? How does Ubuntu handle Alsa?

I'm running Kubuntu Breezy.

Thanks.

---

### Post by jwdeff on 2006-02-03
Here are some shortened versions of lsmod and lspci
 lsmod
...
evdev                   9088  0
snd_hda_intel          17428  4
snd_hda_codec         115328  1 snd_hda_intel
snd_pcm                78216  3 snd_hda_intel,snd_hda_codec
snd_timer              21764  2 snd_pcm
snd                    50752  10 snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10248  2 snd_hda_intel,snd_pcm
sr_mod                 15652  0
...
 
 lspci mostly shows a bunch of "0000:00:03.0 PCI bridge: nVidia Corporation: Unknown device 02fd (rev a1)"
 This repeats with devices numbers. There is nothing that says "sound" or "audio".
 
 To try to install the drivers I pretty much did this:
 rm -rf /lib/modules/$KERNEL_VER/kernel/sound/pci
 rm -rf /lib/modules/$KERNEL_VER/kernel/sound/acore
 rm -rf /lib/modules/$KERNEL_VER/kernel/sound/driver
 cd alsa-driver-1.0.11rc3
 ./configure
 make
 make install
 ./snddevices
 cd ..
 rm -rf /lib/libasound.*
 rm -rf /usr/lib/libasound.*
 cd alsa-lib-1.0.11rc3
 ./configure
 make
 make install
 cd ..
 cd alda-utils-1.0.11rc2
 ./configure
 make
 make install
 /etc/init.d/alsasound stop
 rm -rf /etc/asound.state
 rm -rf /dev/sndstat
 ln -s /proc/asound/oss/sndstat /dev/sndstat
 alsaconf/alsaconf
 
 This was essentially the install script from the realtek-linux-audiopack-3.5-6, but with the newer version of the alsa files.
 
 I also tried changing /etc/modprobe.d/sound as follows:
 options snd device_mode=0666
 alias snd-card-0 snd-hda-intel
 alias sound-slot-0 snd-hda-intel
 alias char-major-116 snd
 alias char-major-14 soundcore
 alias sound-service-0-0 snd-mixer-oss
 alias sound-service-0-1 snd-seq-oss
 alias sound-service-0-3 snd-pcm-oss
 alias sound-service-0-8 snd-seq-oss
 alias sound-service-0-12 snd-pcm-oss
 (this is from Alsa install instructions)
 And added snd-hda-intel into /etc/modules.
 I've restarted a number of times along the way, and randomly modprobed a number of things.

---

