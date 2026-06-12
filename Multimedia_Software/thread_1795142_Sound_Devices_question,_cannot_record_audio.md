---
title: "Sound Devices question, cannot record audio"
date: 2011-07-02
forum: Multimedia Software
---

### Post by briandorling on 2011-07-02
Hi,
I had problems in 10.10 and upgraded to 11.04, but that did not help. I want to record sound in VLC. To do that I must specify the input audio device, but I cannot find that, looking in /dev
I cant seem to find /dev/snd /dev/dsp, in /dev/snd I have:
```
by-path  controlC0  hwC0D0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D1p  seq  timer

```   

I can hear the sound, coming in via Analog line in. Strange thing is though that the master volume control in alsamixer does not alter the volume of that input, it alters the volume of
stuff played by mplayer (e.g.) and others. 

So basically something is totally screwed up. Can I maybe totally remove all sound support and reinstall? This is an Ubuntu that has been upgraded a few times over the years, and the mainboard (sound is on that) did change last year. 

General listening to music etc, or skype works without problems.


Anyway here's a few displays:

> 
brian@brian:/dev/snd$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


brian@brian:/dev/snd$ lsmod | grep snd
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  3 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm


---

### Post by skitter on 2011-07-04
I found this thread while trying to get the same sort of functionalty (record 'what you hear') working in Audacity.  I was able to get it to work on my machine by going to the sound preferences applet and then the hardware tab. I changed the profile from Analog Stero Duplex to Analog Stero Output, and I'm now able to use Audicty to record any sound coming out of my PC.  I hope that helps.

---

### Post by arizonalarry2 on 2011-07-04
I can hear myself in my microphone, if I try Sound Recorder the playback is silent and if I try Audacity it crashes as soon as I hit the record button.

---

### Post by arizonalarry2 on 2011-07-04
> **arizonalarry2 said:**
> I can hear myself in my microphone, if I try Sound Recorder the playback is silent and if I try Audacity it crashes as soon as I hit the record button.


Okay, got it working... kinda...

Here's what I did -

I start up the Sound Recorder and go to \File\Open Volume Control to open the Sound Preferences dialog box. I go to the \Input tab and see that the volume control is greyed out, there is no action on the Input Level if I talk into the microphone and there are no devices listed for the sound input. 

I then click on the \Hardware tab and in the 'Settings for the selected device' it says 'Analog Stereo Output' so I change it to 'Analog Stereo Input'. Going back to the \Input tab the volume control is now working and the input level is moving as I speak into the microphone. Going back to the Sound Recorder I talk into the microphone and the level indicator is moving to show the input is indeed going in. However if I hit playback I hear nothing but silence. If I save the file there is nothing but silence. 

Now I go back to 'Settings for the selected device', select 'Analog Stereo Output', close the Sound Preferences dialog box and go back the the Sound Recorder. Now when I hit playback I hear the recording. However, if I try to make another recording there is no input.

So basically when I want to record I have to select 'Analog Stereo Input' (which disables the output) and when I want to play back I have to select 'Analog Stereo Output' (which disables the input). 

Does anyone know how to make them both work at the same time so I don't have to keep going back and forth? Thanks.  


... still haven't figured out the Audacity thing :(

---

