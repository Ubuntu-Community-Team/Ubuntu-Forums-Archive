---
title: "[SOLVED] Help playing MIDI's ins Rosegarden"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by carlinuxlearner on 2008-01-30
All I want to do is play MIDI files in Rosegarden, and right now it only kinda works, the sound is EXTREMELY Choppy, and I believe it is using Timidity.
I just want some one to tell me the easiest way of doing it, I do not have a MIDI sound card so I have to use a synthesizer of some kind. I believe I need to install a low latency kernel but I don't know how this is done. So any help will be greatly appreciated.

C@RL

---

### Post by Bruce H. McCosar on 2008-01-30
Actually, Rosegarden is the reason I switched to Ubuntu / KDE.

I'm not sure about your system or soundcard, but I tried manually compiling and configuring a low latency kernel for about a month.  I got some ok results, but never anything great.

That was with Debian.

On investigation, I found out about Ubuntu Studio.  I always have spare hard drive partitions to try out new systems and new tricks (sort of a test bed area, just in case things go wrong), so I installed:

1. Ubuntu 7.10, then

2. After initial configuration, loaded the modules listed here to transform to ubuntu-studio:

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)

Notice this includes a new package called linux-rt.  That's your realtime kernel, already made up, packaged, and ready to go for multimedia apps.

After being aggravated with trying to configure my own, it was great to have this download and run perfectly.  Audio in/out and MIDI are a snap.

At least for me.  I know from my experience in trying to configure my own version of a low latency kernel there are a lot of options.  Probably I'm benefiting from have an old and not particularly fancy computer -- a vanilla box, if you will -- and the generic options work fine for me with rt.

Now the second thing you need to get going, other than linux-rt, is JACK.  Rosegarden works very well with jack in realtime mode.

And the third thing ... probably Qsynth (a GUI for fluidsynth).  Timidity++ is sort of sketchy with Jack and Rosegarden.  I've never had it work reliably.  On the other hand Qsynth works incredibly well, as do other JACK aware synths like Aeolus (a pipe organ emulator).

Without knowing more, I can't make any better recommendations, but I hope this at least points you in the right direction.  It can be done.  I'm having a blast playing pipe organ every night, thanks to Ubuntu --- certainly less expensive than building my own cathedral :D

---

### Post by carlinuxlearner on 2008-01-30
Well thanks for the reply, I got a real time kernel installed, but I think I need to restate my problem now. Rosegarden is now using Qsynth, and this sound font "PC51f.sf2" but the MIDI play back is still horrible! It's all Crackly and choppy, and sound horrendous so any ideas what I'm doing wrong?

C@RL

Could it be my computer? It's certainly not very good (PIII 1.3GHz, 256MB RAM, 20GB HD)

---

### Post by Bruce H. McCosar on 2008-01-31
> **carlinuxlearner said:**
> Could it be my computer? It's certainly not very good (PIII 1.3GHz, 256MB RAM, 20GB HD)

Well, let's say if the problem were possibly one of three things -- your computer, alien invasion, or O.J. Simpson -- your computer is looking like a pretty strong suspect.  I thought *my* setup wasn't very good . . .

```
Linux bermuda-depths 2.6.22-14-rt #1 SMP PREEMPT RT Tue Dec 18 10:01:34 UTC 2007
One AMD Unknown 2079MHz processor, 4160.78 total bogomips, 447M RAM
System library 2.6.1
```

. . . but everything works reliably, with the same setup you've described.  If you use JACK, you can open the status box and see the actual latency.  Mine is generally very low (below 1 ms), which tells me magic has happened, because even when I was custom compiling my Debian kernel I never got below 100 ms.

I wonder what the minimum system requirement is?  I know RAM is usually the culprit, not CPU speed.  I believe you can test the theory several ways:

1. Try another path for MIDI playback.  Timidity does this well by itself, without Rosegarden.

2. Try a non-soundfont solution.  See if you can get it to work with a softsynth -- something with less of a memory footprint.  PC51 is a big soundfont.  I mean, I've got a pipe organ soundfont that's extremely thorough, but only 1/3 the size.

3. Go to the commandline and run 'top' to see who's hogging all the CPU time and memory.  You may be able to cut back by reducing desktop special effects (the GNOME stuff in 7.10 was dragging my system down, so I cut it to minimum.  Then I switched over to KDE, and there was no problem).

Just my guesses.  Let me know, and I'll see if I can toss a few more out there.

--BMC

---

### Post by carlinuxlearner on 2008-02-01
Well thanks I believe I discovered the problem, timidity++ was running when I started up my computer, so then I would start Qsynth, and I had TWO synthesizers running at the same time! So I stopped Timidity and now it all sounds fine! (I didn't use Timidity because it seamed to be a real CPU hog, and if you did anything else while it was playing it would skip and get all choppy) Also the reason I want to play MIDI's in Rosegarden is because I want to write them, so I want to write, and then listen, then fix, then listen, then write, and so on and so forth. But hey thanks! I never knew about that "top" command, that helps a lot.

C@RL

---

### Post by Bruce H. McCosar on 2008-02-01
> **carlinuxlearner said:**
>  (I didn't use Timidity because it seamed to be a real CPU hog, and if you did anything else while it was playing it would skip and get all choppy).

Timidity++ gets installed on the system and automatically loads as a daemon at start up.  You can disable it by editing /etc/default/timidity -- the line in question looks like this:

```
# Enable MIDI sequencer (ALSA), default is enabled
# Disable it if you have real MIDI hardware
TIM_ALSASEQ=true
```

However, you can also tune Timidity in it's config file to use less of the CPU.  You can find the config file at /etc/timidity/timidity.cfg

I used to use Lilypond by itself a lot, before Rosegarden.  I would make midi files as a sanity check if I was transcribing something with complicated rhythms (most of my music, actually ;-D )  Timidity had the advantage of being able to 'compile' even huge MIDI files to wav files -- not rendering them in realtime, but taking the MIDI and writing it directly to .wav.  I specifically say .wav because the .ogg and .flac versions were a bit wonky -- better to generate the .wav and then flac it yourself.

So I wouldn't give up on it.  Agreed, though, qsynth works a lot better with Rosie and JACK.

---

### Post by carlinuxlearner on 2008-02-02
Ahh... Well I also just realized that if what you say is true (and I believe it is), I had TWO instances of Timidity running at the same time! Because when I was trying to get it to work I would run Timidity through the terminal.
I now Have Timidity running with Rosegarden, and it all works fine (no crackles), BUT I have this song I just made, and it has two "Music box" tracks. With Qsynth and that sound font loaded (the PC51f.sf2) it plays just fine, but when I use Timidity there is NO sound, unless I change the tracks to a Piano. So is it possible to load a sound font in Timidity? And if so HOW! I tried searching the web for it, but I've had no luck so far. 
I have heard that Timidity can convert from MIDI to WAV, and that would be great, IF I can load Sound fonts in it.

Thanks for all the help
C@RL

---

### Post by carlinuxlearner on 2008-02-02
Hey never mind I figured it out. Here the links to the sites I found it at. 
[http://yoten.blogspot.com/2007/07/convert-midi-to-wav.html](http://yoten.blogspot.com/2007/07/convert-midi-to-wav.html)
[http://mandrivausers.org/index.php?showtopic=29329](http://mandrivausers.org/index.php?showtopic=29329)

C@RL

---

### Post by Bruce H. McCosar on 2008-02-02
> **carlinuxlearner said:**
> Hey never mind I figured it out. Here the links to the sites I found it at. 
[http://yoten.blogspot.com/2007/07/convert-midi-to-wav.html](http://yoten.blogspot.com/2007/07/convert-midi-to-wav.html)
[http://mandrivausers.org/index.php?showtopic=29329](http://mandrivausers.org/index.php?showtopic=29329)

C@RL

Good going!  And thanks for posting the links here in case someone else searches for the same info later.

Timidity and JACK have some sort of communication issue most of the time, at least with the Gutsy version of JACK.  I've heard that the problem is fixed in the newest version of JACK.  Problem is, for me, I've got everything working right now, and I really don't want to buy trouble by compiling my own version . . . I'll just wait for the Ubuntu package :D

I'm past the point of wanting to tweak everything and optimize to kingdom come . . . I'd rather spend my time making music.  So I hope your project succeeds.  Let me know how your music turns out; I'm recording my 4th album right now (it will be posted to Jamendo like my other three).  

If you think Rosegarden is neat, try Hydrogen -- I used it today to beta together a rhythm track and test out a layered composition I'm working on (bass, piano, nord lead 2x, violin, trumpet).  Fastest I've ever got a track together.

Then, of course, I have to admit that the combo Aeolus / Rosegarden takes up a lot of my time here lately . . . never thought I'd find myself arranging tunes for the pipe organ in my spare time!  What can I say, two steps forward, three steps back :D

---

