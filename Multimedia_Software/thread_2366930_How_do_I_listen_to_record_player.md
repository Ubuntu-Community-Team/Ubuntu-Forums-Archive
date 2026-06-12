---
title: "How do I listen to record player?"
date: 2017-07-23
forum: Multimedia Software
---

### Post by cdavila on 2017-07-23
I am trying to listen to audio from a turntable using the soundcard  on my Ubuntu 16.04 system. The audio is connected to Line 0 (stereo) on  my soundcard and I am unable to hear it. As suggested elsewhere, I tried  running Audacity and PulseAudio Volume Control. I have the following  settings on pavucontrol:
  
[LIST]
[*]Configuration:  Analog Stereo Duplex 
[*]Input Devices: Monitor of Built-in Analog Stereo 
[*]Output Devices: Line Out (plugged in, speakers) 
[*]Recording Devices: Monitor of Built-in Audio Analog Stereo 
[/LIST]
  My input and output devices on Audacity are set to:

  recording device: pulse: Line 0
output device: pulse
  
Based on other solutions I have seen on this and other forums, this  should work. However I only get silence. Sound otherwise plays fine. can  listen to CD audio, videos, etc. Would appreciate any suggestions...Windows seems to handle this with no problems, am surprised that Linux cannot.

---

### Post by Bucky Ball on 2017-07-24
Welcome. USB turntable? Plug in, switch it on, then run this in a terminal.

```
lsusb
```

What make and model of turntable? When you are playing music from the turntable via Audacity, look in PAVContol. In playback, is there a section for Audacity and anything bouncing up and down on the level meter?

It can sometimes take some considerable experimentation and tweaking of settings to get audio out of external devices in Ubuntu. Don't be surprised as the majority of hardware in not made to work with Linux, manufacturers give no support for Linux, but have possibly provided you with a disk with Windows drivers. 

If it is a regular, standard USB device, there should be no reason we can't get it going one way or the other - eventually - without the need for additional drivers or 25 digit authorisation codes for driver downloads and installs!

[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") so it's a bit like comparing apples with oranges. ;)

---

### Post by Autodave on 2017-07-24
Does your turntable have a ceramic or magnetic cartridge in it? (I am assuming this is not a USB turntable.) Non-amplified? (Again, I will assume non-amplified.) If ceramic, you need to input it into the microphone input. If it is a magnetic cartridge, you will not be able to hear it because a magnetic cartridge's output is extremely low. You will have to get a low level amplifier for your turntable and then probably use the LINE IN or maybe still the MIC IN.

---

### Post by rramesh2 on 2017-07-24
You will need something that does RIIA equalization. It can be done in software, I believe, but hardware units will also add gain to the signal and make it line level. There are several on amazon that you should be able to pick up for small money. In fact you might find USB versions that will make recording/listening a  simple task. 

Ramesh

---

### Post by cdavila on 2017-07-24
Thanks for the responses. My goal is to digitize a collection of vinyl LPs. I have an audio-technica AT-LP120-USB turntable. Being able to monitor the audio facilitates adding track labels during the actual recording on Audacity. I can record with the USB feature (cannot monitor audio either). Initially, I was able to record from Line 0 of the  Intel HDA PCH (name of my soundcard according to Ubuntu), but was also not able to monitor the audio. I chose to sample the analog signal with the soundcard since I get higher resolution (32-bit floating point versus 16-bit PCM for USB). This gives me extra bits in case I need to do post-processing. The turntable has a built-in preamplifier which can be turned on or off. Stylus is ATN95E (magnetic) and I have been using the preamp. I thought it might have been the soundcard driver that Ubuntu uses, my soundcard is an integrated Realtek High Definition Audio using an ALC 1220 codec. But I understand that my current Linux kernel supports this codec. Also installed Ubuntu 17.04 on another drive and got similar results.

---

### Post by cdavila on 2017-07-24
"When you are playing music from the turntable  via Audacity, look in PAVContol. In playback, is there a section for  Audacity and anything bouncing up and down on the level meter?"

Yes and Yes.

"If it is a regular, standard USB device, there should be no reason we  can't get it going one way or the other - eventually - without the need  for additional drivers or 25 digit authorisation codes for driver  downloads and installs!"

I get that...but on very elemental level, I** *should*** be able to plug an audio cable into the Line-input of my soundcard, regardless of whether or not I am recording, and be able to hear audio on my speakers.

---

### Post by Autodave on 2017-07-25
Without trying to record, are you saying that you cannot hear what the turntable is playing? What program are you running to try and hear the music?

As I said before, you may have to plug that into the microphone input: some preamps on magnetic cartridge turntables only "pre-amp" the signal to that of a ceramic cartridge's output which is about the same as a ordinary microphone.

---

### Post by Bucky Ball on 2017-07-25
> **cdavila said:**
> "When you are playing music from the turntable  via Audacity, look in PAVContol. In playback, is there a section for  Audacity and anything bouncing up and down on the level meter?"

Yes and Yes.

In that case, it could be presumed that all is working as it should with the record player signal getting into the machine and that can be put aside while you look for why you are not getting sound out. The turntable is working fine and getting signal to Ubuntu.

In PAVControl, are you sure you are using the correct port for output? Under the 'Output Devices' tab, you should see the level meter bouncing. In the dropdown list above that section (Built in Audio Analogue Stereo), next to 'Port device', are you sure you have the right output device set there?

Go to the 'Playback' tab and check the audio stream there. To the right, just above the stream, have you got it set to the correct device there?

---

### Post by cariboo on 2017-07-25
I've had success using an old stereo amplifier with a builtin pre-amp for turntables. I used the Tape out connectors on the amplifier to line in on my sound card, and if I remember correctly, audacity to do the recording.

---

### Post by Autodave on 2017-07-25
Are you trying to p[lay the sound through Audacity? There is an option there to listen to what you are recording. However, you need a duplex sound card for that. I looked online, but could find little info about your sound card. A lot of sound cards are not capable of handling an incoming signal and an out-going stream at the same time.

Go into the sound settings and then into configuration. Under Built In Audio, does it have the option of *Analog Stereo Duplex?  *If so, try choosing that. If it does not have that option, then probably your sound card is not a duplex card.

---

### Post by cdavila on 2017-07-25
> **Autodave said:**
> Are you trying to p[lay the sound through Audacity? There is an option there to listen to what you are recording. However, you need a duplex sound card for that. I looked online, but could find little info about your sound card. A lot of sound cards are not capable of handling an incoming signal and an out-going stream at the same time.

Go into the sound settings and then into configuration. Under Built In Audio, does it have the option of *Analog Stereo Duplex?  *If so, try choosing that. If it does not have that option, then probably your sound card is not a duplex card.

Yes, it is a duplex soundcard, very common on Gigabyte and similar motherboards ([http://www.realtek.com.tw/default.aspx](http://www.realtek.com.tw/default.aspx)). Today I installed a Ubuntu update and now appear to have a setting that works. Will post later.

---

### Post by Bucky Ball on 2017-07-26
Good news. As I mentioned, sometimes it takes a little (or a lot of!) tweaking to get things just so. Once you're there you'll know how it's done on your system and easier next time. Once you get it set up right it may just default to your settings next time you use the turntable anyhow. ;)

Keep us updated.

---

### Post by cdavila on 2017-07-26
....(later) using the same settings as last night, I am not able to  reproduce the results of last night. I have noticed the sound system  state is not very stable. Rebooting can change things even when Audacity  and Pulseaudio volume control settings are the same. Am throwing in the  towel for now.

---

