---
title: "Jack boot problem with &quot;Integrated&quot; card"
date: 2023-12-23
forum: Multimedia Software
---

### Post by manucontrovento on 2023-12-23
Hi all, 
let me premise that I have been using applications that work with Jack for years and have used them on different notebooks and with different models of sound cards connected, without problems or at least solving them easily.
I recently changed notebooks, now I have an HP TPN C126 AMD. For the first time I can't use Jack (it goes error right at startup!) with the integrated card, which I sometimes have to do.

At startup in fact a messagebox says:
- operation failed
- unable to connect to JACK server

and then in the "message" window it's all this:


[COLOR=#000080]13:51:11.487 Reset stats.
13:51:11.505 ALSA connections changed.
Cannot connect to server socket err = File o directory non esistente
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
13:51:11.543 Change in ALSA connections.
13:51:36.866 JACK is starting...
13:51:36.866 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2
Cannot connect to server socket err = File o directory non found
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
13:51:36.886 JACK è stato avviato con PID=6275.
no message buffer overruns
no message buffer overruns
no message buffer overruns
jackdmp 1.9.20
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2016 Grame.
Copyright 2016-2021 Filipe Coelho.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
self-connect-mode is "Don't restrict self connect requests"
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Released audio card Audio0
audio_reservation_finish
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
13:51:37.174 JACK has been arrested
13:51:39.103 I couldn't start JACK as client. - Operation failed. 
Cannot connect to server socket err = File o directory non found
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
[/COLOR]

I remain waiting for ideas... obviously I have already tried to change various parameters in jack configuration without concluding anything, before writing in the forum...
and i would add that the problem arises precisely only with the pc integrated card, in fact if i connect external sound cards and configure jack to use them, everything works normally.

And happy holidays to all.

---

### Post by manucontrovento on 2023-12-28
Hi everyone!!
some days passed from my thread.. any idea?
Thanks!

---

