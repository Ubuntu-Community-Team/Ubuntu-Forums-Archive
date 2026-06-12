---
title: "Audio Recording/mixing/sequencing software suggestions?"
date: 2007-06-13
forum: Multimedia Production
---

### Post by Saxomophone on 2007-06-13
I'm new to Linux, and don't know much about the available sound software. I do a decent amount of audio recording, and have used sound studio, deck, and garage band while at college. Part of my impetus for beginning linux use was the availability of good multimedia software. I've installed cinelerra for video editing purposes, but I have no idea where to begin for sound editing.

So what I'm looking for is what people think are the best software options for doing sound recording and editing, and why.

Thanks!!!

---

### Post by eric71 on 2007-06-14
The main contender for audio production is Ardour.  It is a very good multitrack DAW. The only thing it lacks compared to its Windows and Mac cousins is MIDI sequencing, which it will have in the future. If you use a lot of MIDI, then Rosegarden is your best choice.  It is a KDE based program. It does audio sequencing as well, but not anywhere near the capabilities of Ardour. Because both programs use the Jack sound server, they can interconnect, link their timing, etc.  There is also another useful program, Jamin, for mastering purposes that works well via Jack with Ardour and Rosegarden. Linux doesn't have great support for VST effects right now, but it is improving.  Ardour has some ways to get it done, and Rosegarden can do it via its DSSI plugin system.  Native Linux LADSPA and DSSI effects and instruments I think are better than they get credit for, and you can usually get pretty much the same thing done as with VSTs. Everything (except some proprietory things needed for VST suppiort) is available in the standard Ubuntu repositories.

[www.ardour.org](www.ardour.org)
[www.rosegardenmusic.com](www.rosegardenmusic.com)
jamin.sourceforge.net

---

### Post by NeoLithium on 2007-06-14
There's a good list of programs and options available at [http://www.linux-sound.org](http://www.linux-sound.org) or you can also take a peek at Ubuntu Studio: [http://www.ubuntustudio.org](http://www.ubuntustudio.org)

Hope this helps! :)

---

### Post by Saxomophone on 2007-06-14
Thank you both. That was very helpful.

---

### Post by niglch on 2007-06-14
I use a combination of these packages:
A) Audacity - At this point in time, I think it is the best software around for the sole purpose of editing and recording audio files. It's fairly simple once you get the hang of it, and it does a pretty good job of whatever you need it. You can download from the Ubuntu repositories, but a .deb installer of the new beta version (1.3.2) is available at getdeb.org which integrates much better into the GNOME desktop environment.
B) UbuntuStudio LADSPA Plugins - Once installed, these work in Audacity many other audio editing programs. It is a collection of nearly 300 effects.
C) Rosegarden - A MIDI sequencer with many features. You can also mix the MIDI sequences with audio files. It can export to various formats including Lilypond (below).
D) Lilypond - This program is basically meant to generate the best musical score output possible. Probably what you want to use if you need to print sheet music or export it to a PDF fiile.
E) Fluidsynth - This is a SoftSynth program needed only if you don't have a soundcard that handles MIDI input and output on it's own. You also need to install a soundfont (search the forums for more info on this). Timidity is another option, but I heard Fluidsynth has better performance and output.
F ) JACK - I'm still not sure what it does exactly, but a lot of programs seem to use it for audio output. I'm not sure if I'm explaining it correctly, but I think the advantage is that it allows multiple connections to whatever audio back-end you're using (ALSA, OSS, etc) and basically brings all the audio programs you are using together. For example, output errors are common if you do not tell Audacity to use it [Edit => Preferences => Device] and other audio programs are running. Note that JACK will not appear if it is not running.
G) JACK Control - A lot of people seem to be scared of installing JACK because seems complicated to first time users (mostly because there's no GUI). This graphical front-end makes usage of JACK a bit easier (even if it's just starting and stopping it).
H) Qsynth - A GUI for Fluidsynth. Very useful considering I haven't even been able to get fluidsynth to start up from the command-line yet.  It also makes installing soundfonts easier (you can just browse for SF2 files).
Some other stuff:
A) Ardour - I heard it's really good, but it unfortunately confuses me right now. I also think it is much more useful if you are doing hard disk recording, but right now I'm using a separate multi tracker and transfer audio to my computer after it's recorded.
B) Low-latency kernels - You might run into the need for this if you are using Rosegarden or Ardour. UbuntuStudio comes with it preloaded, but it would require you to install a separate distro. However, you might be able to compile a low-latency kernel for a normal Ubuntu install (I currently need to figure this out as I'm having some trouble getting Rosegarden to not run out of processing power).

I hope this helped. Time to go study for some exams . . .

---

