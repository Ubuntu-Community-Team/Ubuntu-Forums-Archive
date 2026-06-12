---
title: "qjackctl won't start, hugely annoyed"
date: 2011-09-05
forum: Multimedia Software
---

### Post by LouManChu on 2011-09-05
Sorry if that title rubs anyone the wrong way but ever since I decided to go Linux over Windows XP I have been non stop trying to fix things and conducting 0% productivity.  Besides the booting issue I still have where I get the GRUB screen and the options for 'generic' or 'recovery mode' and the 20 or so Esc key hits I have to make just to get the login screen, I am also having problems getting qjackctl to work.  Here's the following message I get about 5 seconds after starting qjackctl:

[B]Could not connect to JACK server as client.
-Overall operation failed.
-Unable to connect to server.
Please check the messages window for more info.
[/B]
here is the messages content:

Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
11:53:12.613 ALSA connection graph change.
11:53:17.911 JACK is starting...
11:53:17.911 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xraw
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
11:53:17.981 JACK was started with PID=1710.
11:53:17.989 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver EMU10K1 running on card 0 - SB Live! 5.1 (rev.10, serial:0x80641102) at 0xdd00, irq 18
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
scan: added port hw:0,0,0 in-hw-0-0-0-EMU10K1-MPU-401--UART-
scan: added port hw:0,0,0 out-hw-0-0-0-EMU10K1-MPU-401--UART-
scan: added port hw:0,1,0 in-hw-0-1-0-Emu10k1-Synth-MIDI
scan: added port hw:0,1,1 in-hw-0-1-1-Emu10k1-Synth-MIDI
scan: added port hw:0,1,2 in-hw-0-1-2-Emu10k1-Synth-MIDI
scan: added port hw:0,1,3 in-hw-0-1-3-Emu10k1-Synth-MIDI
scan: added port hw:0,1,4 in-hw-0-1-4-Emu10k1-Synth-MIDI
scan: added port hw:0,1,5 in-hw-0-1-5-Emu10k1-Synth-MIDI
scan: added port hw:0,1,6 in-hw-0-1-6-Emu10k1-Synth-MIDI
scan: added port hw:0,1,7 in-hw-0-1-7-Emu10k1-Synth-MIDI
scan: added port hw:0,1,8 in-hw-0-1-8-Emu10k1-Synth-MIDI
scan: added port hw:0,1,9 in-hw-0-1-9-Emu10k1-Synth-MIDI
scan: added port hw:0,1,10 in-hw-0-1-10-Emu10k1-Synth-MIDI
scan: added port hw:0,1,11 in-hw-0-1-11-Emu10k1-Synth-MIDI
scan: added port hw:0,1,12 in-hw-0-1-12-Emu10k1-Synth-MIDI
scan: added port hw:0,1,13 in-hw-0-1-13-Emu10k1-Synth-MIDI
scan: added port hw:0,1,14 in-hw-0-1-14-Emu10k1-Synth-MIDI
scan: added port hw:0,1,15 in-hw-0-1-15-Emu10k1-Synth-MIDI
scan: added port hw:0,1,0 out-hw-0-1-0-Emu10k1-Synth-MIDI
scan: added port hw:0,1,1 out-hw-0-1-1-Emu10k1-Synth-MIDI
scan: added port hw:0,1,2 out-hw-0-1-2-Emu10k1-Synth-MIDI
scan: added port hw:0,1,3 out-hw-0-1-3-Emu10k1-Synth-MIDI
scan: added port hw:0,1,4 out-hw-0-1-4-Emu10k1-Synth-MIDI
scan: added port hw:0,1,5 out-hw-0-1-5-Emu10k1-Synth-MIDI
scan: added port hw:0,1,6 out-hw-0-1-6-Emu10k1-Synth-MIDI
scan: added port hw:0,1,7 out-hw-0-1-7-Emu10k1-Synth-MIDI
scan: added port hw:0,1,8 out-hw-0-1-8-Emu10k1-Synth-MIDI
scan: added port hw:0,1,9 out-hw-0-1-9-Emu10k1-Synth-MIDI
scan: added port hw:0,1,10 out-hw-0-1-10-Emu10k1-Synth-MIDI
scan: added port hw:0,1,11 out-hw-0-1-11-Emu10k1-Synth-MIDI
scan: added port hw:0,1,12 out-hw-0-1-12-Emu10k1-Synth-MIDI
scan: added port hw:0,1,13 out-hw-0-1-13-Emu10k1-Synth-MIDI
scan: added port hw:0,1,14 out-hw-0-1-14-Emu10k1-Synth-MIDI
scan: added port hw:0,1,15 out-hw-0-1-15-Emu10k1-Synth-MIDI
scan: added port hw:0,2,0 in-hw-0-2-0-Emu10k1-Synth-MIDI
scan: added port hw:0,2,1 in-hw-0-2-1-Emu10k1-Synth-MIDI
scan: added port hw:0,2,2 in-hw-0-2-2-Emu10k1-Synth-MIDI
scan: added port hw:0,2,3 in-hw-0-2-3-Emu10k1-Synth-MIDI
scan: added port hw:0,2,4 in-hw-0-2-4-Emu10k1-Synth-MIDI
scan: added port hw:0,2,5 in-hw-0-2-5-Emu10k1-Synth-MIDI
scan: added port hw:0,2,6 in-hw-0-2-6-Emu10k1-Synth-MIDI
scan: added port hw:0,2,7 in-hw-0-2-7-Emu10k1-Synth-MIDI
scan: added port hw:0,2,8 in-hw-0-2-8-Emu10k1-Synth-MIDI
scan: added port hw:0,2,9 in-hw-0-2-9-Emu10k1-Synth-MIDI
scan: added port hw:0,2,10 in-hw-0-2-10-Emu10k1-Synth-MIDI
scan: added port hw:0,2,11 in-hw-0-2-11-Emu10k1-Synth-MIDI
scan: added port hw:0,2,12 in-hw-0-2-12-Emu10k1-Synth-MIDI
scan: added port hw:0,2,13 in-hw-0-2-13-Emu10k1-Synth-MIDI
scan: added port hw:0,2,14 in-hw-0-2-14-Emu10k1-Synth-MIDI
scan: added port hw:0,2,15 in-hw-0-2-15-Emu10k1-Synth-MIDI
scan: added port hw:0,2,0 out-hw-0-2-0-Emu10k1-Synth-MIDI
scan: added port hw:0,2,1 out-hw-0-2-1-Emu10k1-Synth-MIDI
scan: added port hw:0,2,2 out-hw-0-2-2-Emu10k1-Synth-MIDI
scan: added port hw:0,2,3 out-hw-0-2-3-Emu10k1-Synth-MIDI
scan: added port hw:0,2,4 out-hw-0-2-4-Emu10k1-Synth-MIDI
scan: added port hw:0,2,5 out-hw-0-2-5-Emu10k1-Synth-MIDI
scan: added port hw:0,2,6 out-hw-0-2-6-Emu10k1-Synth-MIDI
scan: added port hw:0,2,7 out-hw-0-2-7-Emu10k1-Synth-MIDI
scan: added port hw:0,2,8 out-hw-0-2-8-Emu10k1-Synth-MIDI
scan: added port hw:0,2,9 out-hw-0-2-9-Emu10k1-Synth-MIDI
scan: added port hw:0,2,10 out-hw-0-2-10-Emu10k1-Synth-MIDI
scan: added port hw:0,2,11 out-hw-0-2-11-Emu10k1-Synth-MIDI
scan: added port hw:0,2,12 out-hw-0-2-12-Emu10k1-Synth-MIDI
scan: added port hw:0,2,13 out-hw-0-2-13-Emu10k1-Synth-MIDI
scan: added port hw:0,2,14 out-hw-0-2-14-Emu10k1-Synth-MIDI
scan: added port hw:0,2,15 out-hw-0-2-15-Emu10k1-Synth-MIDI
scan: added port hw:1,0,0 in-hw-1-0-0-MPU-401-UART-MIDI
scan: added port hw:1,0,0 out-hw-1-0-0-MPU-401-UART-MIDI
scan: opened port hw:0,0,0 in-hw-0-0-0-EMU10K1-MPU-401--UART-
scan: opened port hw:0,0,0 out-hw-0-0-0-EMU10K1-MPU-401--UART-
scan: opened port hw:0,1,0 in-hw-0-1-0-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,1 in-hw-0-1-1-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,2 in-hw-0-1-2-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,3 in-hw-0-1-3-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,4 in-hw-0-1-4-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,5 in-hw-0-1-5-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,6 in-hw-0-1-6-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,7 in-hw-0-1-7-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,8 in-hw-0-1-8-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,9 in-hw-0-1-9-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,10 in-hw-0-1-10-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,11 in-hw-0-1-11-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,12 in-hw-0-1-12-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,13 in-hw-0-1-13-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,14 in-hw-0-1-14-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,15 in-hw-0-1-15-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,0 out-hw-0-1-0-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,1 out-hw-0-1-1-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,2 out-hw-0-1-2-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,3 out-hw-0-1-3-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,4 out-hw-0-1-4-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,5 out-hw-0-1-5-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,6 out-hw-0-1-6-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,7 out-hw-0-1-7-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,8 out-hw-0-1-8-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,9 out-hw-0-1-9-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,10 out-hw-0-1-10-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,11 out-hw-0-1-11-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,12 out-hw-0-1-12-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,13 out-hw-0-1-13-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,14 out-hw-0-1-14-Emu10k1-Synth-MIDI
scan: opened port hw:0,1,15 out-hw-0-1-15-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,0 in-hw-0-2-0-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,1 in-hw-0-2-1-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,2 in-hw-0-2-2-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,3 in-hw-0-2-3-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,4 in-hw-0-2-4-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,5 in-hw-0-2-5-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,6 in-hw-0-2-6-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,7 in-hw-0-2-7-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,8 in-hw-0-2-8-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,9 in-hw-0-2-9-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,10 in-hw-0-2-10-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,11 in-hw-0-2-11-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,12 in-hw-0-2-12-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,13 in-hw-0-2-13-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,14 in-hw-0-2-14-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,15 in-hw-0-2-15-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,0 out-hw-0-2-0-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,1 out-hw-0-2-1-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,2 out-hw-0-2-2-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,3 out-hw-0-2-3-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,4 out-hw-0-2-4-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,5 out-hw-0-2-5-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,6 out-hw-0-2-6-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,7 out-hw-0-2-7-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,8 out-hw-0-2-8-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,9 out-hw-0-2-9-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,10 out-hw-0-2-10-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,11 out-hw-0-2-11-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,12 out-hw-0-2-12-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,13 out-hw-0-2-13-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,14 out-hw-0-2-14-Emu10k1-Synth-MIDI
scan: opened port hw:0,2,15 out-hw-0-2-15-Emu10k1-Synth-MIDI
scan: opened port hw:1,0,0 in-hw-1-0-0-MPU-401-UART-MIDI
scan: opened port hw:1,0,0 out-hw-1-0-0-MPU-401-UART-MIDI
11:54:58.466 JACK is stopping...
jack main caught signal 15
scan: deleted port hw:0,0,0 in-hw-0-0-0-EMU10K1-MPU-401--UART-
scan: deleted port hw:0,0,0 out-hw-0-0-0-EMU10K1-MPU-401--UART-
scan: deleted port hw:0,1,0 in-hw-0-1-0-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,1 in-hw-0-1-1-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,2 in-hw-0-1-2-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,3 in-hw-0-1-3-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,4 in-hw-0-1-4-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,5 in-hw-0-1-5-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,6 in-hw-0-1-6-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,7 in-hw-0-1-7-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,8 in-hw-0-1-8-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,9 in-hw-0-1-9-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,10 in-hw-0-1-10-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,11 in-hw-0-1-11-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,12 in-hw-0-1-12-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,13 in-hw-0-1-13-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,14 in-hw-0-1-14-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,15 in-hw-0-1-15-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,0 out-hw-0-1-0-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,1 out-hw-0-1-1-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,2 out-hw-0-1-2-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,3 out-hw-0-1-3-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,4 out-hw-0-1-4-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,5 out-hw-0-1-5-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,6 out-hw-0-1-6-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,7 out-hw-0-1-7-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,8 out-hw-0-1-8-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,9 out-hw-0-1-9-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,10 out-hw-0-1-10-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,11 out-hw-0-1-11-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,12 out-hw-0-1-12-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,13 out-hw-0-1-13-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,14 out-hw-0-1-14-Emu10k1-Synth-MIDI
scan: deleted port hw:0,1,15 out-hw-0-1-15-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,0 in-hw-0-2-0-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,1 in-hw-0-2-1-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,2 in-hw-0-2-2-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,3 in-hw-0-2-3-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,4 in-hw-0-2-4-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,5 in-hw-0-2-5-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,6 in-hw-0-2-6-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,7 in-hw-0-2-7-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,8 in-hw-0-2-8-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,9 in-hw-0-2-9-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,10 in-hw-0-2-10-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,11 in-hw-0-2-11-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,12 in-hw-0-2-12-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,13 in-hw-0-2-13-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,14 in-hw-0-2-14-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,15 in-hw-0-2-15-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,0 out-hw-0-2-0-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,1 out-hw-0-2-1-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,2 out-hw-0-2-2-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,3 out-hw-0-2-3-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,4 out-hw-0-2-4-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,5 out-hw-0-2-5-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,6 out-hw-0-2-6-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,7 out-hw-0-2-7-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,8 out-hw-0-2-8-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,9 out-hw-0-2-9-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,10 out-hw-0-2-10-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,11 out-hw-0-2-11-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,12 out-hw-0-2-12-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,13 out-hw-0-2-13-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,14 out-hw-0-2-14-Emu10k1-Synth-MIDI
scan: deleted port hw:0,2,15 out-hw-0-2-15-Emu10k1-Synth-MIDI
scan: deleted port hw:1,0,0 in-hw-1-0-0-MPU-401-UART-MIDI
scan: deleted port hw:1,0,0 out-hw-1-0-0-MPU-401-UART-MIDI
control device hw:0
Released audio card Audio0
audio_reservation_finish
control device hw:0
11:55:00.461 JACK was stopped successfully.

True to its word, qjack stops and there is nothing in the way of connecting devices going on.  

I'm getting to the point where reinstalling Windows isn't sounding so difficult anymore, at least I had a working environment.  Now my family asks why I'm spending so much time in front of the computer.  Sorry, I'm just frustrated with this mess.  20 years ago I learned the ins and outs of DOS and was fascinated with its powerful, yet unforgiving, command line design but these days I just want a working computer so the work and the play gets done.

---

