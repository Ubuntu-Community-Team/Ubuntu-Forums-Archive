---
title: "RoseGarden won't start"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by muhkayoh on 2006-06-15
Hi,

I have Rosegarden installed, but when i try to launch it I just see the splash page for a second or two and then nothing ever happens. No error messages, just nothing.  Any ideas?  I'm using Ubuntu 6.06.

I have most other sound-related things working, after following the various HowTo entries at the Wiki.  I also did the basic Ubuntu Studio set up.  Just can't seem to launch Rosegarden.

Thanks,

Matt Jordan

---

### Post by bluevoodoo1 on 2006-06-15
Try running it from the terminal, then you will be able to see any potential errors.

---

### Post by muhkayoh on 2006-06-15
Thanks, but I can't seem to get anything to happen there.  I may not be using the right command, though, as I'm only 4 days into this linux thing.  I can run, for instance, mplayer from the terminal by just typing in 'mplayer'.  But when I just type in 'rosegarden', it tells me that's an unrecognized command.

Matt

---

### Post by bluevoodoo1 on 2006-06-15
Ok, I think it might be rosegarden4 or something equally as strange. 

What you can do is, a neat trick. Type "rose" then hit the Tab button on your keyboard and it should automatically complete it. If it doesn't, type a bit more of the name "rosegarden" then hit Tab and see what happens.

---

### Post by muhkayoh on 2006-06-15
Okay, this is weird.  I tried your suggestions and nothing worked.  It seemed the terminal was basically telling me that there was no rosegarden on my computer, so I went back to the applications menu to try again from there and - it's gone.  I had just tried opening it shortly before posting this thread, and now it's gone.  Haven't done an update in the meantime or anything.

That seems pretty weird.

I guess I'll try to reinstall it now and see what happens.

Thanks,

Matt

---

### Post by muhkayoh on 2006-06-15
More strangeness.

I decided not to reinstall Rosegarden just yet and instead played with Audacity.  I was able to record my voice via mic input.  All was well.

I shut down the computer and went out for some exercise.  Now that I've booted back up, Audacity tells me it can't start the i/o layer and it won't record.  I didn't do anything since the last time I used it!

So what's up?  First Rosegarden mysteriously disappears, and now Audacity stops working.  There's obviously something fundamental I'm not getting here.

Matt

---

### Post by muhkayoh on 2006-06-15
Rebooted again and now it's working again.

Matt

---

### Post by muhkayoh on 2006-06-15
Wow, something's going on, 'cause I have a serious case of the "now it works, now it doesn't" going on.

On this reboot, I don't hear anything coming out of timidity, whereas it was playing fine earlier.  And all I'm doing is trying software and rebooting the system.  I'm making no changes to things like soundcard watchamacallits or anything.  What is it about a boot-up that makes the working of sound-related programs so potluck?  And how can I get things to work consistently?

Thanks for any help.

Matt

---

### Post by muhkayoh on 2006-06-15
After experimenting with a couple more reboots, it seems to be the case that I can have either audacity or timidity work properly (depending on which one I tried to launch first) but not both.  In other words, if I launch audacity first, it works fine, but then I can't hear anything in timidity.  On the other hand, if I launch timidity first, I can hear it loud and clear, but then I can't record anything in audacity (even after shutting down timidity).

Now, linguistically, this makes a lot of sense, given that timidity and audacity are basically opposites.  :D

But from a software standpoint, it's kind of a pain in the butt. :mad: 

Matt

---

### Post by muhkayoh on 2006-06-15
No Jack success either:

> 

18:29:06.326 Patchbay deactivated.
18:29:06.362 Statistics reset.
18:29:06.741 MIDI connection graph change.
18:29:06.745 MIDI connection change.
18:29:18.260 MIDI connection graph change.
18:29:18.372 MIDI connection change.
18:29:19.745 MIDI connection graph change.
18:29:29.556 Startup script...
18:29:29.556 artsshell -q terminate
sound server terminated
18:29:30.709 Startup script terminated successfully.
18:29:30.754 JACK is starting...
18:29:30.754 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
18:29:30.770 JACK was started with PID=7227 (0x1c3b).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
18:29:30.931 JACK was stopped successfully.
18:29:32.861 Could not connect to JACK server as client. Please check the messages window for more info

I don't know what it means when it says that hw:0 is already in use.  I don't have anything else open but the web browser at the moment.

---

### Post by bluevoodoo1 on 2006-06-15
[QUOTE=muhkayoh]No Jack success either:

I don't know what it means when it says that hw:0 is already in use.  I don't have anything else open but the web browser at the moment.[/QUOTE]

Hmm... Very strange indeed. I wish I could help with that jack stuff...

---

### Post by cha0s on 2008-06-25
try this

```
sudo /sbin/alsa force-reload
```

There is some cleaner way to check what is locking up 'hw:0' and kill it instead of alsa, but I lost the link...

---

