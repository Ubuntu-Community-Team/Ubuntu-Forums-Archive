---
title: "Tuxguitar lag and sound problems"
date: 2013-04-05
forum: Multimedia Software
---

### Post by kerryhall on 2013-04-05
Hello,

I'm running timidity with a soundfont with tuxguitar. Even without timidity or the soundfont, I get terrible lag. Tuxguitar is unable to keep a steady beat. I have compared with a metronome. Obviously, for music software this is problematic...

I have tried tux guitar on three different systems, and they all experience this issue, including systems with the real time kernel installed. 

Any ideas? Is this just another case of java not working for real time applications? (ie, it's deciding to garbage collect right when I don't want it to?)

vlc works great, no lag. I have not noticed any issues with any other sound producing applications on my system. 

If this requires a source code fix, I would potentially be interested in making a donation to you for your time if you can make this fix.

---

### Post by vandalheart on 2013-04-07
I had the same problem with TG. Especially while trying to create my own tabs, it kindof did the job but during editing it lagged awfully especially as the song got longer. this became unbearable at times, and I nearly resorted to piracy ( I still run windows for various reasons)

Not too sure what version its on now, nor do I have much understanding of the program, I do recall having issues with Java or some such component ( got no sound) and had to install the relevant component to get sound, with the results I described.

I dont think VLC can be compared to TG, as it is very streamlined and (mostly) just plays audio and video. TG edits and interprets several file formats, and by nature is a rather bulky piece of software due to the amount of variables it has to account for.  in a nutshell, clumsy.

Another logical argument would be this coupled with the fact that ubuntu itself is not what most machines were designed for, and while buntu adapts to the various hardwares etc. they are becoming more varied and specialized. TG was probably designed to run on a wide range of machines, and by default will likely rely on a single core to execute its actions one by one. is your CPU a multicore? I will try find out if TG is capable of runnning multiple cores.

---

### Post by kerryhall on 2013-04-20
My CPU is multicore. Don't worry about the number of variables, for instance, a game like OpenArena has plenty of variables to keep track of, yet can render and display a frame every 8 milliseconds. I'm afraid that the problem here is probably java related, as java is a memory hogging, garbage collecting behemoth. :/ The problem is that garbage collection is non-deterministic, and can cause lag in real time applications. 

Anyone have any ideas here?

---

### Post by kerryhall on 2013-04-20
I must have been wrong! (Although I do dislike java's memory usage and allocation issues haha)

I fixed both the lag and the phase issues by doing a:

sudo apt-get install qsynth fluidsynth

then running qsynth, and selecting the alsa driver, and selecting the fluidr3_gm soundfont. Finally, select the "Synth input port" as the midi port in tuxguitar. Sounds awesome now!!! No lag! I've been banging my head against this issue for years now, honestly, years haha. (qsynth must be running while tuxguitar is running as well, or possibly just fluidsynth is needed)

Holy crap, I just realized this solves one additional problem as well, I was unable to listen to audio with any other program while tuxguitar is running. Solved now!!

---

