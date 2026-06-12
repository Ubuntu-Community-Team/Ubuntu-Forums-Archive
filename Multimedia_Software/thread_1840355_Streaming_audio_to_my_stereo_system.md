---
title: "Streaming audio to my stereo system"
date: 2011-09-07
forum: Multimedia Software
---

### Post by serpicojam on 2011-09-07
I want to stream audio to my home stereo, and I know I can do this using PulseAudio. What I do not know, however, is the hardware I need that I will be sending the audio stream to (that will be hooked up to my stereo receiver). 
 
I do NOT want to use AirPort Express. There has to be a clear, pain-free choice at this stage of the game, right? 
 
Thanks!

---

### Post by serpicojam on 2011-09-19
Any help or suggestions will be appreciated. I want to know I can make the transition from OS X to ubuntu. Streaming audio to the stereo system is a big part of our everyday lives. Thanks.

---

### Post by oldos2er on 2011-09-19
Moved to Multimedia & Video.

I have a cable from Line Out on my soundcard to my receiver's Aux input. Not sure if that's the solution you're looking for.

---

### Post by Bucky Ball on 2011-09-19
> **oldos2er said:**
> I have a cable from Line Out on my soundcard to my receiver's Aux input. Not sure if that's the solution you're looking for.

Yep, did that for awhile, too. Then we got a media player which connects directly to the router which means we can now stream audio/video straight to the tv/sound system via the network from any computer in the house (there are four) instead of just the one hardwired to the amp with an audio cable. 

Just depends on what hardware you already have and how you've been doing it already as to what is the best way to go. Tell us what you have and how you've been going about doing it with OSX.

---

### Post by serpicojam on 2011-09-22
We send audio from the Mac/iTunes wirelessly to an AirPort Express module, which connects to the stereo via a stereo connection kit. Been this way since '08.
 
Thanks so much for your assistance/feedback.

---

### Post by papibe on 2011-09-22
If your stereo doesn't have the ability the receive and play a stream of music, then you need a device connect to it that either receive/decode the stream, or simply play the music.

I have an old Pentium III laptop with a wireless pcmcia card connected to my stereo. Since this device is 'smart', I don't stream the music. I shared it using nfs on my home server, and I mounted the partition on the laptop.

Is that what are looking for?
Regards.

---

### Post by serpicojam on 2011-09-23
A bridge router should do the trick, and there are many options. I'm concerned however that PulseAudio won't see it, or that configuring it will turn out to be a science project. I was hoping somebody could suggest one that worked fairly well for them.

---

### Post by serpicojam on 2011-09-27
Anybody out there have success with a bridge router? If so, which one?

---

### Post by aeiah on 2011-09-27
just send a broadcast to your airport express i guess.

from here: [http://www.hersson.net/technotes/stream-audio-from-any-application-to-your-airportexpress](http://www.hersson.net/technotes/stream-audio-from-any-application-to-your-airportexpress)

> 5. Go to System->Preferences->PulseAudio Preferences. Under Network Access select both “Make discoverable network sound devices available locally”, and “Make discoverable Apple Airtunes sound devices available locally”. Press Close


i made myself a stream receiver by loading openwrt onto a router that has a usb port (and plugged a soundcard into the usb port). works great for the bathroom powered by batteries. since you've already got an airport express, it might not be worth the hassle though.

---

### Post by serpicojam on 2011-09-28
Unfortunately, the "Make discoverable Apple AirTunes sound devices locally" option via PulseAudio preferences is grayed out and unavailable for me. I don't know why.
 
Argh!
 
Any suggestions?

---

### Post by quista on 2012-05-12
the following will enable that option:

aptitude install pulseaudio-module-raop

---

