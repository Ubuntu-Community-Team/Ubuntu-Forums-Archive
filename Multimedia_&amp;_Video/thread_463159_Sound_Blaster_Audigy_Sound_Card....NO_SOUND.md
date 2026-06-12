---
title: "Sound Blaster Audigy Sound Card....NO SOUND"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by chelehandsome on 2007-06-03
Hello Everyone, Can You Plz Help Me To Find Out How To Configure My Sound Hardware To Get My Multimedia Sound?

I Have A Sound Blaster Audigy Card, And I Tried To Listen To Music But The Player Seems Is Playing The Song, But I Cant Hear Anything,

I Checked My Hardware Configuration, And Actually The Sound Card Appeared Perfectly Installed, So I Dont Know What Else To Do.

I already made the changes in the volume icon in the right corner of the top bar, and I deselected the digital out, and and Preferences submenu I selected Sorround and turn up the volume to 80, but I still dont have sound.

Thx 4 ur support

I Am New User Of Ubuntu.

---

### Post by wolfen69 on 2007-06-03
the ubuntuguide has a possible fix for your sound. [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

it is towards the bottom of the page.

---

### Post by Epic Plecostomus on 2007-12-25
Bump to top.   Having issues with this card.  Tried the suggested fix from above, no luck.  Any other pointers?

---

### Post by Armithius on 2008-01-01
BUMP

I can't get my card working either. I've tried everything suggested here and elsewhere (unchecking analog/digital, etc.) Any help would be appreciated.

---

### Post by Freebyrd on 2008-01-05
I had the same problem with my audigy 1 card. I had to go into BIOS and disable on-board sound to get mine to work.

---

### Post by Rubruquis on 2008-01-05
I have a similar problem. I have Sound Blaster Audigy LS and half of the times I start Ubuntu my sound card works and half of the times it does not.

---

### Post by cokehabit on 2008-01-09
Same problems here on hardy, Audigy 1 up and running but no sound. All the apps say everything is fine.

---

### Post by Jive Turkey on 2008-01-09
I find that whenever I have a new install the "PCM" slider is set to zero and some apps actually will zero it from time to time.  It's like the master slider, but somehow not.  Make sure your PCM isn't set to zero.

---

### Post by cokehabit on 2008-01-09
Nope, everything is fine, the modules are loaded

```
george@george-desktop:~$ lsmod | grep emu10k1
snd_emu10k1_synth       8064  0 
snd_emux_synth         35328  1 snd_emu10k1_synth
snd_emu10k1           142752  6 snd_emu10k1_synth
snd_ac97_codec        100516  1 snd_emu10k1
snd_pcm                80644  4 snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11272  2 snd_emu10k1,snd_pcm
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  3 snd_usb_audio,snd_emux_synth,snd_emu10k1
snd_rawmidi            25600  4 snd_usb_lib,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_timer              24324  4 snd_rtctimer,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55172  24 snd_usb_audio,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
emu10k1_gp              4608  0 
gameport               16648  2 emu10k1_gp

```selecting OSS or PulseAudio doesn't help either. The player says it is playing but no sounds are coming out. Everything is unmuted.

---

### Post by cokehabit on 2008-01-24
My problem was I had ```
Audigy Analog/Digital Output Jack
``` unmuted in alsamixer.

As soon as I muted it the sound came back

---

### Post by Bungo on 2008-01-24
> **Freebyrd said:**
> I had the same problem with my audigy 1 card. I had to go into BIOS and disable on-board sound to get mine to work.

I got mine working the same way. Having difficulty getting sound IN though...can't use Skype or record anything.

---

### Post by jackhe22 on 2008-05-30
Where do you find the Ubuntu Volume control??

---

### Post by cokehabit on 2008-05-30
there are a number of ways.

first you can run alsamixer in the console

or...

in sound/video in your menu there should be a volume control there 

but...

I like to have an easy one on my screen so i right-click the bar at the top of my screen and then add a volume control. You can also add icons for everything else in that fashion

---

### Post by jackhe22 on 2008-05-31
Im gonna file a bug report in Launchpad now.

---

### Post by jackhe22 on 2008-05-31
Fixed! Simply right click on the Volume Icon in the top right corner. Select Open Volume Control. UnMute PC Speaker. Click on Switches Unselect the Box. Now play music! Fixed.

---

### Post by rudy_691 on 2008-06-01
still got the same problem...it didnt work for me..

---

### Post by jackhe22 on 2008-06-13
Well.... Sorry! Thats a shame though but.... Maybe! Just keep updating it every day, and you never know!

---

