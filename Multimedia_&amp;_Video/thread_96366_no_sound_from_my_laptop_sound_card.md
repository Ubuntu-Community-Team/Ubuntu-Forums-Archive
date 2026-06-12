---
title: "no sound from my laptop sound card"
date: 2005-11-28
forum: Multimedia &amp; Video
---

### Post by mistergq on 2005-11-28
I am using a Gateway 4520 notebook that I purchased a year ago.  I just started using Ubuntu (first ever linux install on any of my computers).

According to Ubuntu, my sound device is an Intel 82801db-ch4. I do not have any sound. If I use the external volume control next (on the case), a little window pops up showing the voluming going up and down. Since Gateway does not support linux on this laptop, I am out of luck there.

I have tried many different things mentioned on this board including compiling a new kernel to 2.6.14 Vanilla Kernel (latest) + ck Patchset (Enhanced Performance kernel) and that has not helped.

Any suggestions?


Thanks.

---

### Post by jliedeka on 2005-11-28
Since you have the kernel sources, check out the file ALSA-Configuration.txt in the Documentation/sound directory.  I was able to get my sound working after following what it said.  I have the same chip as you.

When you "lsmod | grep snd", can you see the modules loaded?  I actually had the modules loaded but no sound.  Also, try alsamixer, see if the external amplifier is muted (it should be) and the master and pcm are unmuted.

---

### Post by mistergq on 2005-11-28
Thanks for the help

The Ismod report came back as
snd_intel8x0           30816  2
snd_ac97_codec         83580  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            46112  0
snd_mixer_oss          16896  2 snd_pcm_oss
snd_pcm                78600  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21892  1 snd_pcm
snd                    49252  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10376  2 snd_intel8x0,snd_pcm


As to the suggestions about the txt file, I am not sure what I am supposed to do.  I am a newbie to this.  Can you be more specific with what I need to change and what the terminal commands are.

I checked the mixer and all the settings are as you requested.

---

### Post by jliedeka on 2005-11-29
I was suggesting you read the file and try the suggestions.  E.g. "less /usr/src/linux-source-2.6.12/Documentation/sound/alsa/ALSA-Configuration.txt"

Ignore the stuff about compiling a kernel.  The stock Ubuntu kernel has everything you need.  First try the stuff under "DEVFS support".  That's what helped me.  If it still doesn't work, try the options under the "Module snd-intel8x0".    You would use them in /etc/modprobe.d/alsa-base.

Here is my alsa-base file:

# snd module options
options snd device_mode=0660
# autoloader aliases
alias char-major-116 snd
alias snd-card-0 snd-intel8x0
options snd-intel8x0 id="first"

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

---

### Post by mistergq on 2005-11-30
question:

I realized that I did not have the devfs in my build.  So I went to synaptic manager and added it.  Then it said that I had to add devfs=mount to lilo.conf for it to load.  Well, I don't lilo.conf in /etc/lilo.conf. 

So how do I know if it is loaded?

---

### Post by mistergq on 2005-11-30
ok, so I figured out that I am using Grub and how to add devfs=mount to that.  Not sure how to check to make sure it is properly loaded, but that is besides the point.

Now my qustion is where is devfsd.conf.  I did a search for that file, but can't find it. I have devfsd installed, so I am not sure what to do next.

---

### Post by mistergq on 2005-11-30
for some reason, when I did the search, I could not find the devfsd file.  Well, I found it in the etc/devfsd folder.  So I modified the devfsd.conf with the recommendation in the alsa document, specifically I added:

LOOKUP snd MODLOAD ACTION snd
REGISTER ^sound/.* PERMISSIONS root.audio 660
REGISTER ^snd/.* PERMISSIONS root.audio 660

I will try the next configuration you recommended.

---

### Post by jliedeka on 2005-11-30
I'm not entirely clear on the whole devfs->udev thing.  I thought udev was being used by  kernels but adding the LOOKUP... stuff to /etc/devfs/conf.d solved my problem.

I think modern kernels actually use udev.  As far as I can tell from the boot scripts, udev is usedm not devfs.  Still, adding that file is the thing I did before my sound started working.

Make sure your alsa-base file looks like what I said above and run
sudo /etc/init.d/alsa-utils restart

See if that helps.

---

### Post by mistergq on 2005-11-30
well, I did what you said and now linux does not even recognize my sound card.  I replaced my alsa-base file with this

```
# snd module options
options snd device_mode=0660
# autoloader aliases
alias char-major-116 snd
alias snd-card-0 snd-intel8x0
options snd-intel8x0 id="first"

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

This is what my old alsa-base looked like.
```
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7
# Load optional modules above their base modules
install snd modprobe --ignore-install snd && { modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a modprobe --ignore-install snd-ad1816a && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 modprobe --ignore-install snd-ad1848 && /lib/alsa/modprobe-post-install snd-ad1848
install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 modprobe --ignore-install snd-als100 && /lib/alsa/modprobe-post-install snd-als100
install snd-als4000 modprobe --ignore-install snd-als4000 && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci modprobe --ignore-install snd-armaaci && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi modprobe --ignore-install snd-asihpi && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp modprobe --ignore-install snd-atiixp && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 modprobe --ignore-install snd-au1x00 && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 modprobe --ignore-install snd-au8810 && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 modprobe --ignore-install snd-au8820 && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 modprobe --ignore-install snd-au8830 && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 modprobe --ignore-install snd-azt2320 && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 modprobe --ignore-install snd-azt3328 && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 modprobe --ignore-install snd-ca0106 && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci modprobe --ignore-install snd-cmipci && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 modprobe --ignore-install snd-cs4231 && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 modprobe --ignore-install snd-cs4232 && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 modprobe --ignore-install snd-cs4281 && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx modprobe --ignore-install snd-cs46xx && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-darla20 modprobe --ignore-install snd-darla20 && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 modprobe --ignore-install snd-darla24 && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x modprobe --ignore-install snd-dt019x && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g modprobe --ignore-install snd-echo3g && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x modprobe --ignore-install snd-emu10k1x && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 modprobe --ignore-install snd-ens1370 && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 modprobe --ignore-install snd-ens1371 && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 modprobe --ignore-install snd-es1688 && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx modprobe --ignore-install snd-es18xx && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 modprobe --ignore-install snd-es1938 && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 modprobe --ignore-install snd-es1968 && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 modprobe --ignore-install snd-es968 && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 modprobe --ignore-install snd-fm801 && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x modprobe --ignore-install snd-fm801-tea575x && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 modprobe --ignore-install snd-gina20 && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 modprobe --ignore-install snd-gina24 && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic modprobe --ignore-install snd-gusclassic && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme modprobe --ignore-install snd-gusextreme && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax modprobe --ignore-install snd-gusmax && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony modprobe --ignore-install snd-harmony && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel modprobe --ignore-install snd-hda-intel && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp modprobe --ignore-install snd-hdsp && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm modprobe --ignore-install snd-hdspm && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 modprobe --ignore-install snd-ice1712 && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 modprobe --ignore-install snd-ice1724 && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo modprobe --ignore-install snd-indigo && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj modprobe --ignore-install snd-indigodj && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio modprobe --ignore-install snd-indigoio && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 modprobe --ignore-install snd-intel8x0 && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave modprobe --ignore-install snd-interwave && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb modprobe --ignore-install snd-interwave-stb && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 modprobe --ignore-install snd-korg1212 && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 modprobe --ignore-install snd-layla20 && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 modprobe --ignore-install snd-layla24 && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 modprobe --ignore-install snd-maestro3 && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia modprobe --ignore-install snd-mia && /lib/alsa/modprobe-post-install snd-mia
install snd-miro modprobe --ignore-install snd-miro && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart modprobe --ignore-install snd-mixart && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona modprobe --ignore-install snd-mona && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 modprobe --ignore-install snd-mpu401 && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle modprobe --ignore-install snd-msnd-pinnacle && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav modprobe --ignore-install snd-mtpav && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 modprobe --ignore-install snd-nm256 && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 modprobe --ignore-install snd-opti92x-ad1848 && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 modprobe --ignore-install snd-opti92x-cs4231 && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x modprobe --ignore-install snd-opti93x && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 modprobe --ignore-install snd-pc98-cs4232 && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp modprobe --ignore-install snd-pcsp && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr modprobe --ignore-install snd-pcxhr && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf modprobe --ignore-install snd-pdaudiocf && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus modprobe --ignore-install snd-pdplus && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 modprobe --ignore-install snd-portman2x4 && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac modprobe --ignore-install snd-powermac && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 modprobe --ignore-install snd-pxa2xx-ac97 && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-rme32 modprobe --ignore-install snd-rme32 && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 modprobe --ignore-install snd-rme96 && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 modprobe --ignore-install snd-rme9652 && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 modprobe --ignore-install snd-s3c2410 && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 modprobe --ignore-install snd-sa11xx-uda1341 && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 modprobe --ignore-install snd-sb16 && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 modprobe --ignore-install snd-sb8 && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe modprobe --ignore-install snd-sbawe && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi modprobe --ignore-install snd-serialmidi && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 modprobe --ignore-install snd-serial-u16550 && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy modprobe --ignore-install snd-sgalaxy && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes modprobe --ignore-install snd-sonicvibes && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape modprobe --ignore-install snd-sscape && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 modprobe --ignore-install snd-sun-amd7930 && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 modprobe --ignore-install snd-sun-cs4231 && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri modprobe --ignore-install snd-sun-dbri && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident modprobe --ignore-install snd-trident && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio modprobe --ignore-install snd-usb-audio && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y modprobe --ignore-install snd-usb-usx2y && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 modprobe --ignore-install snd-vx222 && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxp440 modprobe --ignore-install snd-vxp440 && /lib/alsa/modprobe-post-install snd-vxp440
install snd-vxpocket modprobe --ignore-install snd-vxpocket && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront modprobe --ignore-install snd-wavefront && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci modprobe --ignore-install snd-ymfpci && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2


```

Did I not include enough in the new alsa-base file?

---

### Post by jliedeka on 2005-12-01
The stuff in the default file essentially tries every sound card driver until one works.  That's fine for when things work out of the box.

Try adding the same alsa-base file to /etc/modutils.  Also, run the command:
sudo update-modules

That will actually create /etc/modules.conf from the files in /etc/modprobe.d (I think).  I put my alsa-base file in two places.  I don't think it should be necessary but it's worth a try.

Then try re-starting alsa-utils.

---

### Post by mistergq on 2005-12-02
[QUOTE=jliedeka]The stuff in the default file essentially tries every sound card driver until one works.  That's fine for when things work out of the box.

Try adding the same alsa-base file to /etc/modutils.  Also, run the command:
sudo update-modules

That will actually create /etc/modules.conf from the files in /etc/modprobe.d (I think).  I put my alsa-base file in two places.  I don't think it should be necessary but it's worth a try.

Then try re-starting alsa-utils.[/QUOTE] Okay here is what I did.

in /etc/modprobe.d, the alsa-base file is this one:
```
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7
# Load optional modules above their base modules
install snd modprobe --ignore-install snd && { modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a modprobe --ignore-install snd-ad1816a && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 modprobe --ignore-install snd-ad1848 && /lib/alsa/modprobe-post-install snd-ad1848
install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 modprobe --ignore-install snd-als100 && /lib/alsa/modprobe-post-install snd-als100
install snd-als4000 modprobe --ignore-install snd-als4000 && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci modprobe --ignore-install snd-armaaci && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi modprobe --ignore-install snd-asihpi && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp modprobe --ignore-install snd-atiixp && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 modprobe --ignore-install snd-au1x00 && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 modprobe --ignore-install snd-au8810 && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 modprobe --ignore-install snd-au8820 && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 modprobe --ignore-install snd-au8830 && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 modprobe --ignore-install snd-azt2320 && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 modprobe --ignore-install snd-azt3328 && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 modprobe --ignore-install snd-ca0106 && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci modprobe --ignore-install snd-cmipci && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 modprobe --ignore-install snd-cs4231 && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 modprobe --ignore-install snd-cs4232 && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 modprobe --ignore-install snd-cs4281 && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx modprobe --ignore-install snd-cs46xx && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-darla20 modprobe --ignore-install snd-darla20 && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 modprobe --ignore-install snd-darla24 && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x modprobe --ignore-install snd-dt019x && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g modprobe --ignore-install snd-echo3g && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x modprobe --ignore-install snd-emu10k1x && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 modprobe --ignore-install snd-ens1370 && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 modprobe --ignore-install snd-ens1371 && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 modprobe --ignore-install snd-es1688 && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx modprobe --ignore-install snd-es18xx && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 modprobe --ignore-install snd-es1938 && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 modprobe --ignore-install snd-es1968 && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 modprobe --ignore-install snd-es968 && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 modprobe --ignore-install snd-fm801 && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x modprobe --ignore-install snd-fm801-tea575x && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 modprobe --ignore-install snd-gina20 && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 modprobe --ignore-install snd-gina24 && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic modprobe --ignore-install snd-gusclassic && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme modprobe --ignore-install snd-gusextreme && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax modprobe --ignore-install snd-gusmax && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony modprobe --ignore-install snd-harmony && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel modprobe --ignore-install snd-hda-intel && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp modprobe --ignore-install snd-hdsp && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm modprobe --ignore-install snd-hdspm && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 modprobe --ignore-install snd-ice1712 && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 modprobe --ignore-install snd-ice1724 && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo modprobe --ignore-install snd-indigo && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj modprobe --ignore-install snd-indigodj && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio modprobe --ignore-install snd-indigoio && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 modprobe --ignore-install snd-intel8x0 && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave modprobe --ignore-install snd-interwave && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb modprobe --ignore-install snd-interwave-stb && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 modprobe --ignore-install snd-korg1212 && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 modprobe --ignore-install snd-layla20 && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 modprobe --ignore-install snd-layla24 && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 modprobe --ignore-install snd-maestro3 && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia modprobe --ignore-install snd-mia && /lib/alsa/modprobe-post-install snd-mia
install snd-miro modprobe --ignore-install snd-miro && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart modprobe --ignore-install snd-mixart && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona modprobe --ignore-install snd-mona && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 modprobe --ignore-install snd-mpu401 && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle modprobe --ignore-install snd-msnd-pinnacle && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav modprobe --ignore-install snd-mtpav && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 modprobe --ignore-install snd-nm256 && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 modprobe --ignore-install snd-opti92x-ad1848 && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 modprobe --ignore-install snd-opti92x-cs4231 && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x modprobe --ignore-install snd-opti93x && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 modprobe --ignore-install snd-pc98-cs4232 && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp modprobe --ignore-install snd-pcsp && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr modprobe --ignore-install snd-pcxhr && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf modprobe --ignore-install snd-pdaudiocf && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus modprobe --ignore-install snd-pdplus && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 modprobe --ignore-install snd-portman2x4 && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac modprobe --ignore-install snd-powermac && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 modprobe --ignore-install snd-pxa2xx-ac97 && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-rme32 modprobe --ignore-install snd-rme32 && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 modprobe --ignore-install snd-rme96 && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 modprobe --ignore-install snd-rme9652 && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 modprobe --ignore-install snd-s3c2410 && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 modprobe --ignore-install snd-sa11xx-uda1341 && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 modprobe --ignore-install snd-sb16 && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 modprobe --ignore-install snd-sb8 && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe modprobe --ignore-install snd-sbawe && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi modprobe --ignore-install snd-serialmidi && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 modprobe --ignore-install snd-serial-u16550 && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy modprobe --ignore-install snd-sgalaxy && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes modprobe --ignore-install snd-sonicvibes && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape modprobe --ignore-install snd-sscape && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 modprobe --ignore-install snd-sun-amd7930 && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 modprobe --ignore-install snd-sun-cs4231 && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri modprobe --ignore-install snd-sun-dbri && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident modprobe --ignore-install snd-trident && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio modprobe --ignore-install snd-usb-audio && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y modprobe --ignore-install snd-usb-usx2y && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 modprobe --ignore-install snd-vx222 && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxp440 modprobe --ignore-install snd-vxp440 && /lib/alsa/modprobe-post-install snd-vxp440
install snd-vxpocket modprobe --ignore-install snd-vxpocket && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront modprobe --ignore-install snd-wavefront && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci modprobe --ignore-install snd-ymfpci && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

```

In etc/modutils, the alsa-base file is this one:

```
# snd module options
options snd device_mode=0660
# autoloader aliases
alias char-major-116 snd
alias snd-card-0 snd-intel8x0
options snd-intel8x0 id="first"

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

```

Then, I opened up a terminal window and did 
```
 sudo update-modules
```

Then I restartred alsa-utils
```
 sudo /etc/init.d/alsa-utils restart 
```

Then I restarted the computer.

No sound, so I opened a terminal window, typed alsamixer and muted every option.  Put a CD in, started turning each thing back on, and soundly, my sound was blaring.

I am not sure which step worked, but that is how I got my sound to work.  I need to print! :eek: :p

Thank you jliedeka for all your help.  You rock! :D

---

### Post by mistergq on 2005-12-02
BTW: you must have external amplifer muted.  In alsamixer, you mute options by type M on each individual option.

---

