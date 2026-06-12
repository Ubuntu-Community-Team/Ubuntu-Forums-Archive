---
title: "USB MIDI controller not working"
date: 2012-06-02
forum: Multimedia Software
---

### Post by TheNEScollector on 2012-06-02
Yesterday I bought a FirstAct USB MIDI controller, but I can't seem to get it to work. All I want to be able to do is use my new keyboard with MuseScore. But that is proving difficult. I have Jackd and Qjackctl both installed but it doesn't seem to work. When I try to start it, it gives me an error saying this:

 ```
p, li { white-space: pre-wrap; }  [COLOR=#999999]13:20:21.006 Patchbay deactivated.[/COLOR]
[COLOR=#999999]13:20:21.009 Statistics reset.[/COLOR]
[COLOR=#cccc99]13:20:21.017 ALSA connection change.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
[COLOR=#66cc99]13:20:21.099 ALSA connection graph change.[/COLOR]
[COLOR=#999999]13:20:23.308 JACK is starting...[/COLOR]
[COLOR=#990099]13:20:23.308 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
[COLOR=#999999]13:20:23.351 JACK was started with PID=3121.[/COLOR]
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver ICH4 running on card 0 - Intel ICH5 with AD1980 at irq 17
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
[COLOR=#999999]13:20:23.574 JACK was stopped with exit status=255.[/COLOR]
[COLOR=#ff0000]13:20:25.384 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```I just can't figure it out. I also know MuseScore requires you to have the MIDI controller be Jack MIDI, but my controller appears under ALSA in QjackCtl. I read online that I need to "bridge" them with  the command "a2jmidid -e", but that gives me this error:

```
JACK MIDI <-> ALSA sequencer MIDI bridge, version 7 (b169fb6b8e9e11ce1488d1964649aabedbb89ddf) built on Wed Dec 31 19:00:00 1969
Copyright 2006,2007 Dmitry S. Baikov
Copyright 2007,2008,2009,2011 Nedko Arnaudov

Bridge starting...
Using JACK server 'default'
Hardware ports will be exported.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
ERROR: a2j_jack_client_create: Cannot create jack client
ERROR: a2j_start: a2j_new() failed.
```I'm really at a loss here. I'm generally pretty good with GNU/Linux, but audio stuff (especially MIDI) is pretty new to me. Thank you so much for any tips you may have for me!

---

### Post by TheNEScollector on 2012-06-03
I've tried running jack as root, but it doesn't make a difference. I've also tried to close all other applications before running jack but it still gives me the same error. Please help! Thanks!

---

### Post by TheNEScollector on 2012-06-05
Bump...

---

### Post by TheNEScollector on 2012-06-13
bump

---

### Post by JayPeeJay on 2012-06-17
Try closing all running sound applications before starting Jack.  When you start Jack, does it actually start running, or just open the program?  You can tell because the "start" button will be pressed.  Jack is very picky about your settings and will not run if they are not correct.

It shouldn't matter that your USB Controller appears under the Alsa tab and not the midi tab as long as you have "alsa sequencer support" checked under the misc tab.  None of my midi devices appear in the midi tab, they are always in the alsa tab and they work.  The fact that it appears at all is good news and means it is recognized.  You now need only connect it to Musescore in the connections tab.

If all the above is going as it should, then it is just a matter of making sure your settings within MuseScore are correct (you track has midi enabled, on the same channel as your controller, etc...).  If you hadn't been using Jack before you got the controller, you probably need to change  the settings in MuseScore to let it know that you are now using Jack, both for audio and midi.

---

### Post by TheNEScollector on 2012-06-17
Jack still won't start... I even rebooted my machine and started Jack before anything else and it still won"t start. It only opens the program, and if I try to start it, it just gives me the same error as before. Any ideas?

---

### Post by TheNEScollector on 2012-06-17
I don't think you meant to post that...

---

### Post by JayPeeJay on 2012-06-23
I am by no means an expert, but since no one else is replying...

Try increasing the priority to 89, 10 seems low.  If that doesn't work try un-checking realtime.  Here are my settings:

---

### Post by BicyclerBoy on 2012-06-23
The midi kernel driver support is in alsa..

With the USB midi interface plugged in..
In a terminal (<ctrl>+<alt>+<T>) run:

alsa -l

With midi instrument connected:
alsa -d
If this returns nothing you might be of of luck..

If success with the above:
You can monitor the midi commands with KMidimon.

---

### Post by TheNEScollector on 2012-07-05
Well, after giving up all hope about a week ago, I reformatted my hard drive and installed Arch Linux. I was planning on doing this anyway, I did not wipe everything just for the keyboard. But the keyboard works now. I have no idea what the issue was, but it works just fine. :)

---

