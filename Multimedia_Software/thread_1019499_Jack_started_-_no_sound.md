---
title: "Jack started - no sound"
date: 2008-12-23
forum: Multimedia Software
---

### Post by gilli4 on 2008-12-23
Hi,

I'm running Ubuntu Studio 8.10 and I can't use Jack audio for applications like Ardour. The jack engine is able to start and Ardour can connect itself to it but I can't hear any sound being played back.
Other applications using ALSA or OSS work though. Only when I start jack, I can't hear the sound being played through it while Ardour assumes that everything is just right. The meters work, the playback progresses (visually) but I can't hear the sound.

My soundcard is an ALC268 and Jack did work with it when I was on Kubuntu Hardy.

I'd be glad about any help.

Thanks in advance and merry x-mas,

Gilzad

---

### Post by gilli4 on 2009-02-13
By now I could not solve the problem on my own. Am I the only one having this problem under Ubuntu Studio 8.10?

I'd still be glad about any advice.

---

### Post by neu2buntu on 2009-02-13
try starting both programs from the terminal by typing ```
qjackctl
``` and ```
ardour2
``` and paste the output of both terminals and also the messages in qjackctl,

---

### Post by Stochastic on 2009-02-14
better yet, could you post the output of qjackctl's message window as well as a screenshot of it's settings window?

---

### Post by gilli4 on 2009-02-14
Hi Neu2ubuntu and Stochastic and thanks for your help!

My output of qjackctl is:

```
gilzad@nt:~$ qjackctl
Warning: no locale found: /usr/share/locale/qjackctl_de_DE.qm

```

My output of the Jack messages is:
```
13:06:51.610 Patchbay deactivated.
13:06:51.816 Statistics reset.
13:06:51.848 ALSA connection graph change.
13:06:52.061 ALSA connection change.
```

The screen shot of my Jack's setup window looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103339&stc=1&d=1234613441[/IMG]

My output of ardour2 is:
```
gilzad@nt:~$ ardour2
WARNING: Your system has a limit for maximum amount of locked memory!
This might cause Ardour to run out of memory before your system runs out of memory. You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.conf
Ardour/GTK 2.5
   (kompiliert mit Version 3525 und GCC Version4.3.2)
Copyright (C) 1999-2008 Paul Davis
Einige Teile Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker
theme_init() called from internal clearlooks engine
lade voreingestellte UI-Konfigurationsdatei /etc/ardour2/ardour2_ui_default.conf
lade benutzerdefinierte UI-Konfigurationsdatei /home/gilzad/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
ardour: [INFO]: Ardour will be limited to 1024 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/gilzad/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /home/gilzad/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
ardour: [INFO]: Control surface protocol discovered: "Mackie"
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable

(ardour-2.5:7351): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(ardour-2.5:7351): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(ardour-2.5:7351): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(ardour-2.5:7351): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::cursor-color' of type `GdkColor' from rc file value "((GString*) 0x906aed0)" of type `GString'
JACK COMMAND: /usr/bin/jackd -p 128 -T -d alsa -n 2 -r 0 -p 1024 -d hw:0,0 
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 0
creating alsa driver ... hw:0,0|hw:0,0|1024|2|0|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 0Hz, period = 1024 frames (inf ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
loading bindings from /etc/ardour2/mnemonic-us.bindings
Loading session /home/gilzad/test using snapshot test (1)
unknown destination port in attempted connection [ardour:i_wanna_give_you_devotion_-_unknown_or_maybe_nomad.flac/in]
unknown destination port in attempted connection [ardour:i_wanna_give_you_devotion_-_unknown_or_maybe_nomad.flac/in]
Loading history from '/home/gilzad/test/test.history'.


**** alsa_pcm: xrun of at least 1234612105773.056 msecs

/* a couple of more xruns */

(ardour-2.5:7351): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

/* a couple of more Gtk assertions */

```

The output of Ardour's log window is:
```
[ERROR]: AudioSetup value for samplerate is missing data
[ERROR]: AudioEngine: cannot connect ardour:auditioner/out 1 (ardour:auditioner/out 1) to ardour:i_wanna_give_you_devotion_-_unknown_or_maybe_nomad.flac/in (ardour:i_wanna_give_you_devotion_-_unknown_or_maybe_nomad.flac/in)
[ERROR]: AudioEngine: cannot connect ardour:auditioner/out 2 (ardour:auditioner/out 2) to ardour:i_wanna_give_you_devotion_-_unknown_or_maybe_nomad.flac/in (ardour:i_wanna_give_you_devotion_-_unknown_or_maybe_nomad.flac/in)

```

Edit: The output of Jack's messages after starting Ardour is:
```
13:26:20.653 Patchbay deactivated.
13:26:20.660 Statistics reset.
13:26:20.773 ALSA connection graph change.
13:26:20.971 ALSA connection change.
13:26:27.765 ALSA connection graph change.
13:26:27.908 ALSA connection change.
```

The configuration for 0Hz does me wonder a bit as for the missing samplerate. But I can't estimate if that's the source of the problem or how I could change it.

---

### Post by Jeffrey Magder on 2009-02-16
I had been struggling with getting audio output to work as well, but thankfully just figured out why it was not working on my system.  

First, I followed these common directions:

1) kill all "jackd" processes (ie, killall -9 jackd)
2) Start qjackctl
3) Start Ardour

Of course this still didn't work for me.  In my case, the problem was that the [FONT="Courier New"]jackd[/FONT] setup was using the ALSA driver by default instead of the OSS driver.  

To fix, I clicked on "Setup" in the JACK Audio Connection Kit (ie, qjackctl).  In the dialog that followed, I changed the "Driver" box on the right to "oss" from "alsa".  I then clicked "OK", and was prompted with a dialog box letting me know that jackd had to be restarted for the new settings to take effect.  So I stopped JACK by clicking "stop" and restarted by clicking on "start".  In Ardour I then reconnected to JACK through Ardours menu system.  Specifically: JACK -> Reconnect.

As a final step I jumped out of my chair due to the volume being set WAY too loud. :P

---

### Post by gilli4 on 2009-02-18
Thanks a lot for your help everyone.

The problem is solved indeed. Jack is working finally, it's started and sound is there.

The reason I didn't have any sound seemed to be because of too small buffer sizes. Usually I'd know that since Jack would mention any jitters immediately. Don't know if any updates from the past might have fixed the Jack issue aswell without me noticing it.

Jeffrey, thanks a lot for the detailed instructions! Both, ALSA and OSS are working for me now. Could it be that increasing your buffer sizes would make Jack work with ALSA, too? That might confirm my assumption which I'm not very sure of yet. At least it would make sense to mark this thread as [solved] then.

Best regards,

Gilzad

---

