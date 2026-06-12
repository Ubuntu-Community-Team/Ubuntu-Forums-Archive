---
title: "Timidity works great - no sound in Rosegarden"
date: 2011-03-05
forum: Multimedia Software
---

### Post by RobotGymnast on 2011-03-05
Exactly as the topic says; running a MIDI file through Timidity in command-line works fine, but doing it in Rosegarden just outputs silence.

Any help is appreciated.

---

### Post by shantiq on 2011-03-06
ok   this is kinda my special area of interest   see if if we can get that going

First thing is to enter after you have opened Rosegarden   ```
timidity -iA
``` into your terminal   you will see something of the sort


```
Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3

```

then to go back to rosegarden

and do what it shows on the attached image
 1. click on keyboard (manage midi devices)
 2. then click on first item in midi playback box (0) and link with (0) in Midi Outputs box (0)


make sure you pick the one furthest down the list

do same for other midi(s)


hope this helps

======================================================

[B]bonus info
[/B] ( if you already know simply ignore this )


if you wish to turn your midi to wav later use



```
   timidity  -A120 filename.mid -Ow2 -o filename.wav 

```

i have included -A120 to hike the sound a little since midi is usually low but it can be omitted

also change -Ow2  to -Ow if you want 16-bit wav and not 24-bit

wav can be changed to flac

---

### Post by RobotGymnast on 2011-03-06
> **shantiq said:**
> ok   this is kinda my special area of interest   see if if we can get that going

First thing is to enter after you have opened Rosegarden   ```
timidity -iA
``` into your terminal   you will see something of the sort


```
Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3

```

then to go back to rosegarden

and do what it shows on the attached image
 1. click on keyboard (manage midi devices)
 2. then click on first item in midi playback box (0) and link with (0) in Midi Outputs box (0)


make sure you pick the one furthest down the list

do same for other midi(s)


hope this helps
...

Yup it works great. Boy do I feel silly for not checking that. Strange, though, because it worked for a short time a while ago.. No idea how the devices got unset.

---

### Post by Alfred_McGee on 2011-04-30
@shantiq:

Like nearly all Rosegarden commentators, I get no sound! Your instructions above are all good until this: 

            > 2. then click on first item in midi playback box (0) and link with (0) in Midi Outputs box (0)

I only have one item in the playback box, so I don't know what your "(0)" means. I have many items in the output box, from Timidity ports with different numbers to "No port." Trial and error has gotten me nowhere. This is especially annoying because I have gotten Rosegarden to produce sound before on older Ubuntu versions. All I need Rosegarden for is to playback scores that I write.

---

### Post by shantiq on 2011-04-30
Alfred if you only have one midi there 

open your terminal and enter  ```
timidity -iA
```

**then** go to manage midi devices

and click on your only channel which numbers 0; and click on the lowest 0 on the right panel . Indeed numbers 0 1 2 3 will all work picked from the midi output box which have just been added by doing ```
timidity -iA
```


added tool:   once you have done all that if you still get no sound shut rosegarden (you may hear sound as it shuts) reload and do not do the timidity thing it is already there simply  load up your midi file and play ( sometimes it takes that to get it to start)


  see attached image


**PS** i also have ubuntustudio-audio installed from synaptic i think but i am not totally sure that it is required for rosegarden but maybe go for that too.

---

### Post by Alfred_McGee on 2011-04-30
When I got Rosegarden working in Ubuntu 9.04, I didn't have Ubuntustudio-audio installed. Rosegarden gave me lots of error messages at start up, but it always worked. Anyway, thanks for your pointers, shantiq. I tried everything you said, then installed 'studio-audio and tried it all again, but still no sound. If you have any other hints, please let me know.

---

### Post by shantiq on 2011-05-01
sorry Alfred that is all i got.  It is a temperamental program in my experience.  Try an earlier version mayhaps?? One day it will start working and you won't even know why:KS

---

### Post by Alfred_McGee on 2011-05-01
I tried Ubuntu 11.4 the other day, but went back to 10.10 because I prefer the Gnome desktop. The Rosegarden that comes with 11.4 has a different number after it, but do you think it would be different?

---

### Post by shantiq on 2011-05-01
sorry Alfred really do not know.:KS try all permutations if you have the patience. I seem to remember once i had no sound; installed ubuntu-studio then had sound so maybe something in there is required but i do not know what. It is so complex the whole sound experience on Ubuntu. I wish you luck or someone might come along who knows much more

---

### Post by Alfred_McGee on 2011-05-15
Finally got Rosegarden to play back musical scores with sound in Ubuntu 10.10! Ubuntu Studio was **NOT** necessary. All I had to install in addition to Rosegarden itself was Qsynth. This tutorial, like most Rosegarden documentation, is old, but it worked, at least for me: [http://gauthampai.livejournal.com/62383.html](http://gauthampai.livejournal.com/62383.html)

---

### Post by mozgren on 2012-10-02
"open your terminal and enter
Code:
timidity -iA"

This solved a routine headache here.  Thanks!

I've other Rosegarden problems - the most significant of which is of how to prevent notes from being sustained indefinitely and the whole composition sounding like a bad orchestral tuning session.  I suspect this is a Timidity issue and don't expect a reply from you.

---

### Post by overdrank on 2012-10-02
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

