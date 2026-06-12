---
title: "Tapioca: Can hear other party, but they can't hear me"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by Ma_USMC on 2006-06-06
I've worked out all my alsa issues and can record my voice through the mic fine using Sound Recorder, but for some odd reason a very low garbled static is transmitted to the other party instead of my voice.  Does anyone know if there is some sort of config'ing to be done in Tapioca to get this to work? It seems as though everything should be working fine, but I just can't transmit. Help is appreciated.

*Edit: Forgot to mention.  I'm running a SB Audigy 2ZS and Alsa-* 1.0.10.

---

### Post by Patsoe on 2006-06-09
As far as I can tell, there's no sound config needed in tapioca itself. The only thing the tapioca website has is [http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone](http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone) which basically just sets some general alsa stuff.

I'm trying to get it to work too, but right now I don't have sound travelling either way... :( 

I'm going to run it while watching the debug messages and see what comes out :) Will report back if I find anything interesting.

---

### Post by Bachstudies on 2006-06-23
Just wondered if you had any success on getting rid of the garbled static. I have the same issue - I can hear my friend very clearly but all they hear is broken up nonsense. Skype works absolutely fine so must be some dependency error or something.

Chris

---

### Post by Patsoe on 2006-06-23
Well, I have it working more or less now. The other party can hear me, but they say the quality is nowhere near what they hear when I use googletalk (on winxp). The sound coming my way is good quality...

I should add that I'm running a very up-to-date version of tapioca, the source taken from svn. 

(BTW, why I didn't have any sound before: the gstreamer plugins I compiled were invisible to gstreamer, so it just didn't load them.... wrong directory)

---

### Post by Ma_USMC on 2006-07-03
To update, I haven't tweaked with this in a while since I moved and the only internet I have is at work; thus, I'm still afflicted.  To be honest I was waiting for update version of this or even the Linux GTalk to be available before I began again.  

 I do want to note though, that when recording voice (muted the +20 amp to mic) it records very low volume.  I tested it with Exaile playing in the background and it was actually recording the sound output from the computer as well as input from the mic.

 This could spell a need for either new ALSA drivers or me to be de-noobified.

---

### Post by kendals on 2006-09-20
Any luck, people? I'm also getting crap sound sent to my Gtalk contacts in Tapioca, but they come through crystal-clear. Skype works great, so does Sound Recorder...latest of everything! :(

Where's Gtalk for Linux :(

---

