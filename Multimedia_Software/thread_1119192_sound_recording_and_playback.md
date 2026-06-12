---
title: "sound recording and playback"
date: 2009-04-07
forum: Multimedia Software
---

### Post by teh-walrus on 2009-04-07
Hi,

Not sure if this is the right forum but thought i'd give it a wack:

I am trying to investigate ways of interfacing an mdm Zinc 3.0 flash projector application with sound recording and playback in Linux, specifically interested in ubuntu. I have a couple of questions for the techies:

1) Is ALSA support built into the standard ubuntu kernel that you would find on any old standard install of ubuntu or edbuntu?

2) Is there a much easier way of calling a local system app which will record and play back files in a simple format (e.g. WAV) on the ALSA 0 device?

I am happy to consider running "sysexec" commands (which would hopefully run a terminal command like 
$ builtinrecordingapp --record --file="file1.wav"
) or writing some sort of interface application (although this would be more complicated as I would obviously have to provide an "approved" .deb installer for users, which would be more fuss for me to build and them to install).

Looking forward to people's ideas, and thanks in advance,

Joe

---

