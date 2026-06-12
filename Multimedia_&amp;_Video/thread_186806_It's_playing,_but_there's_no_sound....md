---
title: "It's playing, but there's no sound..."
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Rogue Jedi X on 2006-06-02
I upgraded to Dapper yesterday and I think I may have done something wrong. After the upgrade, I wouldn't get any sound whatsoever and I don't mean just with mp3s. Oggs, flacs, nothing would work. Players seem to play files without errors, there's even those columns jumping up and down when you play audio files.

Anyway, I asked around on IRC and we did the following tests:
```
aplay /dev/urandom
```
Nothing plays. Silence.
We've also checked alsamixer and everything seems to be fine there.
```
cat /dev/urandom > /dev/dsp
```
Again, nothing.

cat /dev/urandom > /dev/dsp displays this: [http://kubuntu.pastebin.com/752349](http://kubuntu.pastebin.com/752349)

Also, if it helps, here's my lsmod output: [http://kubuntu.pastebin.com/752349](http://kubuntu.pastebin.com/752349)

After being unsuccessful to remedy the problem, I thought maybe my alsa.conf file may have been overwritten during upgrade, so I tried running alsaconf...only to find out it isn't there anymore. Any ideas?

---

### Post by Useruntu on 2006-06-02
I've got the same problem :( I've got an on-board soundcard. I'm searching everywhere on the web but with no success.
Did you find a solution?

---

### Post by oimon on 2006-06-03
Grrr, having some problems since the big dapper upgrade.
Got my netgear wg121 working after blacklisting the prism drivers, now my creative sb live card isn't producing any sound...

root@raclette:/var/log# cat /proc/asound/cards
0 [Live           ]: EMU10K1 - SBLive! [CT4620]
                     SBLive! [CT4620] (rev.4, serial:0x211102) at 0xb800, irq 209

lspci 
..
0000:02:05.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
...

When i boot into windows, i get sound.
I've tried the KDE control centre to change the sound manager (ALSA, esd, OSS, autodetect,etc) but no joy.

Wondering if there's a solution...?

---

### Post by Bloch on 2006-06-03
Just did my first install of dapper and same problem - sound doesn't work. Actually with volume at max I can hear a distorted crackle.

Occasionally I used to get the same problem with Breezy but it used to go away.

Is there anything I can do?

I am using the default esd and onboard sound VIA8235

---

### Post by oimon on 2006-06-03
Actually i just fixed the problem i had.

Typing alsamixer takes you into the sound settings.

Check the first column "Master"
The top of the screen should say something like this

Card: SBLive! [CT4620] 
&#9474;&#9474; Chip: TriTech id 3
&#9474;&#9474; View: [Playback] Capture  All
&#9474;&#9474; Item: Master  

mine said 
Item: Master  [off]

If you have this setting , it doesn't matter what your sounds levels are set to -you won't get sound!
Press "m" to turn the master volume on.
Use up and down arrows to change some volume settings (master, wave, etc)

Hope this works for the rest of you.

---

### Post by Rogue Jedi X on 2006-06-03
Actually, I don't have the option to mute the master volume in alsamixer. Is this only with me or is this a common problem?

---

### Post by Zap on 2006-06-03
I've the same problem, no sound and it's not because it's mute...
It's strange nobody fix this bug until the stable version:-k

---

### Post by Tyche on 2006-06-03
Grasping at straws, I tried your suggestion (below).  Alsamixer reported that the master was live (not muted).  I still get no sound.  Top of the screen says:

Card:  SBLive [Unknown]
Chip:  SigmaTel Stac9758,59
View:  [Playback] Capture  All
Item:  Master

](*,) 
Tyche



> **oimon]Actually i just fixed the problem i had.

Typing alsamixer takes you into the sound settings.

Check the first column "Master"
The top of the screen should say something like this

Card: SBLive! [CT4620] 
&#9474 said:**
>  Capture  All
&#9474;&#9474; Item: Master  

mine said 
Item: Master  [off]

If you have this setting , it doesn't matter what your sounds levels are set to -you won't get sound!
Press "m" to turn the master volume on.
Use up and down arrows to change some volume settings (master, wave, etc)

Hope this works for the rest of you.

---

### Post by Rogue Jedi X on 2006-06-04
Did anyone figure anything out yet? This situation is really unnerving, since I can't play games, watch videos, not to mention my sound system not working. I could, of course, just download the Install CD and make a fresh install, but I'd hate that, since I'd have to reinstall everything afterwards.

---

### Post by Rogue Jedi X on 2006-06-04
Just so everyone knows: Doing a fresh install as opposed to upgrading, does NOT help. For me, anyway. I still have the same problem.

---

### Post by crane on 2006-06-04
Mine worked for a bit, then stopped. I have no sound in Quake4 or any system sounds.

---

### Post by knytphal on 2006-06-05
I've got the exact same problem....just finished the upgrade from Breezy to Dapper and really, really, really, really wishing that I hadn't....

output of aplay -l: (cut down some)
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32

card 0: Live [SBLive! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]

card 0: Live [SBLive! Platinum [CT4760P]], device 3: emu10k1 [Multichannel Playback]


output of lsmod: (relevant parts)
snd                    60004  21 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10784  1 snd


And like everybody else above, amarok seems to play just fine - the eq shows the bars moving.  I have made sure that sound is not muted by using both the control panel stuff and the alsa tool itself. 

I've got to have sound.....

---

### Post by knytphal on 2006-06-05
[QUOTE=knytphal]I've got the exact same problem....just finished the upgrade from Breezy to Dapper and really, really, really, really wishing that I hadn't....

output of aplay -l: (cut down some)
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32

card 0: Live [SBLive! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]

card 0: Live [SBLive! Platinum [CT4760P]], device 3: emu10k1 [Multichannel Playback]


output of lsmod: (relevant parts)
snd                    60004  21 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10784  1 snd


And like everybody else above, amarok seems to play just fine - the eq shows the bars moving.  I have made sure that sound is not muted by using both the control panel stuff and the alsa tool itself. 

I've got to have sound.....[/QUOTE]

Sorry about the double post, but I couldn't figure out how to edit my previous one...

I figured out what was up on my problem, for some reason the 'Wave' volume was turned all the way down on the mixer and that caused no sound.  Go figure.

---

### Post by real_jester on 2006-08-22
I got the same problem, i fixed ith with turning the Wave Volume switch up in the alsamixer. There are lots of gauges, wave was set to 0. I put it to a normal level, and now the sound works.

Greets,
Oliver

---

