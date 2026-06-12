---
title: "Audacity:  Can 'speak', but not 'hear' (!)"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2006-12-01
I've been struggling with this for a couple of days:

I can PLAY all manner of files via Audacity, but I can't record from ANY source.

I've got my receiver plugged into my line-in jack on my sound card.  I know the source material is arriving, because I can hear it through my speakers (without any audio software running).

Audacity has the following input choices:  VOL, LINE, MIC, CD, LINE1, PHONEIN, PHONEOUT, and VIDEO.

I have tried to record from ALL of them--but I just get a flatline waveform.

I've checked alsamixer--and the linein sliders raise and lower the volume of the input signal...

This is a dual-boot box, and XP (via Audition) records everything fine, so it wouldn't seem to be a hardware issue...

Any advice??  ](*,)

---

### Post by logos34 on 2006-12-04
Install alsa-oss if needed.

(gnome desktop) From the menu bar System>Preferences>Sound>Sounds tab.
Uncheck 'Play system sounds' (and ESD mixing if necessary).

In Audacity set mixer source to 'Vol' (='stereo mix' in Windows ver.)

Check that recording is set for '2 (stereo)' in Preferences>Audio I/O.

Set the Input level meter to 'monitor input'.   If audio is playing both channels should light up.  

If you can record but the result is distorted, try changing the project sampling rate from the defualt 44100 to 48000Hz.

See if that helps.

If you get "error initializing audio I/O layer" and you've disabled system sounds, try launching Audacity from terminal as root:

$ sudo audacity 
or
$ sudo aoss audacity

Set mixer to 'IGain' and select 'monitor input'.


Good luck.

---

### Post by wilberfan on 2006-12-11
> **logos34 said:**
> Install alsa-oss if needed.

(gnome desktop) From the menu bar System>Preferences>Sound>Sounds tab.
Uncheck 'Play system sounds' (and ESD mixing if necessary).

In Audacity set mixer source to 'Vol' (='stereo mix' in Windows ver.)

Check that recording is set for '2 (stereo)' in Preferences>Audio I/O.

Set the Input level meter to 'monitor input'.   If audio is playing both channels should light up.  

If you can record but the result is distorted, try changing the project sampling rate from the defualt 44100 to 48000Hz.

See if that helps.

If you get "error initializing audio I/O layer" and you've disabled system sounds, try launching Audacity from terminal as root:

$ sudo audacity 
or
$ sudo aoss audacity

Set mixer to 'IGain' and select 'monitor input'.


Good luck.

Oooh..you got my hopes up!   I *did* have "Play system sounds" and "ESD Mixing" selected, so I unchecked those...

Alas, no input meter activity, and a flatline recording...  Running audacity as sudo made no difference.

Still baffled!   ](*,)

---

### Post by wilberfan on 2006-12-11
Success???

For no other reason (than desperation) I started a KDE session and started playing with KMixer (is that what it's called?).  It wasn't until I turned on something called "ADC" that I got a response on the VU meter in Audacity!!

In Gnome, I had to turn on "ADC" and "ADC Capture".   But it's weird:  moving the ADC slider only affects the LEFT channel (in gnome).  I have to keep it near max to get even left-and-right levels...   Also, the Input Volume slider in Audacity merely controls the levels coming out of the speakers while I'm recording--NOT the recording levels.   (?!)  I have to use the AlsaMixer input slider to control the recording levels.  (Maybe this is logically consistent--but to this noob it's confusing!) 

I have NO idea what any of this means!   Can anyone explain what ADC is?  And why it would affect recording in Audacity?

:-k

---

### Post by logos34 on 2006-12-12
Hello again.

'ADC'=Analog-to-Digital Converter.  You're piping audio from your stereo to your pc through the line-in jack so it's sending an analog signal to your soundcard which then converts it to digital form or PCM (pulse code modulation). Same thing if you plug a microphone into your pc: the mic sends sound (analog) to be coverted into a digital signal. The opposite happens when you send out audio to be played through your stereo: the mp3 playing in your music player gets converted by the DAC (digital-analog-converter) before it leaves the pc.  (Of course none of this is necessary if your soundcard has digital out jacks and you have a newer digital stereo receiver with toslink/optical or coaxial input).

Audacity records by reading that PCM signal--your system sound--as a (uncompressed) wav, which you can then export as either lossless or lossy format (mp3 or ogg only).  I also have my stereo hooked to my computer (but as line-out), so I reversed it to line-in like yours: on the stereo side switched the RCA plugs to audio-out position, then connected it to the (blue) line-in jack on the pc.  In Audacity I set the source to 'line'.  Works.  Except this time only the Input volume on the mixer (ie Capture in gnome sound) affects record level.  When I record internal audio (streamed audio) I have to adjust both the output/PCM and input/capture levels to avoid clipping.  

Verify your capture isn't muted.  Gnome volume control>capture tab.  There should not be a red x through the little mic icon. (If no capture tab displayed, then edit>preferences>check capture).  In Alsa mixer, the 'record' box at the bottom of the capture slider should be checked.

The slider issue: on the playback tab in gnome volume control make sure the tiny chainlinks are connected (between bottom of slider and mute button).
Or in alsa mixer, check 'lock' box.

---

### Post by logos34 on 2006-12-12
well i've been playing around with alsa mixer and audacity for the last half hour and can't figure out why your input is controlling the speakers, not the recording level. Thought maybe 'Play other tracks while recording new one' and 'Software playthrough' options in Audacity prefs>i/o inputs had something to do with it, but no.

But if you can adjust it through alsa mixer at least that's something.  On my pc I notice that the alsa PCM slider and the output slider in Audacity move in sync no matter which slider you move, and control speaker level only.  The audacity Input volume slider and alsa capture slider move in sync only if the 'rec' box is checked; if I uncjeck it the VU meter dies and audacity input slider drops to zero.  I have to click back on the audacity input slider to get the volume back. I'm getting a nice big 2-channel waveform when I hit record button. 

At least you're making some progress.  About the only thing I can suggest is keep fiddling with audacity and alsa mixer settings.  Try reboot.  You could always reinstall audacity with Synaptic or even try compiling the latest 1.3 beta version--you can install both side by side. I tried compiling but it failed--problem related to wxgtk widgets dependency.  IF all else fails head over to audacity forums.

---

### Post by wilberfan on 2006-12-13
> **logos34 said:**
> 
At least you're making some progress.  About the only thing I can suggest is keep fiddling with audacity and alsa mixer settings.  Try reboot.  You could always reinstall audacity with Synaptic or even try compiling the latest 1.3 beta version--you can install both side by side. I tried compiling but it failed--problem related to wxgtk widgets dependency.  IF all else fails head over to audacity forums.

Hey, I really appreciate the explanation!  It helps--and it makes sense that "ADC" would stand for Analog to Digital conversion!   My receiver is a Sansui from the early 70's (!) and, yes, no digital inputs on either sound card--so that makes sense.

I *am* using the latest beta of Audacity, btw.   More features and looks MUCH better!  I'll continue to experiment with settings, etc.  

Thanks again for your input!

---

### Post by wilberfan on 2007-03-04
> **logos34 said:**
>   

If you can record but the result is distorted, try changing the project sampling rate from the defualt 44100 to 48000Hz.

I GOTTA REMEMBER THAT ONE!  Is there a way to make that setting a default?  (Haven't found it yet.)

I've been trying to get Audacity to record properly in openSuSE 10.2....   This piece of advice made all the difference (That, and selected "i2s in" as the capture source...  :guitar:

---

### Post by xen-uno on 2008-03-08
ADC & DAC are easy enough, but why would tweaking on the ADC slider affect playback volume when the source is digital (ie playing an ogg). They seem to be intertwined volume wise in AlsaMixer. I would think ADC would only control the recording side. I'm using an MAudio 2496.

---

