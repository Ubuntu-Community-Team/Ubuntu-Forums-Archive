---
title: "How to get MIDI working?"
date: 2011-03-04
forum: Multimedia Software
---

### Post by RobotGymnast on 2011-03-04
I installed a minimal Ubuntu install, and I can't get my MIDI to work. I have timidity installed, alsa-utils, freepats, jackd, and jackd2 installed. As for my sound card:

```
me@lappy486:~$ lspci | grep Audio
00:1b.0 [COLOR="Red"]**Audio**[/COLOR] device: Intel Corporation 82801H (ICH8 Family) HD [COLOR="red"]**Audio**[/COLOR] Controller (rev 03)

```

Thanks for any help.

---

### Post by Breambutt on 2011-03-04
If you're trying to play MIDI with Timidity in a sequencer/TuxGuitar/something, it's probably just PulseAudio getting in the way. Try killing it first or run *timidity -iA -Oj -B2,8* for a JACK port.

I'm not particularly familiar with all the MIDI nonsense, but what does *aplaymidi -l* tell you?

---

### Post by RobotGymnast on 2011-03-04
> **Breambutt said:**
> If you're trying to play MIDI with Timidity in a sequencer/TuxGuitar/something, it's probably just PulseAudio getting in the way. Try killing it first or run *timidity -iA -Oj -B2,8* for a JACK port.

I'm not particularly familiar with all the MIDI nonsense, but what does *aplaymidi -l* tell you?

Killing pulseaudio works great, but then no other audio works. As for the other stuff:

```
me@lappy486:~$ timidity -iA -Oj -B2,8
jack_client_new: deprecated
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
Couldn't open JACK device (`j')
```

How does one start a jack server?

And then ```
me@lappy486:~$ aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
128:0    TiMidity                         TiMidity port 0
128:1    TiMidity                         TiMidity port 1
128:2    TiMidity                         TiMidity port 2
128:3    TiMidity                         TiMidity port 3
129:0    rosegarden                       record in
129:2    rosegarden                       external controller

```

Edit: Actually, killing PulseAudio doesn't seem to work anymore.. Weird.

---

### Post by Breambutt on 2011-03-04
Alrighty, so you're new to JACK too.

Qjackctl (JACK Control under Sound & Video [and Audio Production in UbuStudio]) is probably a good way to start, you can figure out proper settings yourself from the GUI. Trial and error to make the best of your system but basically all you have to do is press "Start".

I've just purged PulseAudio completely ever since Hardy, it still doesn't work sufficiently on any level even with my relatively popular sound card and is of no use whatsoever. ALSA is more than fine, but I don't own any laptops so don't treat this as a universal truth.

There's probably a way or two to make Timidity function under PA but I smell it's going to be messy. On the other hand, if anyone can prove my gut instinct wrong, I'd be interested in hearing all about it.

P.S. PulseAudio has a habit of restarting itself (except for when running JACK) like every 5 seconds or when you use software that uses audio, even the browser.

---

### Post by RobotGymnast on 2011-03-06
Turns out timidity was working fine; Rosegarden was having the issues (the MIDI devices got themselves unselected somehow).

---

