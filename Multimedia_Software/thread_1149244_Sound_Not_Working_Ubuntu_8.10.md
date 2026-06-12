---
title: "Sound Not Working Ubuntu 8.10"
date: 2009-05-05
forum: Multimedia Software
---

### Post by Viligam on 2009-05-05
Hi Everyone,

I am having a minor sound issue where the sound sometimes works, sometimes does not depending on boot.  As in sometimes after I boot up it works and sometimes not.  Anywho, I was wondering if anyone had any tips or advice to make the sound work more consistantly, like everytime.  :P

So, here is where I am at now, I followed the sound trouble shooting guide here ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)) and I have some info to post that hopefully will be of help.  I am not a complete noob, but I still have a fair amount to learn.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


When I do this it shows that my drivers are installed:
 ```
find /lib/modules/`uname -r` | grep snd

```


```
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000 Device 0506
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at c0503400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ATI IXP AC97 controller
        Kernel modules: snd-atiixp
```

This is where I stopped.  Not sure if I need to update all drivers or if I should be doing something else. :confused:

Any advice that helps out is appreciated.:KS

---

### Post by Viligam on 2009-05-17
Humm ... No suggestions?  :sad:

---

### Post by cguy on 2009-05-17
On my older computer I had the same problem (Windows XP, Win2000, Ubuntu, you name it). (AC'97 integrated card)
The problem was beyond the OS.

I'm not suggesting you have the same problem, but it's a perspective which shouldn't be disregarded.

---

### Post by Aaardwark on 2009-05-17
My guess is you system thinks the modem is a sound card. When you boot with multiple sound cards, it is random which module loads first. That might put your modem as primary sound card. If that is the problem, it is solvable by specifying the order the modules load.

Could you give me the output of this?:
```
lsmod | grep snd
```

---

### Post by Viligam on 2009-05-17
Thanks!  Here is the results. 

> xxxxxxx:~$ lsmod | grep snd
snd_atiixp             24204  3 
snd_seq_dummy          10884  0 
snd_atiixp_modem       20360  0 
snd_ac97_codec        111652  2 snd_atiixp,snd_atiixp_modem
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_pcm                83204  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  17 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  3 snd_atiixp,snd_atiixp_modem,snd_pcm

---

### Post by andypearce on 2009-05-18
hi....got the same problem maybe...sound on boot up variable from normal to half speed to what sounds like one note at a time. I have ATI IXP SB400 AC'97 Audio Controller..... not much specific help so far from forum (but some good tips and pointers)... as a complete newcomer it is difficult to know what to ask to engage those that may know...worse in 9.4! If you fixed it I would love to know how.... repeating boot up six times is inconvenient to say the least.
Ta Andy

---

### Post by Viligam on 2009-05-19
So, getting back on focus ... anyone have any suggestions to resolve said issue? ;)

Thanks! :)

---

### Post by Viligam on 2009-05-21
Beuller, Beuller, Beuller .... Wait, they cannot hear me since I cannot get my audio to work correctly.... *sad face*

---

### Post by Viligam on 2009-05-27
I am trying to keep this thread alive till I can get an answer / resolution ... Anyone have any suggestions?  Please?

---

### Post by Aaardwark on 2009-06-02
Sorry guys, haven't been around for a few days. Here's the rest of the solution:

From the "lsmod | grep snd" I believe the sound module for the modem to be "snd_atiixp_modem", and the module for the sound card to be "snd_atiixp".

If I got that part right, what you do is to open alsa-base.
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
In the config-file change
```
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
```
Into:
```
install sound-slot-0 /sbin/modprobe snd-atiixp
install sound-slot-1 /sbin/modprobe snd-atiixp-modem
```

Now you have specified which card is which. The next step is to say what order to input the modules. To the end of the file ad:
```
options snd-atiixp index=0
options snd-atiixp-modem index=1
```
Save and close the file.

Now hopefully, every time you start the computer it will input the modules in the right order. If it doesn't work, pm me again and I will take another look.

---

### Post by andypearce on 2009-06-04
Hi Aaardwark....is that a specific fix for Viligam's computer or is it a fix that anyone can use? I have probably now spent over 50 hours on this problem including research and asking the forum; I regularly have to restart my laptop four plus times before the sound(then all related stuff) comes right. Any help appreciated.
thanks Andy

---

### Post by Aaardwark on 2009-06-04
The solution is specific. However, you can do the same thing. Use lsmod, to find out what modules you are using (this depends on the sound cards).
```
lsmod | grep snd
```
After figuring out which cards, and modules you have. You open the configuration file.
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
In there you edit the same lines, and ad the same lines as in the other instruction. Changing the sound card modules names to your modules.

For example: My computer has two sound cards (actually three, but I've disabled one in the BIOS). Reading through "lsmod | grep snd", I realize the modules names are "snd_ice1724" and "snd_emu10k1".
That would mean instead of changing it like this:
```
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1

Into

install sound-slot-0 /sbin/modprobe snd-atiixp
install sound-slot-1 /sbin/modprobe snd-atiixp-modem

And adding

options snd-atiixp index=0
options snd-atiixp-modem index=1
```
I would change it like this:
```
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1

Into

install sound-slot-0 /sbin/modprobe snd-emu10k1
install sound-slot-1 /sbin/modprobe snd-ice1724

And adding

options snd-emu10k1 index=0
options snd-ice1724 index=1
```
The complicated part is to figure out which modules to put in. If you want help figuring that part out, give me the output of "lsmod | grep snd", and I will gladly help you out. I also need to know what sound card you want me to place first (so I don't make the sound not work 100%, instead of 50% of the time). To find out which cards you have, use this command:
```
aplay -l
```
Give me that output as well, and tell me which card you prefer.

---

### Post by andypearce on 2009-06-04
Hi Aaardwark.... thanks very much... here is what I have
andy@andy-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

andy@andy-laptop:~$ lsmod | grep snd
snd_atiixp_modem       20360  0 
snd_atiixp             24204  3 
snd_ac97_codec        112292  2 snd_atiixp_modem,snd_atiixp
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_pcm                82948  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  17 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  3 snd_atiixp_modem,snd_atiixp,snd_pcm

I do not know what card I prefer.....I do not know enough as yet to make that choice! Is that enough info' or do you need more. Thanks again for your time and help.
Andy

---

### Post by Aaardwark on 2009-06-04
It was a specific solution, but you've got the exact same cards and modules:
snd_atiixp_modem
snd_atiixp
Just follow my first instructions, and you should be fine.

Good luck! :-D

---

### Post by andypearce on 2009-06-05
thanks aaardwark..... i shall give it a go... let you know
Andy

---

### Post by andypearce on 2009-06-05
Hi Aaardwark again.... it does not seem to have fixed the problem... I may have done it wrong... this is what I did.

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-atiixp
install sound-slot-1 /sbin/modprobe snd-atiixp-modem
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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-atiixp index=0
options snd-atiixp-modem index=1

Is that what you suggested?

---

### Post by andypearce on 2009-06-07
hey viligam did it work for you?  The most common indication of this fault for me is when the opening tune starts it can turn into a clicking noise that goes on and on.... no media works then. Alternatively there is no welcome tune and after a few minutes the repetitive clicking begins... i can use everything except sound, flash, dvd etc... I have to put the sound on mute. Is it the same for you?
Andy

---

