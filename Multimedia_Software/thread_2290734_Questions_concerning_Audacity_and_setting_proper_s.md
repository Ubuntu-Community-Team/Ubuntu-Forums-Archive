---
title: "Questions concerning Audacity and setting proper sound levels"
date: 2015-08-14
forum: Multimedia Software
---

### Post by cscj01 on 2015-08-14
I have Ubuntu 14.04.02 x64 and Audacity 2.0.5.  My questions concern setting appropriate sound levels to maintain the greatest SNR possible.  I have used, at one time or another, PulseAudio Volume Control, alsamixer, and the Sound applet in System Settings.  It seems that these all can affect the sound levels of line or microphone input.  Since these three applications can change settings in each other (at least in some cases), there must be some rules for their uses.  One might possibly be, if I am setting sound levels, which should I use and in what order?  Another could be, is there one of these three that can handle everything?  I know that PulseAudio is the audio server for Ubuntu, but it seems to me that I cannot completely control input sound levels in Audacity from PulseAudio Volume Control alone.  Am I wrong?  Another question is, in PulseAudio Volume Control on the input devices tab, what is the reference point labeled Base?  Finally, is there a tried and true method for setting the volumes so that one can obtain the best SNR possible?

---

### Post by TheFu on 2015-08-15
I'm not an expert and as soon as I display my ignorance, someone else with more knowledge will answer. ;)

I use the levels inside Audacity. The audacity online manual is pretty good, as I recall.  When setting levels, my goal is to have them as high as possible, but never hit the red. NEVER.

I do not touch anything else while recording.

---

### Post by tgalati4 on 2015-08-15
You will have to experiment with your hardware.  As a rule-of-thumb, you want to pay attention to the "gain stages" in your signal chain.  You want to keep each one at about 70% of maximum, where maximum is defined as digital clipping or audible distortion.

Microphone Transducer Level (70%)-->Mic Pre-amp Level (70%)-->Multi-channel mixer (PCM) (70%)-->digital recording.  Maximum signal-to-noise is a goal, but you need sensitive, calibrated test equipment to measure accurately.  Otherwise, you use your ears to determine if the final outcome is acceptable.  The intended purpose of the recording also determines the audio fidelity required.

Where problems happen:

1.  Microphone is not appropriate for sound levels you are trying to record.  You can't use a built-in laptop microphone to record a rock band session.  Expensive microphones are expensive for a reason.
2.  Preamps need to be matched to the microphone or pickup or other equipment.  Otherwise you get a gain mismatch and distortion.  For pairing, you need to consider impedance of the connection and reviews from others as to what works with what.
3.  As you mix more channels, the level of each needs to be turned down so that the summation (mix) doesn't exceed clippling levels.  24-bit recording has more dynamic range than 16-bit (CD Quality).  
4.  Your mixing and monitoring equipment needs to be high quality otherwise your final mixes will never be better than that equipment.  You can't effectively mix with earbuds--you need studio-quality speaker monitors or headphones.

As far as software control of levels, most controls will reach down to the hardware and control the same thing.  However, many switches, boost levels, etc are hidden for simplicity, so you have to research and dig around to find them.

When recording, one normally doesn't need *pulseaudio* since that is designed to control the sound levels of several applications at once on the desktop.  Use *alsamixer* to set your levels for *audacity* or use audacity's controls.  If you want to record drum tracks and record mult-track sessions, then consider learning *jackd*.

If you need *pulseaudio* (for recording game sounds) then install the *pulseaudio* tools:

pulseaudio-utils
padevchooser - PulseAudio Device Chooser
paman - PulseAudio Manager
paprefs - PulseAudio Preferences
pasystray - PulseAudio controller for the system tray
pavucontrol - PulseAudio Volume Control
pavumeter - PulseAudio Volume Meter

---

### Post by TheFu on 2015-08-15
See - my post helped! <rbg>

---

### Post by cscj01 on 2015-08-18
Thanks for the reply.  One thing I'm confused about is that Audacity no longer allows for the settings of levels.  So I must use an external source.  I do not seem to get good results with alsamixer.  I can set the line level at 18 and still get flat wave forms.  I used to be able to use much higher input volume levels without flattening or clipping.  My issue is if I have to set the input level very low, the noise component is going to be a larger part of the wave, thereby lowering the SNR.  Is that correct?  If so, I need a single source for setting the input levels so that I can get as much of the signal as possible without flattening the wave form or clipping.  Nothing I do seems to work well anymore.  How might jack make things better?

---

### Post by TheFu on 2015-08-18
Using a quality mic? All the cheap ones I've tried didn't work well at all. Found a relatively cheap ($35) USB mic that seemed tuned for audacity out of the box. Samson is the brand. OTOH, I'm easily impressed and have control over the ambient noise.

---

### Post by tgalati4 on 2015-08-18
I'm running 2.05 and it has sliders for the input channels (on 14.04 system).  What version are you using?  If you are using an internal microphone jack, then check the "microphone boost" switch.  If you have a microphone plugged into a Line-in jack, then you need a preamplifier to get a usable signal.

The sliders in audacity go from 0.0 to 1.0, I don't know what "18" level means.  Is that -18 dB or +18 dB?

---

### Post by cscj01 on 2015-08-19
> **tgalati4 said:**
> I'm running 2.05 and it has sliders for the input channels (on 14.04 system).  What version are you using?  If you are using an internal microphone jack, then check the "microphone boost" switch.  If you have a microphone plugged into a Line-in jack, then you need a preamplifier to get a usable signal.

The sliders in audacity go from 0.0 to 1.0, I don't know what "18" level means.  Is that -18 dB or +18 dB?Version is 2.0.5.  I have sliders for input and output, but they don't seem to do anything.  The input slider goes from 0 to 1 as you said.  Perhaps that setting is having some effect, although I have not noticed it in the meters or the wave form.  Does your slider affect either the wave form or the meter reading?  18 is a percentage figure from alsamixer which indicates a 0db gain.  19 is 0.75db gain, 20 is 1.5db gain, etc.  I presume that since dbs are logarithmic, they must be mapping db gain to a percentage gain.  100% is a 30db gain.  I am using an internal mic jack, so I'll check the microphone boost.  The mic boost allows for 4 settings; 0db, 10db, 20db, and 30db.

---

### Post by tgalati4 on 2015-08-19
You need to select "ALSA" and the correct input device in the audacity toolbar.  If you are using a laptop, built-in microphone, then you need to speak into it, very close.  The wave forms are barely noticeable for normal speaking.  If you have an external microphone, then you may need phantom power (5VDC, 24VDC, or 48VDC) to get the microphone to wake up.  Most laptop microphone jacks put out 5VDC for headsets, but that won't power a real dynamic microphone.

What microphone are you using?

Post a screenshot of the *audacity* track.  Be sure to zoom in on it, because the waveforms will be flat for everything expect professional microphones or external microphone preamps.  Microphone boost will give you some squiggles in your track, but a lot of noise as well.

You can generate pure tones in *audacity*.  Create some 30-second clips of 200 Hz, 400 Hz, 800 Hz, 1600 Hz with an amplitude of 0.7 then play them back on your system.  They may be loud.  Store the tracks on an mp3 player and then play them on a stereo system or use a cable to feed them directly into your microphone port.  Adjust the levels.  Compare the pure track with the recorded track.  You may be surprised at how difficult it is to get clean recordings with a computer.

If you want to get sophisticated, you can time-align the pure tone with recorded tone and use the subtract function to get just the noise.

---

### Post by TheFu on 2015-08-19
> **cscj01 said:**
> Version is 2.0.5. 
<snip>
 Does your slider affect either the wave form or the meter reading?


Same version here.

The sliders GREATLY effect the USB mic I'm using.
[http://www.amazon.com/Samson-Mic-Portable-Condenser-Microphone/dp/B001R76D42/](http://www.amazon.com/Samson-Mic-Portable-Condenser-Microphone/dp/B001R76D42/)
It is amazing for the price. The reviews are true, IMHO.

---

### Post by tgalati4 on 2015-08-19
There are a lot of podcaster blogs that give microphone reviews that work well for podcasting.  Blue Yeti, Samson, Shure, Sennheiser, there are a bunch. Those microphones provide the proper gain levels to make excellent recordings with *audacity*.  So you either have a configuration issue, or a crappy microphone.  It's a common problem.

---

### Post by TheFu on 2015-08-19
> **tgalati4 said:**
> There are a lot of podcaster blogs that give microphone reviews that work well for podcasting.  Blue Yeti, Samson, Shure, Sennheiser, there are a bunch. Those microphones provide the proper gain levels to make excellent recordings with *audacity*.  So you either have a configuration issue, or a crappy microphone.  It's a common problem.

Exactly. I have 5 different $10 microphones. None worked well, if at all.

For a single input, usb, audio source, the Samson is good and cheap. 

If you need multiple input sources, a mixer will probably be desired - perhaps from Behringer - but these don't work with USB inputs, at least not the cheap mixers. ;(

---

