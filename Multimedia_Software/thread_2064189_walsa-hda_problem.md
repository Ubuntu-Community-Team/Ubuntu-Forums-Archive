---
title: "walsa-hda problem"
date: 2012-09-28
forum: Multimedia Software
---

### Post by redsprite on 2012-09-28
hey everyone,

I recently upgraded to ubuntu 12.04 but just after updating grub i lost sound so
i have tried theese 2 links :

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)

I apologize for making a new thread, but I haven't been able to find any solutions in the other threads regarding problems with sound.

My desk seems to recognize my sound card. In fact, everything looks fine... but, no sound! just on kernel  linux-headers-3.2.0-31-generic ???
so all thing  
but sound works like a charm on precedent  linux-headers-3.2.0-16-generic  

Nothing is muted in alsamixer and all channels are at full volume...the headphone jack actually works, but the volume is way too low.

My ALSA information is located at:[http://www.alsa-project.org/db/?f=09dcab500ad7ce35734659ea1779dc09209d35cf](http://www.alsa-project.org/db/?f=09dcab500ad7ce35734659ea1779dc09209d35cf)


so this is my make.log (/var/lib/dkms/alsa-hda/0.201209241126~precise1/build/make.log) file:

" DKMS make.log for alsa-hda-0.201209241126~precise1 for kernel 3.2.0-31-generic (i686)
vendredi 28 septembre 2012, 19:21:01 (UTC+0100)
make -C /lib/modules/3.2.0-31-generic/build M=/var/lib/dkms/alsa-hda/0.201209241126~precise1/build modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-31-generic'
  CC [M]  /var/lib/dkms/alsa-hda/0.201209241126~precise1/build/patch_analog.o
/var/lib/dkms/alsa-hda/0.201209241126~precise1/build/patch_analog.c: In function &#8216;get_order&#8217;:
/var/lib/dkms/alsa-hda/0.201209241126~precise1/build/patch_analog.c:5107:1: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.
Preprocessed source stored into /tmp/ccjTnQTf.out file, please attach this to your bugreport.
make[2]: *** [/var/lib/dkms/alsa-hda/0.201209241126~precise1/build/patch_analog.o] Error 1
make[1]: *** [_module_/var/lib/dkms/alsa-hda/0.201209241126~precise1/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-31-generic'
make: *** [all] Error 2 "


thnx in advance..

---

### Post by BicyclerBoy on 2012-09-28
I've (intentionally) never followed those instructions..
Your attempt to fix the audio in the latest kernel has resulted in breaking the replacement alsa kernel module.
I think the update process you followed will continue to trigger & try to build (dkms) against any new kernel update..
Hopefully it will work in future.

None of your posted links work..

You can:
- set the previous kernel image as default (grub)
- find all ubuntu-audio-dev packages & roll them back.
- wait for new kernel updates..

My experience of the ubuntu-audio-dev with lucid 10.04 was that it caused dependency problems with later kernels/iquik/alsa backports..

---

### Post by redsprite on 2012-09-29
hi , thank  you for your time
links work for now ..
About new kernel update,i'll try with the next one :kernel 3.2.0-32

---

### Post by BicyclerBoy on 2012-09-29
Your links work today..

You've set your default alsa output device to digital output..
Is this intended?

There are a lot of "mute=1" in the alsa file..
And a lot of mutes in the hw:0,1 device nodes etc.

I would:
- re-check for muted outs in alsamixer
- remove /etc/asound.conf (rename/stash it)
- run pavucontrol i.e. do config in pulse audio.

speaker-test -l 1 -c 2 -r 48000 -D hw:0,1
if you are analogue connected then use hw:0,0

---

### Post by redsprite on 2012-10-05
hello BicyclerBoy , 

1- My default alsa output device was setting to digital output
2- No "mute=1" in alsa file at all
 then :
- No mute in outs for alsamixer
- /etc/asound.conf is emty
- Pulse audio was configured after running pavucontrol
- here is the output for : "speaker-test -l 1 -c 2 -r 48000 -D hw:0,0"
"speaker-test 1.0.25
Playback device is hw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5,632207"

thank u for your time

---

### Post by redsprite on 2012-10-05
hi ,
finly it was solved..

just by adding this line :

options snd-hda-intel model=generic

in (/etc/modprobe.d/alsa-base.conf) and reboot.
  
Thank you BicyclerBoy for the help and reply ..

---

