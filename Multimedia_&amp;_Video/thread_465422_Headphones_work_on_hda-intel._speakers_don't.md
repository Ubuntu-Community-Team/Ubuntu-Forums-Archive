---
title: "Headphones work on hda-intel. speakers don't"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by ohme on 2007-06-05
Hello. I've tried a lot of things (compiling latest beta version of alsa, configuring alsa-base, different combinations of the mixer, what have you). I don't remember all of them.  

I'm on a lg laptop (p1 series), sound card=hda intel  5.1 CH with SRS. no acpi updates in the linux acpi site for my laptop (or any lg at all if i remember correctly). but i don't think it's the problem because fans work normally. 

and most important - the system does recognize the sound card. I know this because I can hear everything in headphones. sound just does not appear to work from the speakers. 

i've also try to unmark the headphones in the mixer, but no influence on the speakers.

last detail - i'm on the latest distro (7.04).  

is there a way to make it work?

---

### Post by vkrmsv on 2007-06-07
same problem with my acer 5583.
the head phones work perfectly but not the speakers!

---

### Post by NeoLithium on 2007-06-07
Open up a terminal (Applications -> Accessories -> Terminal) and type:
```
alsamixer
```
Turn up all the volumes and make sure nothing is muted (If there's something with MM on the bottom of the voume control, highlight it and press m)  Fixed my laptop quickly.

---

### Post by gjumi on 2007-06-20
Same problem here on a LG xnote with Ubuntu 7.04 and the latest alsa.

aplay shows

xcl@xcl-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CMI9880 Digital [CMI9880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Does this mean that the computer is thinking the modem is the speaker?

I'll use this chance since it's my first post and say thanks to many people here who have shared their problems and solutions.  I've learned a lot during these days.

---

### Post by ohme on 2007-06-21
As said, alsamixer is not the sollution in my case. I've tried openning them all up, muting one and leaving the rest open, and other combinations.  aplay -l gives in my case :

card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by BillDozer on 2007-06-21
You're not by any chance using a port replicator? 

I had a similair problem on a Dell D600 when it was plugged into the port replicator there was only sound from the earphone but when it was out of the port replicator (docking station) it was ok.

---

### Post by guyvdb on 2007-06-21
i have the exact same problem with the exact same device...

---

### Post by gjumi on 2007-06-21
No port replicators here...

---

### Post by jeffisawesome on 2007-06-21
Do you mean the on-board speakers?  I have the same card and its works with external speakers, but the on-board speakers don't make a peep.

---

### Post by guyvdb on 2007-06-21
> **jeffisawesome said:**
> Do you mean the on-board speakers?  I have the same card and its works with external speakers, but the on-board speakers don't make a peep.

exacly

also, the mic doesn't work

i didn't have this problem with pre-feisty version :(

---

### Post by eggdeng on 2007-06-21
The fix for the original poster's LG P1 is as follows.
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add the line ```
options snd-hda-intel model=lg
```
For other models, check out [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

---

### Post by guyvdb on 2007-06-21
```
options snd-hda-intel model=fujitsu
```
that worked for me on my fujitsu siemens amilo xi 1526
you'll need to compile the newest ALSA release though and the mic still doesnt work. at least i   have working speakers now.

---

### Post by gjumi on 2007-06-22
The eggdeng's advice didn't work for me, neither his link. :(

---

### Post by eggdeng on 2007-06-22
Sorry to hear that, gjumi. Looking at your aplay output, I see that yours is a completely different chip whereas the original poster has a very similar chip to mine. I don't know if you followed up the suggestion in the thread I linked to,which refers to the alsa documentation which you should find at
```
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
```
I am using alsa 1.0.10rc3 on Dapper but the section dealing with your chip is probably the same. It reads 
```
CMI9880
	  [COLOR="Red"]minimal[/COLOR]	3-jack in back
	  [COLOR="Red"]min_fp[/COLOR]	3-jack in back, 2-jack in front
	  [COLOR="Red"]full[/COLOR]		6-jack in back, 2-jack in front
	  [COLOR="Red"]full_dig[/COLOR]	6-jack in back, 2-jack in front
```
So, I would try editing /etc/modprobe.d/alsa-base by adding, for example
```
options snd-hda-intel model=[COLOR="Red"]minimal[/COLOR]
```
or whichever of the given options best suits your configuration. Remember you will probably need to reboot for changes to take effect.

---

### Post by gjumi on 2007-06-22
Thanks eggdeng! It worked! The change of model=lg to model=minimal did the trick for me. I have the same chip as you, namely CMI9880. There's no problem now, the speakers talk, the headphones too, without conflict.

=D>

---

### Post by eggdeng on 2007-06-22
> the mic still doesnt work. at least i have working speakers now.
You might be interested in Stami's post on this thread.
[http://ubuntuforums.org/showthread.php?t=342681](http://ubuntuforums.org/showthread.php?t=342681)

---

### Post by FloSynergy on 2007-06-22
hey there,

this sounds very much like the issue i am wrestling with [here.]("http://ubuntuforums.org/showthread.php?p=2887033#post2887033")

i have had a look at this file on my box:

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m 
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

it sems that the line you refer to does not appear here.

any suggestions?

thanks,
flo

---

### Post by eggdeng on 2007-06-22
The problems (& fixes) we've been looking at relate to Intel High Definition Audio cards; yours is Nvidia. Try doing a form search for  HDA NVidia if you haven't done so already. Sorry not to be of more help.

---

### Post by FloSynergy on 2007-06-22
hey folks,

thanks for the ref re hi-def cards.

i've been struggling for 3 days to get my sound to work...

then, sd-plissken pointed out [this]("http://ubuntuforums.org/showthread.php?t=239995&page=5") thread (it's what i used in the end) and [this]("p://ubuntuforums.org/showthread.php?t=455147") and [the wiki]("https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29").

now, i'm rocking to my favourite marley-tunes 

get-up - stand-up.....feel dem spirit!:guitar:

gigathanks,

flo

---

### Post by iansyngin on 2007-06-28
also having the same problem with Fujitsu-Siemens C Series Laptop.
No Sound from the speakers. Only sound from the earphones. very annoying.

have tried configuring alsa from scratch.
Have tried alsamixer, changing mm, editing the alsa-base file, don't know where to turn now

---

### Post by eggdeng on 2007-06-28
Can you post the output of
```
aplay -l
```

---

### Post by ohme on 2007-06-29
Didn't work for me (the original post). I've changed alsa-base many times. my last configuration was 
options snd-hda-intel position_fix=0 model=lg
but just to be sure I've tried again
options snd-hda-intel model=lg
and
options snd-hda-intel model=minimal 
neither of them did the work.

thanks,

---

### Post by guyvdb on 2007-06-29
but did you try recompiling alsa with the latest version: that fixed it for me
in the latest version new configuration options are available

---

### Post by ohme on 2007-06-29
I have 1.0.14rc4 . I shall try a later version when I have the time. thanks.

---

### Post by Setomidor on 2007-06-29
Having the exact same problem on a ferrari 5000. Hda-intel sb450 running the latest stable releases of alsa (just installed them this morning). Been messing around with model=acer and model=minimal without success. Alsamixer adjusting rendered no result.

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by iansyngin on 2007-06-29
Eggdeng. Here is my output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any ideas why i can't get the speakers working?

---

### Post by eggdeng on 2007-06-30
I suppose you have already tried adding
```
options snd-hda-intel model=fujitsu
``` to the alsa-base file. One other option I have seen recommended for ALC262 is ```
options snd-hda-intel model=basic
``` You may find more options by doing a search for ALC262 in your /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt. (you'll have to gunzip it first). Sorry not to be of more help.
Edit: One more to try ```
options snd-hda-intel model=auto
``` Remember you will need to reboot for changes to take effect.

---

### Post by iansyngin on 2007-07-01
tried the three of these options in the alsa-base file but still having no luck with sound. It's all been very silent lately :(
Anyway the search goes on to discover whats going on here.
If anyone feels like a suggestions, please let me know.

Thanks,
Syngin

---

### Post by iansyngin on 2007-07-05
Has anyone else any suggestions as to how i can resolve this sound issue on the laptop. nearly 3 months now with no sound. I thought there might be some sort of kernal patch by now but would appreciate if someone can help me work this one out.

I'm on gmail if it helps.
PM fot the gmail account
Ian

---

