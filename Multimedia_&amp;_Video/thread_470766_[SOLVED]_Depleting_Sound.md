---
title: "[SOLVED] Depleting Sound"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by jusmurph on 2007-06-11
When i started with Linux i had all sound working but as i have installed programs i have lost sounds.

(I'm a noob so I'm not exactly tweaking thing yet so...) Anyway i get no sound from anything other than Rythmbox Music Player's mp3's. The biggest problem is getting no sound from videos.

I have tried:

1) Reinstalling "libsdl1.2debian-alsa" via Synaptic

2) I also tried this (losing ubuntu-desktop waas no fun btw)

```
 [From 
http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

   1. Remove these packages sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
          * Here's the likely output you'll get by running that above command 
   2. Reinstall those same packages sudo apt-get install linux-sound-base alsa-base alsa-utils
          * VERY IMPORTANT NOTE - Ubuntu (GNOME): users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following sudo apt-get install gdm ubuntu-desktop
   3. Reboot 
```

I run a single stereo signal from a creative sound blaster audigy 2. If someone could help it would be great thank you!

---

### Post by Cappy on 2007-06-12
Run a program in the terminal that isn't getting sound. For instance, if totem isn't playing the audio from videos type ```
totem
``` in the terminal and open a video or audio file. Hopefully, there will be an error once you open a file in totem. Try the same thing for firefox and do something like watch a youtube video.

Does ```
aplay -l
``` give any errors?

---

### Post by jusmurph on 2007-06-12
Thanks.

I will try this when i get home and post my results.

---

### Post by jusmurph on 2007-06-12
Totom shows no errors though no sound, video is flawless.

aplay -l

anthonii@smurph:~$ totem
anthonii@smurph:~$ aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Though when i put in alsamixer
It came up with the device being the onboard realtek chip rather than the audidgy 2... does that mean anything?

---

### Post by Cappy on 2007-06-12
Is the audio playing out of your onboard sound?
In any case, try this:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)

You must put BOTH sound cards in there or else it won't work. You can't just set "snd-emu10k1" as index 0. You need to also set your onboard (whatever it is) to index 1.

Is ubuntu configured to use your Audigy 2 in System-->Preferences-->Sound? It should be selected as the "Device". I'll assume it is. It also should be selected in Volume Control (alsa mixer) in File-->Change Device.

---

### Post by jusmurph on 2007-06-12
> **Cappy said:**
> Is the audio playing out of your onboard sound?
In any case, try this:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)

You must put BOTH sound cards in there or else it won't work. You can't just set "snd-emu10k1" as index 0. You need to also set your onboard (whatever it is) to index 1.

> **Cappy said:**
> 
Is ubuntu configured to use your Audigy 2 in System-->Preferences-->Sound? It should be selected as the "Device". I'll assume it is. It also should be selected in Volume Control (alsa mixer) in File-->Change Device.

I appreciate your help sincerely mate.

The second part is already done, I will start on the other guide now and will post again soon.

---

### Post by jusmurph on 2007-06-12
Fixed.

the " Configuring default soundcards / stopping soundcards from switching" freaked me out. I saw the alternative and found it here [https://bugs.launchpad.net/ubuntu/+bug/57141](https://bugs.launchpad.net/ubuntu/+bug/57141)


[QUOTE=Gabriel Pastor]
I had the same problem with feisty and solved it.
I have 2 sound cards, and it seems that sometimes the wrong sound card is the default sound device.

$ sudo asoundconf list
Names of available sound cards:
Intel
CA0106

The first one is integrated on the motherboard, and the second one (an audigy) is the one I use.

To solve the problem, I just set the default sound card to the audigy:
$ sudo asoundconf set-default-card CA0106

Then the sound works !
Hope it helps.[/QUOTE]

Thank you thank you thank you!

---

