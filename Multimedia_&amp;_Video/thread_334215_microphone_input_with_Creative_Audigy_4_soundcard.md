---
title: "microphone input with Creative Audigy 4 soundcard"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by Rollerbob on 2007-01-08
Hi, I'm using Edgy on an AMD 64 machine running the k8 kernel. Sound output is working fine with my Creative Audigy 4 soundcard, although I can't get sound input to work properly. I searched the forums for this problem and I know this has come up alot, but none of the solutions work for me. So this a last ditch attempt to get this working before I swap the Audigy card for something else!

I want to use a mic for VOIP as well as audio recording. Ekiga seems to recognise the card OK, but when I make a test call, my voice isn't recorded. LIkewise, recording using Sound Recorder or Audacity doesn't work either. 

I know the Mic is working, is switched on, and is plugged into the correct socket because when i turn up 'Amic' in alsamixer, and I can hear myself through my headphones. 

Here are some command line outputs:

```
cat /proc/asound/cards 
 0 [Audigy2        ]: Audigy2 - Audigy 4 [SB0610]
                      Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0xe800, irq 58
```


```
lsmod | grep snd
snd_emu10k1_synth      11008  0 
snd_emux_synth         50176  1 snd_emu10k1_synth
snd_seq_virmidi        10624  1 snd_emux_synth
snd_seq_midi_emul      10112  1 snd_emux_synth
snd_seq_dummy           6020  0 
snd_seq_oss            45824  0 
snd_seq_midi           12160  0 
snd_seq_midi_event     11520  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                77344  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           152480  4 snd_emu10k1_synth
snd_rawmidi            34432  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec        127064  1 snd_emu10k1
snd_ac97_bus            4352  1 snd_ac97_codec
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm               108168  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device         12180  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              31112  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         13200  2 snd_emu10k1,snd_pcm
snd_util_mem            7552  2 snd_emux_synth,snd_emu10k1
snd_hwdep              14088  2 snd_emux_synth,snd_emu10k1
snd                    79016  19 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              14112  1 snd
```

Attached is a screengrab of my alsamixer set up. 

Can anyone help?

---

### Post by Rollerbob on 2007-01-12
OK, after a week of.... ](*,) ... I've finally got my Mic working. Although there is a Caveat, so please try this at your own risk.

On the command line i removed the alsa-base package (see Caveat below): 
> sudo apt-get remove alsa-base

Then I used the instructions on this Ubuntu wiki page to install the latest stable ALSA software:
[https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard)

Note: if you're having problems with an Audigy card, when you compile Alsa-drivers, you need:
> ./configure --with-cards=emu10k1 --with-oss=yes --with-sequencer=yes

If you've never compiled software before don't be put off. If you follow the instructions carefully it's very easy. 

After rebooting my machine, I went to the command line again and ran alsamixer. I pressed the tab key to switch to the 'capture' sliders, and turned Master, Line, CD, Mic, Aux, Analog Mix to 100% (also you need press space on the first 4 to toggle 'CAPTUR' on).

If you're using Sound Recorder to test your Mic then don't. For some reason it likes to change Alsamixer setting and generally doesn't work too well. Instead try Audacity. 

CAVEAT: The only way I could get this to work was to remove alsa-base before compiling and and installing the latest drivers. The problem is that doing 'sudo apt-get remove alsa-base' removes the ubuntu-minimal package with it. Trying to apt-get install ubuntu-minimal again requires that alsa-base be installed again too, and I daren't try this in case it screws the sound up again. But, not having the Ubuntu-minimal package installed means that future upgrades may not work.

---

### Post by greenbakk on 2007-02-18
Hi Rollerbob,

Thanks for you post. It helped me getting microphone on my Audigy 4 working. So, I can use Skype now! 
However still having some issues:
- mic level control button is randomly moving and thus changing my input level
- it looks that mic input is always on even when no program uses sound device 

Do you have the same experiences?

cheers

Alex

---

### Post by Grimmy on 2008-02-26
Rollerbob:  Thanks for the info.  It helped me a lot.

I just had a problem with my Microphone on my standard Audigy 4 in 7.10 so I stumbled across this post.

I couldn't get the instructions in the Wiki to work exactly but I didn't have to do it all.

I just downloaded Alsa Driver ( version 1.0.16 at time of writing ) and extracted it.

I was getting errors doing make clean, but I eventually got it working with just the configure line....  i.e.

```

./configure --with-cards=emu10k1 --with-oss=yes --with-sequencer=yes
make 
sudo make install

```

I then ran ALSA Mixer as described by Rollerbob and changed the levels.

I then tested with Audacity and Teamspeak2 and my microphone worked.   :D

---

