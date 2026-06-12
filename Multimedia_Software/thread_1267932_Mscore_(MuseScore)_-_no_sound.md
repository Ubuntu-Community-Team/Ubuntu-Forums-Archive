---
title: "Mscore (MuseScore) - no sound"
date: 2009-09-16
forum: Multimedia Software
---

### Post by peterroots on 2009-09-16
Has anyone got mscore to play sound on kubuntu9.04?
I first got a problem that mscore could not access /dev/rtc (which points to /dev/rtc0) so I changed the file permissions from 600 to 666 and now mscore reports the following

Suspending PulseAudio
RtcTimer::setTimerFreq(): cannot set ticks 1024 on /dev/rtc: Permission denied
  precise timer not available
MidiSeq:start(): no midi timer available
Cannot start I/O
sequencer init failed

some very old posts suggest
sudo sysctl -w dev.rtc.max-user-freq=1024
to fix the problem but I get back 
error: "dev.rtc.max-user-freq" is an unknown key

Other posts suggest using a jack server but I don't especially want to install any other sound servers (using pulse at the moment and works for everything else)

I would be happy to get mscore working with either alsa or midi (noteedit works with midi, using timidity on my system)

If I set mscore to use Alsa it fails with this

Suspending PulseAudio
Alsa_driver: can't set sample rate to 0.
init ALSA audio driver failed
init ALSA driver failed
init audio driver failed
sequencer init failed

presumably because I can't get a sample rate value to stick in the mscore settings for alsa. The device is set to hw:0 which does stick but sample rate and period size can be set but vanish after restarting.

Any suggestions?

---

### Post by advocate 21 on 2009-10-04
i have the same problem, only with ubuntu 9.04, not kubuntu. 
please help.

---

### Post by kuadra on 2009-10-09
I've just checked my MuseScore setup. Under "Edit" -> "Preferences" -> "I/O", if I switch to "Use midi output", I get the same error as you've reported.
I've activated the "use internal synthesizer" and selected a sound font (in my case */usr/share/sounds/sf2/FluidR3_GM.sf2* from the package *fluid-soundfont-gm*). Furthermore, I've selected ALSA instead of Portaudio because I've not portaudio server running.

Hope it helps.

---

### Post by peterroots on 2009-12-12
rather gave up on this but as I now have Kubuntu9.10 I thought I would revisit it.
still does not work
With Midi (using timidity which works with other things) I still get
```

peter@PeterLT:$ mscore
/usr/bin/mscore: 27: list: not found
Using JACK for audio
RtcTimer:: fatal error: open /dev/rtc failed: Permission denied
MidiSeq:start(): no midi timer available
Cannot start I/O
sequencer init failed

```
Despite what it says above I am NOT using jack, I don't have it installed and it is not selected in the i/o tab of mscore
If I chmod /dev/rtc0 (this is where /dev/rtc points to) I get this
```

peter@PeterLT:$ mscore
/usr/bin/mscore: 27: list: not found
Using JACK for audio
RtcTimer::setTimerFreq(): cannot set ticks 1024 on /dev/rtc: Permission denied
  precise timer not available
MidiSeq:start(): no midi timer available
Cannot start I/O
sequencer init failed

```
if I select 'use internal synthsiser' and alsa (without selecting jack and with a sound font selected)
```

peter@PeterLT:$ mscore
/usr/bin/mscore: 27: list: not found
Using JACK for audio
Alsa_driver: can't set sample rate to 0.
init ALSA audio driver failed
init ALSA driver failed
init audio driver failed
sequencer init failed

```
I can select any value I like for sample rate and period size but they have always gone again after restarting mscore

aplay -l gives me this
```

peter@PeterLT:$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
previously I was using pulse audio but when I did a fresh install of 9.10 pulse audio server was not installed (though the xine and gstreamer pulse plugins were)

---

### Post by Panserbjorne on 2009-12-23
I've read in another topic that in Preferences>I/O settings>
changing the ALSA Audio device from default to hw:0 solves the problem

...It works fine to me...
Greets!!

---

### Post by peterroots on 2009-12-23
Glad you have got it working, thanks for the tip.
Unfortunately for me, whether I use default or hw:0 for the alsa device I always get a failure with 'Alsa_driver: can't set sample rate to 0.'
Whatever value I enter for sample rate or period size vanish again after restarting Mscore

---

### Post by jamh on 2011-10-25
What Peterroots said.  

Also, add to your /etc/modules:
lp
sbp2
snd_seq

and restart.

---

### Post by peterroots on 2011-10-26
Jamh
Thanks for your suggestion - I failed totally on Kubuntu 9.04 and 9.10 and removed Mscore.
With Kubuntu 11.04 and 11.10 Mscore works fine again for me, with no extra fiddling around to fix it. I have no idea if 10.04 or 10.11 worked though as I had Canorus installed then (which did work, and still does but I prefer Mscore)

---

### Post by hg21 on 2011-11-26
Sorry this is a bit off topic.

I can get sound OK but musescore is very unstable it crashes frequently. I cannot get the File>parts mechanism to work.  Could you tell me if you are using 64bit Kubuntu. I wonder if that is my problem?

On 11.10 Kubuntu

Thanks
Howard

---

### Post by peterroots on 2011-11-26
I have never used the parts bit on the file menu (I only do some very occasional mucking about with this). I just tried it and it seems to work, though not entirely sure what I should expect.
Whole thing seems stable enough (I have not had a crash) and I am using 64bit with timidity for midi output

---

