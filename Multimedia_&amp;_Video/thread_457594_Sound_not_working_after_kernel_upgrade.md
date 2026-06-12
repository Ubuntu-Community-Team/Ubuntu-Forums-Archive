---
title: "Sound not working after kernel upgrade"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by timking on 2007-05-28
Ubuntu 7.04 on a Dell Inspiron 6000.

After upgrading from 2.6.20-15-generic to 2.6.20-16-generic, my audio is no longer working.  The sound card is a SigmaTel, but I'm not sure which model.

Any assistance would be appreciated.

Tim King

---

### Post by yabbadabbadont on 2007-05-28
Does it work again if you boot using the old 2.6.20-15 kernel.  Unless you uninstalled it, it should still be available on the Grub boot menu.  (You may have to hit Esc to see the menu)

---

### Post by timking on 2007-05-28
Yes, it works if I boot the 15 kernel.

---

### Post by yabbadabbadont on 2007-05-28
Did you have to install any special drivers for it when you first installed Ubuntu, or did it "just work"?  If you had to install 3rd party drivers (those not included with Ubuntu), then you will need to install them again when you are booted using the newer kernel.  If not....  looks like you found yet another issue with the latest kernel update.  It has been causing a flurry of panicked posts to the forums since it was released last night.  :(

---

### Post by timking on 2007-05-28
No special drivers, it just worked before.  I will stay on 15 for now.

Thanks for your help.

---

### Post by SL666 on 2007-05-29
:( IBM/lenovo T60 laptop, installed new kernel, now i have no sound - at all, and rebooting into 15 doesn't seem to help.

Any ideas?

---

### Post by SL666 on 2007-05-29
seems that it might be related to the intel ICH7 family card?

---

### Post by SL666 on 2007-05-29
this one may have been PEBKAC on my part.. 

It wasn't then working in XP, and then i didn't really do anything to it, and then it started working... farkin!

---

### Post by fgosse on 2007-05-29
I've the same problem with inspiron 6000

---> cat /proc/asound/cards
0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with STAC9752,53 at 0xdfebfe00, irq 18

--->lsmod|grep snd
snd_intel8x0           34332  2
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm


--->aplay /usr/share/sounds/KDE_Desktop6.wav
Lecture en cours WAVE '/usr/share/sounds/KDE_Desktop6.wav' : Signed 16 bit Little Endian, Taux 22050 Hz, Mono


Thanks a lot for your help
F.G

---

### Post by Rice_slayer on 2007-05-29
After the recent updates, My audio works, but only offline, all my online audio is gone. Say on a youtube video, i get the video without audio. I should have stayed with Edgy, it WAS more stable than Feisty Fawn is proving to be...

---

### Post by donald7777 on 2007-05-30
my sound also died after the update, as with everyone if i go to the other kernel it works.
lsmod|grep snd

snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  2 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

laptop gateway MT6451

---

### Post by rynoprinsloo on 2007-06-01
My sound  also doesn't work after upgrade.

I have an Intel 865GLC Chipset.

lsmod|grep snd

snd_intel8x0           34204  2
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm 

I'm using the 15 kernel for now.

---

### Post by wooster12 on 2007-06-01
Same problem, with a twist. After recent kernel upgrade, sound will work for first <indeterminate and variable amount of time> after a reboot. Eventually it'll stop and all video (on- or off-line) is audioless, and audio files will not play at all, with (in Totem) the error:
---
```
Totem could not play 'file:///home/********whatever.mp3.
This is an audio-only file, and there is no audio output available. 
```
---
Other players throw up a similar error, such as "Could not initialize audio" etc.  Rebooting into the updated kernel would repeat the process (sound ok for a while, then gone...)

Rebooted into previous kernel and so far things are ok.  pasting below from the older (currently working audio) kernel.

 lsmod|grep snd
snd_intel8x0           33692  3
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  2 snd

---

### Post by fgosse on 2007-06-08
It's good for me now

In a shell :
-alsamixer
-then in PCM Out replace pre 3D by post 3D

F.G

---

### Post by five_13 on 2007-12-21
yep, have the same problem because of this update :(
Laptop: Fujitsu-Siemes Amilo PA 1510

hope the problem is gonna be fixed soon.

btw: "alsamixer: function snd_ctl_open failed for default: No such device"

---

