---
title: "avconv/ffmpeg audio quality when grabbing multiple audio sources..."
date: 2013-08-24
forum: Multimedia Software
---

### Post by gargl on 2013-08-24
Hi everyone.

I've just managed, after a couple days of work (and only 'somehow' *g),
to be able to grab more than one audio source and save it into one file.

To make things more concrete:
source 1: webcam microphone (plughw:2,0)
source 2: 'what you hear' (soundcard, pulse)

What I do is:
avconv -f alsa -ac 2 -i pulse -f alsa -ac 1 -i plughw:2,0  -map 0:0 -map 1:0 out.wav

where the '-map' option is responsible that both sources are grabbed and saved to the same
output file, which in this case is out.wav (without the '-map' command, only the first source
is considered).
In principle everything works (because both audio sources are overlayed and saved in out.wav),
however the audio quality is _really_ bad. I would describe the sound as 'metallic' and 'distorted'.

However if I record only one source at a time (e.g. plughw:2,0 OR pulse) the recording quality is flawless.
Interestingly, if I alter the audio settings (in the two sources scenario) for example saving the audio as
mp3 instead of wav (e.g. -c:a libmp3lame -q:a 4), the quality drops so drastically that one can not even
understand what was recorded originally.

Any help would be greatly appreciated because I do not know where to start (I've first
though that mb the '-map' option could cause the problem, but recording one source
WITH the 'map' option lead to flawless results).
Thanks a lot in advance if you know an advice or mb even the solution! :)

---

### Post by FakeOutdoorsman on 2013-08-24
The next recommended step is to see if a recent build works as expected. See the [FFmpeg download](http://ffmpeg.org/download.html) page for Linux builds (I'm not sure if they support ALSA input device), or follow a [ffmpeg compile guide](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

Also, you should always include the complete console outputs with your command(s) and use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code).

---

### Post by gargl on 2013-08-25
Ah ok, so sorry for being sloppy and not entirely correct with the title of my post.
I accidentially termed it 'avconv/ffmpeg' assuming that both are the same according
to some crossreading in the forum. However, the written command in my first
post clearly does not work when replacing
'avconv'
with
'ffmpeg'.

That means that instead focussing on a solution with avconv
I was also able to search one using ffmpeg in which I had
a certain clue how to do it. Because for me it seems what
is the '-map' option in avconv seems to be an equivalent to the '-filter_complex'
or '-lavfi' option from ffmpeg (see: [http://ffmpeg.org/ffmpeg.html#Complex-filtergraphs](http://ffmpeg.org/ffmpeg.html#Complex-filtergraphs)).

However, executing ffmpeg with either one of the arguments
('-filter_complex' or '-lavfi') leds in both cases to:
```

#$ Unrecognized option 'lavfi'/'-filter_complex'
#$ Failed to set value 'out.wav' for option 'lavfi'

```

Following the advice from FakeOutdoorsman I wanted to install the
newest ffmpeg version.
However, to make a long story short, following:
[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)
and the output of
```

ffmpeg 2>&1 | head -n1
#$ ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 **the Libav developers**

```
I am (as well as probably many others) using a 'fake' ffmpeg.
Described here:
[http://stackoverflow.com/questions/9477115/who-can-tell-me-the-difference-and-relation-between-ffmpeg-libav-and-avconv/9477756#9477756](http://stackoverflow.com/questions/9477115/who-can-tell-me-the-difference-and-relation-between-ffmpeg-libav-and-avconv/9477756#9477756)
which now confuses me heavily on what to acutally update.
For example do I break my avconv if I install the 'original'
ffmpeg libraries? Do they work at all?
Mhm...mb I just do some further research and then give it a try...

---

### Post by gargl on 2013-08-25
Ok, I've just give it a try.
Thank you FakeOutdoorsman for the link to the excellent how-to on how to compile ffmepg
as it allowed me to creat a 'real' ffmpeg environment.

```

$ ffmpeg 2>&1 | head -n1
ffmpeg version git-2013-08-25-626739e Copyright (c) 2000-2013 the FFmpeg developers

```

There is one thing I want to point out which extremely lighten me the decision
to either try to install 'ffmpeg' or not. At the end of the how-to there is 
explained how to remove anything that was just installed. That enabled me to
choose easily and to just give it a try because it would empower me to just undo
what I did before. Therefore a big respect for the whole guide, their maintainers
and the explanation on how to undo what was just done.

The only downpart of the how-to is that my home folder now contains several folders
which normally belong in other folders like '/usr'. However, this is ok for me considering
the advanced capability I now have.

Because now I can grab and record two audio sources and map them into one output
file on the fly. which was my original concern.

Command goes here:
```

ffmpeg -f alsa -ac 2 -i pulse -f alsa -ac 1 -i plughw:2,0 -filter_complex amix=inputs=2 out.wav

```

I think you can certainly adjust and add further arguments for refinment but for me its
sufficient atm as it just works without any distortion or strange audible artifacts (see
first post).

So far, thanks for all the work done by the different maintainers and programmers and also
of course thank you FakeOutdoorsman as you gave me an important impulse in order to
continue and pursue my goal and continue the work I have done so far.

For all others also struggling of setting up audio and get it running to do some screencasting
or desktoprecording or whatever, keep on trying and have same patience to achieve the goal.
Sometimes it is really difficult but finally it should work! gl!

---

### Post by FakeOutdoorsman on 2013-08-26
> **gargl said:**
> Because for me it seems what
is the '-map' option in avconv seems to be an equivalent to the '-filter_complex'
or '-lavfi' option from ffmpeg (see: [http://ffmpeg.org/ffmpeg.html#Complex-filtergraphs](http://ffmpeg.org/ffmpeg.html#Complex-filtergraphs)).

I don't use avconv, so I can't really comment on it's implementation of the same named options.

> **gargl said:**
> However, executing ffmpeg with either one of the arguments
('-filter_complex' or '-lavfi') leds in both cases to:
```

#$ Unrecognized option 'lavfi'/'-filter_complex'
#$ Failed to set value 'out.wav' for option 'lavfi'

```

The "-filter_complex" option is used to create [complex filtergraphs](http://ffmpeg.org/ffmpeg-filters.html#Filtergraph-syntax-1) (basically using a filter or filters with one or more inputs or outputs). I believe "-lavfi" is an alias for "-filter_complex".

> **gargl said:**
> For example do I break my avconv if I install the 'original'
ffmpeg libraries?

No. Compiling and installing ffmpeg as shown in the guide will not interfere with the libav package (and its tools avconv, and its libraries, etc) from the repo. This is because the guide does not perform a "system" installation, but  a "local" installation to your $HOME so the system and package management system are not interfered with. The only thing that can occur, as far as I know, is that if a package from the repo uses the so-called "ffmpeg" binary from the repo it may use the ffmpeg you compiled instead (and this would only affect your user if you have multiple user accounts on your computer). Maybe WinFF does this? I wouldn't worry about it.

> **gargl said:**
> 
The only downpart of the how-to is that my home folder now contains several folders
which normally belong in other folders like '/usr'. However, this is ok for me considering
the advanced capability I now have.

Everything should have gone into one of three directories in your home:
[list]
[*]**ffmpeg_sources**: where all of the downloaded source files went
[*]**ffmpeg_build**: where some of the compiled files are "installed"
[*]**bin**: where the resulting binaries are placed
[/list]

Undoing everything just removes the two "~/ffmpeg_*" directories, removes the relevant contents of the "~/bin" directory, and uninstalls the dependencies used for compiling.

> **gargl said:**
> atm as it just works without any distortion or strange audible artifacts (see
first post).


Good to hear you found a solution, although the [amerge audio filter](http://ffmpeg.org/ffmpeg-filters.html#amerge) is usually recommended over amix, but unfortunately I can not remember why.

---

