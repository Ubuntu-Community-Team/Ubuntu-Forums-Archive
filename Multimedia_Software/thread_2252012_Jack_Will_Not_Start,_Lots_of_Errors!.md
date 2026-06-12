---
title: "Jack Will Not Start, Lots of Errors!"
date: 2014-11-08
forum: Multimedia Software
---

### Post by geo8 on 2014-11-08
So I am trying to get into making music. I have an Acer C720 Chromebook which I used crouton to install Ubuntu 14.04 Trusty. So far it has been a great thing as I can run most things I need right off my Chromebook. Now, though, I have installed ALSA, jack, and Ardour version 3.5.403 on my system, along with qjackctl. I believe that I don't have multiple installs of Jack because I have removed it, purged it, autoremoved, and autocleaned many times. The first time I ran Ardour, it stated that "Could not reconnect to the Audio/MIDI engine" and "Could not create session in..." (wherever I tried to save the project). So I did some digging and came up with other people having the same problem but no real answers. When I try to start JACK in qjackctl, it somes with lots of errors and the messages tab looks like this:

```
[COLOR=#999999][FONT=Tinos]08:22:35.361 Patchbay deactivated.[/FONT][/COLOR][COLOR=#000000][FONT=Tinos][COLOR=#999999]08:22:35.373 Statistics reset.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos][COLOR=#ff0000]08:22:35.384 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos][COLOR=#999999]08:22:39.523 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos][COLOR=#ff0000]08:22:39.722 D-BUS: JACK server could not be started. Sorry[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Cannot connect to server socket err = No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Cannot connect to server request channel[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]jack server is not running or cannot be started[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Cannot connect to server socket err = No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Cannot connect to server request channel[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]jack server is not running or cannot be started[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: Starting jack server...[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: JACK server starting in realtime mode with priority 10[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: Acquired audio card Audio0[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: ERROR: Cannot initialize driver[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: ERROR: JackServer::Open failed with -1[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:39 2014: ERROR: Failed to open server[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Sat Nov 8 08:22:41 2014: Saving settings to "/home/epicurus/.config/jack/conf.xml" ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos][COLOR=#ff0000]08:22:43.872 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Cannot connect to server socket err = No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]Cannot connect to server request channel[/FONT][/COLOR]
[COLOR=#000000][FONT=Tinos]jack server is not running or cannot be started[/FONT][/COLOR]

```

Any help would be greatly appreciated!

---

### Post by geo8 on 2014-11-09
So, after many hours of searching, I finally found an article that was actually not on JACK, but on Ubuntu Studio. Since I can't figure out a way to download Ubuntu Studio on a Chromebook, I am stuck with the normal, where I am not set up with audio. BUT I finally found out that I can download the Ubuntu Studio package. So I did, and that basically solved ALL these problems! Yay!

---

