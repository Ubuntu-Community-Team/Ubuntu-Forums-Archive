---
title: "Audio over HDMI - Volume control?"
date: 2009-01-29
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2009-01-29
Question for you HDMI gurus:

Do either the Master volume control or PCM volume control affect the hdmi audio?  Basically, should I be able to control the hdmi volume using alsamixer or the volume control in mythtv?

---

### Post by Dewey_Oxberger on 2009-01-29
With alsa 1.0.19 and NVidias latest HDMI is now a reality for mythtv!

Any of you have volume control of the hdmi through mythtv?

---

### Post by dakota34 on 2009-01-30
Dewey, are you actually getting audio and video over your hdmi? is it a 9300 or 9400? I'm trying to assemble hardware for a new mythtv pc, and what with the minute-by-minute developments with VDPAU it's hard to see which way to go hardware-wise, but if you have hdmi working for both then it seems like the way to go..:D


John

---

### Post by Dewey_Oxberger on 2009-01-30
I have audio and video working over hdmi.  The alsa and nvidia elves have been hard at work packing loads of coolness into every byte.  ;)

My set up is: Abit AN-M2 series motherboard with NVidia 7050pv chipset, alsa 1.0.19, and nvidia 180.22 manually installed on Mythbuntu 8.10 with all the mythtv-fixes applied from the weekly builds.

I have no asound.conf or $HOME/.asoundrc file.  I just set mythtv to used ALSA:hdmi as the audio device and it works.  I will need to add a plughw to get other sample rates working (i.e. cd and mp3 playback but that'll be no big deal).

The only downside is the volume stream is fixed at full volume (mythtv can't control the volume).  I have to used the tv remote to control the volume.  That seems so... low tech...

I'll tinker with a softvol setup this weekend and see what I can get.

I was just hoping this was some config error that I could find and fix...

Anybody know if volume should work?

---

### Post by Dewey_Oxberger on 2009-01-31
As of alsa 1.0.19 there does not seem to be a volume control for audio over hdmi.  Still, alsa is one cool pile of code and it allows you to create your own audio over hdmi volume control.

Here is my first cut at using softvol to control the volume.  It looks like it works just fine.  Let me know if it works for you.

Down load it, save it in your home directory, and follow the instructions in it.

---

### Post by freakalad on 2009-02-14
Managed to get my audio to work over HDMI from my ATI Radeon HD 3450 to my Sony Bravia LCD TV (setting under the ALSA mixer).
There doesn't seem to be volume control, but this doesn't bother me too much, since I can control volume via the TV (remote control)

---

### Post by Dewey_Oxberger on 2009-03-11
From what I'm reading in the hdmi spec it seems that the PC should be able to send volume control commands to the tv through the hdmi link.  That would be cool.

Anybody know how to make it work?

---

### Post by Maheriano on 2009-03-11
Why would you think you can control a digital signal with an analogue controller? That doesn't make any sense. Volume control is analogue meaning it has degrees of intensity without getting too far into it. Digital is either on or off, there are no levels. So you can't control your sound through software without converting the signal first. You're better off firing it out to your player (I use my home theatre receiver) and using its volume controller to manage it from there.

---

### Post by nickrout on 2009-03-11
> **Maheriano said:**
> Why would you think you can control a digital signal with an analogue controller? That doesn't make any sense. Volume control is analogue meaning it has degrees of intensity without getting too far into it. Digital is either on or off, there are no levels. So you can't control your sound through software without converting the signal first. You're better off firing it out to your player (I use my home theatre receiver) and using its volume controller to manage it from there.

Agreed, the whole point of digital audio is to NOT have alsa screw with it, but to pump it straight to the decoder (in your tv or amplifier). To control the volume alsa needs to decode and re-encode the digital signal. It reportedly does a bad job. The Hollywood studio spent a lot of time on that 5.1 soundtrack and you don't want alsa screwing it about. Whats wrong with the tv/amplifier's volume control?

---

### Post by Dewey_Oxberger on 2009-03-20
Such a diversity of understanding here.  Maybe throwing more words at this will be a little more clear:

Your HDMI cable consists of several wires arranged as twisted pair sets.  We can talk about the "digital" signals being sent over those twisted pair sets.  We can talk about how those signals work together to form a bi-directional data link between the devices at each end.  But all this would be way too low a level to talk about volume control.  Those signals are tightly controlled by a standard and we don't want to mess with them.

We can talk about how the bi-directional link is built to carry a fairly hefty load of digital information from a source to an output device.  While carrying not such a big load in the reverse direction.  We can talk about error correction codes, compression and such.  Again still to low a level.

What I care about is ultimately there is a sequence of numbers, a "digital representation" of an audio signal.  I want to create a volume control that allows me to scale those numbers.  The volume control is created by taking each one of those numbers in the digital representation and multiplying them by a scale factor that I choose.  The factor can be any number from 0.0 to... oh, say about 2.0.

There are two common ways to implement that "volume multiplier stage."  Do it directly to the digital audio stream, or do it just after the digital audio gets converted back to an analog signal.

There is a bit of difference between those two approaches.  It should be better to apply the volume multiplier after going to analog.  I assume that is what you both are thinking.

Still, the difference in audio quality between the two approaches is so small I can't hear it.  I've tried.  My Samsung TV has very quiet analog amps.  My room is quiet.

That said, HDMI allows the source to send volume control commands directly to the output device.  The output device can then use whatever best approach it has to adjusting the volume.  That is how you really want to do it but it doesn't appear to be supported yet (and may never be supported for all I know).

So, since I like the idea of the computer controlling the volume I offered up this softvol control approach.

---

### Post by Alcareru on 2009-04-10
I was just wondering this very same thing. Is there any such amplifier(s) on the market that one could control with ones computer. I know powering up and shutting down is possible, but the volume (and possibly bass) control (and why not also other settings) is the thing I was wondering.

And to you ppl saying: "What's wrong with the amps (remote) volume control?"
I say, if just in any way possible I don't want to ever touch the frigging amps remote nor it's front panel. In fact after doing the initial installation (plugging the wires and going though sound settings) I don't even want to see either one. I want to hide the ugly box somewhere out of sight and I want to be able to use 1 single remote control and I want to use it to command my computer and let the computer command other hardware as is needed.

P.S. I'm considering to buy an amplifier and I want to make sure my hardware choices do not close the possibility for this feature.

---

### Post by nickrout on 2009-04-10
> **Alcareru said:**
> I was just wondering this very same thing. Is there any such amplifier(s) on the market that one could control with ones computer. I know powering up and shutting down is possible, but the volume (and possibly bass) control (and why not also other settings) is the thing I was wondering.

And to you ppl saying: "What's wrong with the amps (remote) volume control?"
I say, if just in any way possible I don't want to ever touch the frigging amps remote nor it's front panel. In fact after doing the initial installation (plugging the wires and going though sound settings) I don't even want to see either one. I want to hide the ugly box somewhere out of sight and I want to be able to use 1 single remote control and I want to use it to command my computer and let the computer command other hardware as is needed.

P.S. I'm considering to buy an amplifier and I want to make sure my hardware choices do not close the possibility for this feature.

Well you can of course use an ir blaster to control anything that is controllable by infrared.

I am sure that there must be amplifiers that are more specifically computer controllable, like via USB or serial.

Also the volume buttons on my MCE remote can be programmed from another remote, so they are programmed to control my amplifier rather than the computer, not quite what you want but it does the trick for me. I do still have to have the amplifier remote handy for other functions (switching inputs etc).

---

### Post by Alcareru on 2009-04-11
> **nickrout said:**
> Well you can of course use an ir blaster to control anything that is controllable by infrared.
I figured that should be possible, but I quickly abandoned the idea as a bad one. Then again as I gave it a bit more thought I believe it should do the trick. Yeah. Actually it might even be better, cos it doesn't restrict me to control only HDMI connected hardware.

> **nickrout said:**
> I am sure that there must be amplifiers that are more specifically computer controllable, like via USB or serial.
Well that's what I thought.. haven't found any such things as of so far, but perhaps I've just been unlucky.

---

### Post by silo100 on 2010-01-30
Just to add to the discussion, XBMC can control the volume over HDMI on my acer revo..
If only myth could...
and the modified asound doesn't seem to work either, getting

2010-01-30 08:16:53.746 mixer unable to find control Master 1
2010-01-30 08:16:53.752 NVP(0): Enabling Audio
2010-01-30 08:17:01.627 mixer set channel 0 err -1: Operation not permitted

Argh!!  Forget it.. It works fine..  My bad, not in the audio group :redface:

---

### Post by nickrout on 2010-01-30
> **silo100 said:**
> Just to add to the discussion, XBMC can control the volume over HDMI on my acer revo..
If only myth could...
and the modified asound doesn't seem to work either, getting

2010-01-30 08:16:53.746 mixer unable to find control Master 1
2010-01-30 08:16:53.752 NVP(0): Enabling Audio
2010-01-30 08:17:01.627 mixer set channel 0 err -1: Operation not permitted

Argh!!  Forget it.. It works fine..  My bad, not in the audio group :redface:

controlling spdif volume in software can only be done by altering the digital stream, which kinda defeats the purpose of a digital stream.

---

### Post by Dewey_Oxberger on 2010-02-01
> **nickrout said:**
> controlling spdif volume in software can only be done by altering the digital stream, which kinda defeats the purpose of a digital stream.

How so?  Are you worried about loss of sound quality?

---

### Post by nickrout on 2010-02-01
> **Dewey_Oxberger said:**
> How so?  Are you worried about loss of sound quality?

most definitely. take a dts stream and muck with it and its no longer what the film producer intended.

---

### Post by Dewey_Oxberger on 2010-02-01
> **nickrout said:**
> ...and its no longer what the film producer intended.

It's not longer profitable?  LOL.

---

### Post by nickrout on 2010-02-01
> **Dewey_Oxberger said:**
> It's not longer profitable?  LOL.

LOL very good.

The fact is that alsa does a crap job of resampling, your quality will be reduced.

Personally I have THX certified sound system and I'd prefer to put the original soundtrack into it, not some approximation. There is no difficulty adjusting the volume on the amp with the same remote as controls mythtv.

---

### Post by Dewey_Oxberger on 2010-02-02
> **nickrout said:**
> 
Personally I have THX certified sound system

Hey, you could do a little experiment.  Config your system so you are using the ALSA volume control.  Set it at 33% volume and set your THX coolness to 100%.  Then listen to some sounds.

Then change to no ALSA volume control, THX set at 33% and see how major the difference is.  Report what you hear.

How bad is it?

---

