---
title: "Sound gone all of a sudden"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by coldrick on 2006-07-01
For some reason, sound has suddenly disappeared on my Inspiron 9300, which has been running Dapper for some months. Sound card is OK, cause it all works fine if I boot into windoze. I get *no* sound - no beeps, no CD playing, no sound from Flash, etc.  Only event I can think of to tie it to is the recent upgrade of GTK stuff, but that may be a red herring.

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer shows everything on, altho I don't understand what some of the settings mean. I noticed that PCM wasn't on, turned it on with no result - except that a boot or two later, sound was working! Now it isn't again, despite my having changed nothing. :confused: 

/etc/modules lists:

nvidia
lp
psmouse
sbp2

If (following [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)) I do:
sudo modprobe snd-

I get:
FATAL: Module snd_ not found.

Any ideas?

Regards,
David

---

### Post by LordRaiden on 2006-07-02
Hi coldrick,

The instuction said to type sudo modprobe snd- THEN press the TAB key BEFORE pressing the Enter key. You will get  a list of all the sound (snd) available.

However,  in your case you can already see you sound card with aplay -l. 

I would say to try ```
lsmod | grep snd
``` I think the module that you should be looking for is something like hda-intel. I would also suggest you mute/unmute any IEC958 and External Ampliefiers one by one to see if that has any effect.

---

### Post by coldrick on 2006-07-03
Oh yeah. Blush. Actually, it takes a few tabs before I get prompted as to whether I want to see all 136 of them. 

lsmod|grep snd yields 

snd_intel8x0           35708  1
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm

fwiw. There are a number of snd modules about, obviously.

I'll try your suggestion of turning individual alsamixer channels one by one.

Regards,
David

---

### Post by coldrick on 2006-07-03
Hmm. Tried a bunch of combos, but no luck. given the number of possible combinations, I could be doing that for a long time. 

Any ideas?

Regards,
David

---

### Post by LordRaiden on 2006-07-03
wait. If sound was working with pcm turned on, then go back to alsamixer again and have a look if it pcm is muted again.

---

### Post by coldrick on 2006-07-03
Yes, tried that. Even tried rebooting a couple of times after flipping some mutes. Very frustrating!

Regardsm
David

---

### Post by coldrick on 2006-07-10
Gave up and re-installed: all ok now. Sigh

---

### Post by LordRaiden on 2006-07-10
Good to hear you finally got it working. For future reference, keep an old image of the kernel handy so that you can boot into it an --purge remove the newer kernel image and alsa packages. After that, a reinstall of the same packages should solve the problem. Bit like reinstalling but less work ;)

---

