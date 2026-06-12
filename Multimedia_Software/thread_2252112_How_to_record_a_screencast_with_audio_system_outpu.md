---
title: "How to record a screencast with audio system output, preferably JACK?"
date: 2014-11-09
forum: Multimedia Software
---

### Post by dewdrop_world on 2014-11-09
Main question: I need to record a screencast and capture audio from JACK, **not** from pulseaudio.

Problem: JACK input into recordmydesktop is broken in the version of RMD in the Ubuntu repositories. It seems that including --use-jack in the commandline options causes the commandline parser to introduce random numbers into some options, which produces a "Window size specification out of bounds" error. The bug is apparently not important enough to be fixed promptly, despite the availability of a patch.

[https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188)

Also note that I don't need microphone input. I want to capture sound from my audio software.

So then I investigated capturing the system's audio output from ALSA.

[http://recordmydesktop.sourceforge.net/rug/p1_2c.php:](http://recordmydesktop.sourceforge.net/rug/p1_2c.php:)

> In most cases, you will probably want the microphone and/or the mix/wave sources enabled. However, recordMyDesktop, does not offer a mixer interface to configure your sound card. This has to be performed in an external program like kmix, gnome-mixer or alsamixer(ncurses based interface). For more information, refer to the documentation of these tools.

This might be fine for the built-in soundcard, but I'm using a USB audio interface, and alsamixer doesn't know how to configure that. So there is a possibility that RMD might not be useful to me at all.

I also had a look at kx11grab. Just a single text box for the audio device, and I can't find any help online for that. Guesswork is... uncomfortable.

So... where do I go from here? I guess RMD with no audio and try to get the audio another way. That's a pity.

hjh

---

### Post by dewdrop_world on 2014-11-09
FWIW, I did eventually get acceptable results by:


[LIST]
[*]Recording video only (no audio) with kx11grab;
[*]Recording audio directly from the audio software, into a separate file;
[*]Merging them using PiTiVi. I started the video recording before the audio, so that the instruction to start recording would be visible and I could use that kind of like a clapboard in movie production.
[/LIST]

Problems along the way:


[LIST]
[*]RecordMyDesktop is not usable for live-coding screencasts because (at least on my machine) it doesn't show anything for the line of text that you're typing until you hit return and move to the next line. The whole point with live coding is to see the action of typing. At least kx11grab could handle that.
[*]kx11grab produces avi files, but avidemux can't open them. I like avidemux for combining video with a different audio track because it's lighter-weight than a full nonlinear editor, and often you can get away without transcoding. Avidemux has been able to open just about anything I throw at it, except... this.
[/LIST]

Anyway, thought it would be easy... it wasn't. So I hesitate to call it "Solved." I got what I wanted, but had to fly to Tasmania and back for that jar of peanut butter.

hjh

---

### Post by FakeOutdoorsman on 2014-11-10
I have very little JACK experience, but here's what I would try:

1. [Compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu). In addition to these instructions, before you compile ffmpeg, you'll need **libjack-dev** or **libjack-jackd2-dev** as an ffmpeg dependency (either provides what ffmpeg needs, AFAIK). I don't know what the difference is between these packages and didn't look it up. Maybe some fork shenanigans.

2. Capture screen as shown in [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719) and audio as shown in [FFmpeg JACK input device documentation](http://ffmpeg.org/ffmpeg-devices.html#jack). You can do both with one ffmpeg command if you prefer.

---

