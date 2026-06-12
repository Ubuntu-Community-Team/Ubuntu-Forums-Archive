---
title: "Qsynth artefacts"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by jOrganist on 2007-04-01
Hi guys

Until very recently I have been running jOrgan under Windows XP using 'sfz' as the soundfont player.  As a complete 'newbie' to Linux I am rather chuffed that I have been able to get jOrgan up and running with Ubuntu 6.10 (and all without having to do command line stuf!!!) and I am really impressed by the possibilities offered by Qjackctl and Qsynth.  For example, I can run four instances of Qsynth, and identify and use 8 separate mono outputs from my Audigy 2ZS soundcard - stuff that I couldn't do in Windows with sfz and Creative Labs' drivers.  
However, I am less impressed by the quality of Qsynth's soundfont rendering (not to mention the fact that Qsynth's reverb doesn't seem to work).  In particular I notice problems with the top two octaves of (say) the Principal 4' and the top three octaves of (say) the Fifteenth 2' stops.  When I hold down certain notes I get a periodic "tinging" sound, very similar to the "clicks" that you get if you haven't made good loops with Zero-X.  But I've checked the loops and they are are OK - and in any case, I don't get the same problem if I play back the same soundfonts with sfz.
Is this a characteristic of Qsynth-Fluidsynth, or am I doing something wrong?  The fact that everything seems to work - and goes on working without error messages or crashing after five minutes (as happened with Suse/JackLab) encourages me to think I am not a million miles off course.  BTW, I am running Qsynth version 0.2.4.  I tried to update to the Feisty-Fawn version but couldn't do it.  I also tried to find help on the Sourceforge site, but learning Linux is easier than negotiating the SourceForge maze.

Graham

---

### Post by Maxxarcade on 2007-04-01
Hi Graham, 

What kind of sound card are you using?  I'm not having that problem, but I am having a strange problem with the mixer that I posted about earlier.  In fact I think Qsynth sounds better than the onboard Live card synth.

I'm using two SB Live cards on a Duron 1300 with 256MB ram.  Each card has it's own Qsynth engine.  I do get some clicking/popping noises when sending a lot of MIDI data, but I think it is the slow computer and lack of RAM doing that.  The reverb sounds great as well.  I turned off the chorus though.

---

### Post by jOrganist on 2007-04-01
Hi Aaron

I think we met somewhere before   ;) 
As I indicated in my post, I am using a Creative Audigy 2ZS card.
I can't help with your mixer problem, since I now have only one soundcard installed.  But when I had two, and for a while three, SBLive! soundcards installed, under Windows XP, I ran into similar problems.
Re your clicking/popping noises - this may well be due to lack of RAM and CPU power.  However, when I first got going in Ubuntu, I configured Qsynth's audio driver as ALSA, and I got crackling whenever there was graphics activity such as swell LED's operating, or when I displayed Qsynth's channels window whilst playing, or even if I moved the mouse pointer across the console.  Now I have Qsynth's audio driver set as JACK the crackling has completely gone.

Graham

---

### Post by Maxxarcade on 2007-04-01
Hmm, Last time I set the audio output to JACK, it stuttered really bad.  Maybe the computer is just too slow.  I would just upgrade it, but I need to get the console working properly before any more goes into the computer :) 

Have you tried re-installing fluidsynth? Since the reverb doesn't work either, I'd say something is up with Fluidsynth or Qsynth.

Also, how is your latency when playing?  I have the buffers set a bit high to avoid dropouts, and it causes a delay between pressing a key and hearing the note.  Probably another thing that can be cured with a faster computer...

---

### Post by jOrganist on 2007-04-02
Yes - I tried re-installing Fluidsynth with Synaptic, but it didn't make any difference.  Maybe I need to try doing a full un-install followed by a fresh install.

Re stuttering and latency etc. - Assuming you have enough RAM and a reasonable CPU, I think it's all tied up with this Real Time hocus-pocus.  During my abortive attempt with SuSe/JackLab I came across this:
[http://wiki.jacklab.net/index.php/Assigning_real-time_priorities_with_PAM](http://wiki.jacklab.net/index.php/Assigning_real-time_priorities_with_PAM)

So when I got Ubuntu running, I edited the  etc/security/limits.conf  file by adding the following:

@audio		-	rtprio		90
@audio		-	nice		-15
@audio		-	memlock		4000000

and I put me in an audio group - I think this lets me use realtime as an ordinary user - I must confess it's all a deep mystery to me!

In Qjackctl settings I set:

Server Path - jackd
Driver - alsa

Parameters - check Realtime
Priority -  76
Frames/Period - 1024 (this was default)
Sample rate - 48000 (Audigy card runs at this)
Periods/Buffer - 2 (default)
Port Maximum - 128 (default)
Timeout (msec) - 500 (default)

Interface - hw:0  (=Audigy soundcard)
Dither - none (default)
Audio - Playback only (I am not wanting to record)
Output channels - 16 (So I can access 8 mono audio outputs from my Audigy card)
Output latency - 0 (default)
Start Delay (sec) - 2 (default)

Latency - 42.7 msec (governed by Frames/Period)

In Qsynth my MIDI driver is alsa-seq, and my audio driver is jack.

My CPU is a Pentium 4  3GHz and I have 2 GB RAM.

With this set up I can draw a lot of stops - my soundfonts total about 700 MB and they are shared between four instances of Qsynth - and I don't get any pops or glitches.  As for latency - well, I am not conscious of any delay between pressing the keys and hearing the sound.  Generally it's all good except for the way Qsynth seems to render the loop portion of higher pitched soundfonts - and the reverb doesn't work!

---

