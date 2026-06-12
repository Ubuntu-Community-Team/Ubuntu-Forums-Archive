---
title: "dvds too quiet"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Kusho on 2008-06-24
okay i've searched and read thru forums for the last 3 hours, so I feel safe posting my problem.  Sorry if I'm missing another fix, but I just can't find it.  Fairly new to ubuntu, p2 gateway motherboard with a p3 550 processor in it.  Sound blaster live value sound card, and ubuntu up on it.  Sound drivers is set to Ensoniq AudioPCI (Alsa mixer)  I am trying to play dvds on this pc, and the audio is way to quiet with speakers, pc, and video player maxed.  I'm using Todem video player, and grabbed the Ubuntu restricted extras to get the dvd codec.  I do have sound, and tried a internet radio station and sound was sufficient in that.  Speakers sound find when hooked up to my main amd 64 pc, and sound card sounds fine in windows me.  (xp doesn't like this pc, too old)

Thought I'd try ubuntu...  and it seems very stable...  slowly figuring out all of this...  and like the all of the forums on here.  Hate asking this question...  but I've searched and searched.  Any help would be appreciated, and still a novice in this...  so a (fire up concole, type in "bla bla"  type of walkthru for a fix would be appreciated.  thanks.

---

### Post by jrusso2 on 2008-06-24
If I recall correctly that card uses that EMU10k1 driver is that what your using?

---

### Post by Kusho on 2008-06-24
Ensoniq AudioPCI (Alsa mixer) is what autodetected.

---

### Post by Kusho on 2008-06-24
tried to change that to the SBLive! Value [CT4780] (Alsa mixer) under Device in Default Mixer Tracks, but same results.  When I click System-Admin-Hardware drivers it just says no priority dricers are loaded on this system.

---

### Post by Kusho on 2008-06-24
[http://ubuntuforums.org/archive/index.php/t-369123.html](http://ubuntuforums.org/archive/index.php/t-369123.html)  found this ...  but origional walkthru ttp://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+ES.&chip=emu10k2&module=emu10k1
 is no longer there...  and they refer back to origional walkthru at every step.

---

### Post by Kusho on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=19307](http://ubuntuforums.org/showthread.php?t=19307) 

is this what i want?

---

### Post by Kusho on 2008-06-24
oh and using Ubuntu 8.04

tom@tom-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive! Value [CT4780]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Live [SBLive! Value [CT4780]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive! Value [CT4780]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tom@tom-desktop:~$

---

### Post by smlefo on 2008-06-24
```
$ sudo alsamixer
```

That worked for me - one of my channels was really low.  Not sure about your scenario.

~Sean

---

### Post by Kusho on 2008-06-25
Okay tried that...  didnt change anything.  no matter if i max it out, or bring it down to nil.  changed my sound back to Ensonic as saw that was what this mixer showed...  but that still didnt change anything.  this mixer doesnt even seem to be tied to my system.

---

and i'm a little scared to mess too much with what came up from default as i have sound just dvds are way too quiet.  all of these forums are for fixing no sound issues.

---

### Post by cariboo on 2008-06-25
Nobody seems to have mentioned this, have you got PCM turned all the way up? Just double click on the speaker icon and on the Volume Control Panel if PCM is turned down, turn it up. here is a link to explain what pcm is.

[http://en.wikipedia.org/wiki/ADPCM#Digitization_as_part_of_the_PCM_process](http://en.wikipedia.org/wiki/ADPCM#Digitization_as_part_of_the_PCM_process)

Jim

---

### Post by Kusho on 2008-06-25
Don't know how to include a screenshot in this, but yes.  Volume Control is all maxed out on everything but Line-in and Microphone.  Only thing that seems quiet is DVDs but that volume is maxed also.  And it's like way quiet.  but volume still maxed and login and log out arent like deafing like they would be with volume maxed in a windows system.

Just tried a online flash movie... and that had no sound.  all sound is too quiet thou.  sound still maxed...  and gaim sound is the perfect level.  so all sound is just too quiet.

---

### Post by Kusho on 2008-06-25
Guy at work gave me this as a possible fix.  Will try when i get home.

&#8206;&#8206;Piles, Ken&#8206;&#8206; [7:17 PM]:
  [http://saquibhussain.multiply.com/journal/item/45/No_Audio_in_Flash_Player_Ubuntu_Hardy](http://saquibhussain.multiply.com/journal/item/45/No_Audio_in_Flash_Player_Ubuntu_Hardy)
&#8206;&#8206;Piles, Ken&#8206;&#8206; [7:21 PM]:
  sudo apt-get install libflashsupport

---

