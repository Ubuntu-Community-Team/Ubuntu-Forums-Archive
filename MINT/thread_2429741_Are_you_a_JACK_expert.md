---
title: "Are you a JACK expert?"
date: 2019-10-22
forum: MINT
---

### Post by Londrioca on 2019-10-22
Linux Mint 17.3/Ubuntu 14.04
jack, jackd, QjackCtl, Qsynth installed.
ASUS laptop

I've been an Ubuntu/Mint user for several years and long ago gave up on Jack, could never get it to work. Today I tried again with this result:  In QjackCtl/Setup/Interface when I click on the arrow there are 4 options : default; hd:HDMI; hd:Generic; hd:Generic,0  If I select either of the first two Jack won't open ("Could not connect to jack server as client"). If I select either of the other two it opens but when I click Start there's no sound. I've Googled till my eyes glazed over but although the world & his wife seem to have had similar problems with Jack nothing I've tried works. Usually with these things it's simple when you know how so I'm hoping someone will show me how to resolve this in a few seconds! 
Log shows this:

```
[COLOR=#999999]20:52:06.122 Patchbay deactivated.[/COLOR]
[COLOR=#999999]20:52:06.123 Statistics reset.[/COLOR]
[COLOR=#cccc99]20:52:06.152 ALSA connection change.[/COLOR]
[COLOR=#999999]20:52:06.173 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#66cc99]20:52:06.187 ALSA connection graph change.[/COLOR]
(qjackctl:5001): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:5001): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:5001): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:5001): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[COLOR=#999999]20:52:39.605 JACK is starting...[/COLOR]
[COLOR=#990099]20:52:39.606 /usr/bin/jackd -t200 -dalsa -dhw:0 -r44100 -p128 -n2[/COLOR]
[COLOR=#990099]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#990099]Cannot connect to server request channel[/COLOR]
[COLOR=#990099]jack server is not running or cannot be started[/COLOR]
[COLOR=#990099](qjackctl:5001): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
[COLOR=#990099](qjackctl:5001): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
[COLOR=#999999]20:52:39.650 JACK was started with PID=5025.[/COLOR]
[COLOR=#999999]jackdmp 1.9.10[/COLOR]
[COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
[COLOR=#999999]Copyright 2004-2013 Grame.[/COLOR]
[COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
[COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
[COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
[COLOR=#999999]JACK server starting in realtime mode with priority 10[/COLOR]
[COLOR=#999999]audio_reservation_init[/COLOR]
[COLOR=#999999]Acquire audio card Audio0[/COLOR]
[COLOR=#999999]creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
[COLOR=#999999]ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[/COLOR]
[COLOR=#999999]Cannot initialize driver[/COLOR]
[COLOR=#999999]JackServer::Open failed with -1[/COLOR]
[COLOR=#999999]Failed to open server[/COLOR]
[COLOR=#999999]20:52:39.815 JACK was stopped with exit status=255.[/COLOR]
[COLOR=#ff0000]20:52:41.657 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
[COLOR=#ff0000]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#ff0000]Cannot connect to server request channel[/COLOR]
[COLOR=#FF0000]jack server is not running or cannot be started[/COLOR]
```

---

### Post by uRock on 2019-10-22
I am not sure about Mint's support for that version, but 14.04 is no longer supported.

---

### Post by coffeecat on 2019-10-22
*Thread moved to **Mint** sub-forum*

Both Mint 17.3 and Ubuntu 14.04 are now well past end-of-life, and are obsolete releases. You would be better advised to install a currently supported operating system before trying to troubleshoot jack problems.

**Edit:** Note - simultaneous staff action.

---

### Post by Londrioca on 2019-10-23
Upgraded to 18.3, Jack still doesn't like default or hd:HDMI but anything else starts Jack & has sound, but connections tab is virtually empty in Audio, MIDI, & ALSA, so as a Jack noob I have no idea how to proceed.

---

