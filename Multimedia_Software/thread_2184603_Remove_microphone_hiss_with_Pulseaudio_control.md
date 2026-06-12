---
title: "Remove microphone hiss with Pulseaudio control?"
date: 2013-10-29
forum: Multimedia Software
---

### Post by Adam_GUI on 2013-10-29
This isn't a problem as much as it's just a general inquiry.

_xubuntu 12.04._
_Pulseaudio 1.1._
PCAudio shows up as Front Microphone - 
I think it's HDIntel Audio as my input.  
I honestly forget and can't find the output in pavucontrol.

_Description_:
I have a four-channel mixing board.  XENYX 802.
In Channel 1 - I have a cheapish RadioShack microphone into a XLR mono -> 1/4 plug.
The Gain Pot is set to the Nine O'clock position.

Muting the channel entirely with no audio playing and recording still results in a hiss.

Channel 2 - Empty.
Channel 3 - PC Audio-In.  (Stereo.)
Channel 4 - AUX Audio. (RCA Switchbox.  Stereo.)

There's an output to a set of PC speakers and a loopback into my PC Microphone port.
So, it's likely this isn't even a Pulseaudio thing, but something I have to get better input for.

I open Audacity and can play music from my system and get stereo recording of what I'm playing just fine.  
No noticeable hiss.  Same with AUX Audio.  This could just be the problem having "refuge in audacity", in that the hiss is drowned from the loopback recording noise.  There's so much going on that the hiss is negligible.

During a skype call my contact complained about a hiss ocean.

In Audacity, I hear a slight hiss (normal for a cheapish microphone) in recording.  Not a ground-hum; just a light hiss.
It sounds a lot like an old cassette lead to me;  
Like where the tape has no audio to play back and just gives a quite white noise.

During a skype test call, the playback sounds crystal clear.

Playing with my gain setting really doesn't seem to change what level hiss I get.

Is there a pulseaudio setting I can use to try to auto-hiss correct?

I need the solution to be live, not after-effected.  
I won't be offended if the best course is a hardware solution and not a software solution.  
That's why there's a mixing board to begin with.

I'm not sure what I'm doing different, other than it being an input bug outside the system that I can't seem to do much with.
Would a mini-jack condenser extension in at the system mini-jack connector help?
Or, would that be working the wrong end of the horse?

---

### Post by tgalati4 on 2013-10-29
Generally you need to pay attention to the quality of your transducers--microphones and speakers.  Cheap ones will sound like crap.

You can mask some of the effects of cheap transducers by using quiet preamps and mixers and lowering the microphone gain but raising the mixing/output gain.  However, you lose dynamic range.

Expensive microphones going into expensive preamps (as part of an expensive mixer) going into an expensive sound card will generally give good results.  Anything else will give you noise.

You keep spending money until you can't tell the difference.  There are lots of equipment reviews for PC recording equipment.

---

### Post by Adam_GUI on 2014-02-03
Marking this issue as solved.
The lesson learned, is that Radio Shack XLR -> Quarter Inch Jack adapters are, largely, junk.

The Mirophone is working well.  I know it's still a low grade Radio Shack microphone.  But, it's working.
The fix was to swap out the cable for an XLR -> XLR cable.
My audio-in has never sounded better.

Sorry for the necro-bump.  I felt it was necessary as a solution-post.

---

