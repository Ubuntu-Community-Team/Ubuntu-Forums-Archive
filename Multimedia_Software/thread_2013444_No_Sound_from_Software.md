---
title: "No Sound from Software"
date: 2012-06-30
forum: Multimedia Software
---

### Post by Tk007LwZFJW5ej on 2012-06-30
I have downloaded some software called tiny ear trainer from the repository. It does not play any sounds at all. Sound works fine for all other applications. I left a message at the developer's website, but I doubt I will hear back soon, if at all. I just want to know if there is anything obviously wrong that I may be able to fix myself from the command line output:

Connection failure: Connection refused 
starting fluidsynth 
loading  soundfont /usr/share/sounds/sf2/TimGM6mb.sf2 selecting program Cannot  connect to server socket err = No such file or directory 
Cannot connect to server socket 
jackdmp 1.9.7 
Copyright 2001-2005 Paul Davis and others. 
Copyright 2004-2011 Grame. 
jackdmp comes with ABSOLUTELY NO WARRANTY 
This is free software, and you are welcome to redistribute it under certain conditions; see the file COPYING for details 
no message buffer overruns 
no message buffer overruns 
JACK server starting in realtime mode with priority 10 
control device hw:0 
control device hw:0 
audio_reservation_init 
Acquire audio card Audio0 
creating  alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit  control device hw:0 configuring for 44100Hz, period = 1024 frames (23.2  ms), buffer = 2 periods ALSA: final selected sample format for capture:  32bit integer little-endian ALSA: use 2 periods for capture ALSA: final  selected sample format for playback: 32bit integer little-endian ALSA:  use 2 periods for playback 
When I click Play in study mode, I get a bunch of lines like playing (some number) 
for each tone played, then the following when I shut it down: 
deleting fluidsynth 
playing 60 
JackTemporaryException : now quits... 
jack main caught signal 2 
control device hw:0 
Released audio card Audio0 
audio_reservation_finish 
control device hw:0 

This is the additional output after I exit:

deleting fluidsynth
JackTemporaryException : now quits...
jack main caught signal 2
control device hw:0
Released audio card Audio0
audio_reservation_finish
control device hw:0

There isn't much info on the website, but here's the address: 
[http://29a.ch/tinyeartrainer/](http://29a.ch/tinyeartrainer/)

I have ubuntu 11.10 x64.

---

