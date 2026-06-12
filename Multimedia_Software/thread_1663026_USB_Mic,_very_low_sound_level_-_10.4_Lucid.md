---
title: "USB Mic, very low sound level - 10.4 Lucid"
date: 2011-01-09
forum: Multimedia Software
---

### Post by jsland on 2011-01-09
Ubuntu 10.4 recognized a Samson C01U usb microphone when plugged in the very first time and the mic could be selected in Sound Preferences on the Input tab.

gnome-alsamixer also showed the device from the beginning with a single volume control.

After many hours of work backports-modules were removed and alsa-driver-modules reinstalled.

There is now, finally, at least a signal that Applications|Sound & Video|Sound Recorder can record.  The recording is very faint, but its there, along with an industrial amount of noise.

alsamixer gives 2 warnings about 'no idea what to do with line-in mode and Mic-in mode'.  Forum posts have alerted there can be problems if both of these are on at the same time.  One or the other should be muted to avoid a conflict.  Muting line-in or Mic-in has no effect on the error messages.  Maybe these warnings are unrelated to the core issue and can be ignored? 

The machine here is a desktop with 2 soundcards and playback works without any problem.  Both JACK and Ardour seem to be working fine.  Just no recording capability thru the USB Mic.

Can someone shed some light on the signal strength issue and what may be needed to get the mic to work.

---

### Post by lidex on 2011-01-09
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by RaumTrug on 2011-01-09
Hi! I have the very same mic, but not under 10.04 (I still run 9.10, might install 10.04 soon). I have no real clue about the mic & pulseaudio, because I use it with jack/pure alsa, only. it is not really that great, but nice because you can use it with laptops to record mobile, with no need for a power line. handled right, it gives quite a clean signal for me, considering the usb-powered soundchip built into it. but it's sound is a bit "flat", lifeless if you know what I mean...enough bla

but: the mic has a suble "twist" built into the soundchip, that make it work different to other microphones:

I noticed, it delivers a (capture channel only, no playback of course...) stereo signal. the signal in the left channel is the loudest, the right channel contains the same signal, but not quite as loud, and (note!) "inverted". so your problem could be, that when you record from both channels, and it gets mixed together to mono, the right channel cancels out lots of signal strength from the left channel. try recording stereo, and you can watch it: the left is lound, the right is half volume & inverted. try to record only the left channel, it should be much better!

I guess the people designing the mic have done this out of various reasons (not that I'm particularely fond of that descision :-P):

- you get more gain range - the (stereo) in signal can be controlled with 2 sliders (even if you only see one, it's stereo, good alsamixers can control left and right seperately) - each controls one gain stage of the built in soundchip. the first stage is the right channel, and the second the left.

- inverting the signal of the first stage at the right point can cancel out some noise the circuit is catching - because the second stage is catching parially the same noise/inteference, inverting the first stage at the right point will eleminate some of it. I guess you can even tune around a little with left/right balance in the mixer.

- they just had that stereo chip lying around/scheduled for that project, and some engineer had a beer too much the evening before...and was too lazy to tread the chip in a way so it works "mono" or with the right channel doubled ;)

of course it really sucks that they've left in the right signal, and have not doubled the left signal to both channels. other usb-mics, even from the same manufacturer, have it that way. with jack, I just ignore the "capture_2" and feed "capture_1" (the left channel with the louder signal) to the recording progs only. I normally use the mic as "interface" in capture-only mode, and in case I need monitoring, I add another sound device with playback with "alsa_out" or "audioadapter" (jack2 only). that way it gives the best results.

to make it work with pulseaudio - no clue, you probably need to create some routing, i.e. an asound.conf definition that doubles the left channel, and make pulse use that instead of the direct device. or create a channel mapping for pulse for that device that does the same. but as said: i don't use pulse, and know little about configuring it, maybe someone else.

hope that helps!

---

### Post by lidex on 2011-01-09
In pulse you can do this:
Go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

My question is does the OP use pulse?

---

### Post by RaumTrug on 2011-01-09
hmm...if those sliders affect volume of the mic on an alsa-mixer-level, it won't work that way.

thing is, the left channel is fed with the signal you also receive from the right channel. so if the amplifier for the right channel is set to zero, the gain stage of the left channel will have nothing to amplify, and the complete signal will be zero...

---

### Post by jsland on 2011-01-09
Alsa upload located at;

[http://www.alsa-project.org/db/?f=9cfd316dfb77e9397d0584d5814adb2c8a36487c](http://www.alsa-project.org/db/?f=9cfd316dfb77e9397d0584d5814adb2c8a36487c)

Sound Recorder and the pavucontrol vu meter only show signs of life when the hardware is listed as Analog Mono.  Analog Stereo setting shows no active vu meter in pavucontrol.  These settings including digital stereo in were run thru the grinder yesterday and found not to work.

Web searches have a couple postings detailing internal workings of the ADC chip and the cascade of signals.  This detail may be helpful later but is jumping the gun a bit at the moment:).

Need a clarification on OP.  To run JACK pasuspender is used in server path.

---

### Post by lidex on 2011-01-09
> **RaumTrug said:**
> hmm...if those sliders affect volume of the mic on an alsa-mixer-level, it won't work that way.

thing is, the left channel is fed with the signal you also receive from the right channel. so if the amplifier for the right channel is set to zero, the gain stage of the left channel will have nothing to amplify, and the complete signal will be zero...

Did you try it?

> **jsland said:**
> Alsa upload located at;

[http://www.alsa-project.org/db/?f=9cfd316dfb77e9397d0584d5814adb2c8a36487c](http://www.alsa-project.org/db/?f=9cfd316dfb77e9397d0584d5814adb2c8a36487c)

Sound Recorder and the pavucontrol vu meter only show signs of life when the hardware is listed as Analog Mono.  Analog Stereo setting shows no active vu meter in pavucontrol.  These settings including digital stereo in were run thru the grinder yesterday and found not to work.

Web searches have a couple postings detailing internal workings of the ADC chip and the cascade of signals.  This detail may be helpful later but is jumping the gun a bit at the moment:).

Need a clarification on OP.  To run JACK pasuspender is used in server path.

Pretty much follows what RaumTrug was saying. Did you try unlocking the sliders and reducing levels on one channel?

OP= you (original poster)

---

### Post by jsland on 2011-01-10
The following was done shortly after Raum posted and again before this post;

Mic was set to analog stereo.  It's set up to be alive in Sound Preferences.
Gnome-alsamixer will only show a single slider with the stereo setting.  pavucontrol will show 2 sliders which can be unlocked and adjusted independently.  The vu meter below the stereo sliders is dead as a doornail in pavucontrol and Sound Recorder.  Only when the mic is set to analog mono are the vu meters active.  When changes are made to hardware settings the C01U has to be reselected in Sound Preferences because input defaults to the sound card mic.

What mixer are some of the other forum posters possibly using that allows them to get inside the USB Mic and adjust the analog gain stage before the ADC and/or the digital outputs after the ADC?

From my troubleshooting perspective it looks like 2 candidates:

1.   Highly possible from having set the computer up to run sound output on IEC958, which works great and has excellent sound quality, I've introduced some bugs or non-standard settings from the trial & error necessary to get that working a long time ago.

2. There is a setting buried somewhere along the line of thought Raum has but the adjustment is not available in pavucontrol.

Path 2 is my guess as the hardware is recognized correctly.

Path 1 will require your skills Lidex.    

Am still wondering about the warnings for line-in and mic-in.  Can these be ignored or should they be pursued.

What do the backports modules do regarding hardware.  A broader list of supported devices?

---

### Post by jsland on 2011-01-12
Went thru the process of creating a new user account and logging in as new user.

Sound recorded from the USB Mic was significantly louder.  Still weak with alot of background hum but more easily heard.  Stereo and mono hardware settings were tried and both worked.  Unlocked sliders in stereo responded as you would generally expect.  Vu meter still shows very low volume source with sliders at Max.

---

### Post by lidex on 2011-01-13
I just looked up your mic and see it's a condenser. They tend to have a much lower output than dynamics and generally require pre-amplification. Due to the low level signal, the noise floor is pretty high when you crank it up. Can you post a screenshot of alsamixer capture devices?

---

### Post by RaumTrug on 2011-01-13
as one last note from me:

maybe the op could try to record via jack (using some simple jackified recording software, for example mhwaveedit) - use alsamixer to play with the input level. normally 3/4 of slider range (both left&right) is enough for me, and I still have to take care not to shout into the mic too loud, or it'd clip

try to record it stereo, then discard the right channel. or connect the system->capture_1 to all of mhwaveedit's inputs (L&R).

this could rule out problem's with the alsa-driver, or with the hardware itself, as pulseaudio is bypassed - as said above, with 9.10 using jack I get good results with the mic.

btw, at least at the point the alsa-info script was run, the mic was cranked up to 100%, just look at the "Mixer controls" part...

---

### Post by jsland on 2011-01-13
Control settings;

---

### Post by jsland on 2011-01-13
Took a quick look at mhwaveedit.  The program doesn't like something in the configuration and will not record with JACK being started before opening mhwave.  Comes back with the following error:  With JACK, the only supported recording format is Floating-point, single precision, 44100 Hz.  Even though JACK Setup parameter is 44100.

The normal program used for recording is Ardour.  The Mic can be recorded and heard, barely, when settings are cranked.  Same response as Sound Recorder.

---

### Post by lidex on 2011-01-13
Perhaps you can try an outboard pre-amp.This is an informative thread over on the ubuntu-studio forum:
[http://ubuntuforums.org/showthread.php?t=1076300](http://ubuntuforums.org/showthread.php?t=1076300)
I don't spend a lot of time there but you should poke around and maybe ask some questions. Those guys are pretty knowledgeable on this kind of thing.

---

### Post by nerdy_kid on 2011-01-13
quick, easy and dirty fix:

run paman (pulseaudio manager) click the devices tab look under "sources" for your mic, select it hit properties raise that volume slider as far as you want -- goes up to 400%.  This value is remembered by pulseaudio, not sure if it will remember it once you unplug the mic though.  good luck

---

### Post by jsland on 2011-01-14
Give me a minute to stop laughing about the MS crack above.

Will investigate paman further although it may not be able to get the total job done.  In order for JACK to work as the I/O controller for Ardour it's necessary to stop pulse audio.  Maybe some settings will stick so I will not discount it until some time is put in.

Used to run ubuntustudio here before upgrading to Karmic.  Loading the generic version of 9.10 was so much less work than wrestling with studio it really brought home the point how far ubuntu has come. Nearly everything worked right out of the gate.

If a pre amp were used it seems more logical to go back to the standard Mic version with XLR cables and an analog pre.  Was trying to avoid that as space here is somewhat limited.

Lidex.  Thanks for the link.  The 1st page was read last week and probably has alot to do with considering the XLR route due to quality/flexibility/control issues discussed in those posts.

---

### Post by nerdy_kid on 2011-01-14
> **jsland said:**
> Give me a minute to stop laughing about the MS crack above.

Will investigate paman further although it may not be able to get the total job done.  In order for JACK to work as the I/O controller for Ardour it's necessary to stop pulse audio.  Maybe some settings will stick so I will not discount it until some time is put in.

Used to run ubuntustudio here before upgrading to Karmic.  Loading the generic version of 9.10 was so much less work than wrestling with studio it really brought home the point how far ubuntu has come. Nearly everything worked right out of the gate.

If a pre amp were used it seems more logical to go back to the standard Mic version with XLR cables and an analog pre.  Was trying to avoid that as space here is somewhat limited.

Lidex.  Thanks for the link.  The 1st page was read last week and probably has alot to do with considering the XLR route due to quality/flexibility/control issues discussed in those posts.

i think you might be able to keep pulseaudio running, it has a jack module but not sure if it would work all the way for you.  Here is an old thread, but it still should be useful:  [http://ubuntuforums.org/showthread.php?t=548178](http://ubuntuforums.org/showthread.php?t=548178)

---

### Post by jsland on 2011-01-17
Spent some time yesterday trying to get the C01U mic working on a Win7 machine.  The mic comes packaged with software for cakewalk Sonar LE.  When the mic didn't work right out of the box on Win7 the towel was thrown in quickly.  Not about to spend much time troubleshooting that greasy watermelon.

With the work done on 10.4 during the past 2 weeks it seemed logical to at least take another look for the sake of comparison.  Bottom line is the Mic operates about the same in both Operating Systems.

Each one is a desktop machine with AMD Athlon 64x2 processors.  Any opinions on whether the CPU might be creating a bug issue with the hardware and USB drivers.

---

