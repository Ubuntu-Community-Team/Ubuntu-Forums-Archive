---
title: "SKYPE cant speak"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by ashrack on 2006-06-12
I can hear the man am chatting with but he cant hear me. Although when speaking to the MIC I can here myself perfectly in the headsets' speaker, 

I installed SKYPE like this:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Messenger_.28Skype.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Messenger_.28Skype.29)

LSPCI:
```
0000:01:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: Hercules: Unknown device a010
        Flags: bus master, slow devsel, latency 32, IRQ 201
        Memory at e6100000 (32-bit, non-prefetchable) [size=4K]
        Memory at e6000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2

```
Human name for my sound card: Hercules Fortissimo II

---

### Post by asalam on 2006-06-22
hmm i have the same problem and thesame videocard so im very interested in a solution as well

---

### Post by ashrack on 2006-06-29
Since apperantly its not a problem with SKYPE! Cos with WENGO I have the same problem.
So please post here from now on.
[http://www.ubuntuforums.org/showthread.php?p=1196209#post1196209](http://www.ubuntuforums.org/showthread.php?p=1196209#post1196209)

---

### Post by gratefulfrog on 2006-06-29
have you checked the asla mixer settings to be sure that the mic is the "capture" device...

try 
```
$ alsamixer
```

and play with the settings, test with the sound recorder, with no sound using devices started (rebooot first to be sure that you're clean). You'll probably have to enable "mic boost" to get the vu to a reasonable level.

When you get it working, be sure to set up dsp hijacker script to prevent skype from hogging the dsp device. You can find that at: [http://195.38.3.142:6502/skype/]("http://195.38.3.142:6502/skype/")

good luck, let us know if it works!
GF.
[http://gratefulfrog.net]("http://gratefulfrog.net")

---

### Post by ashrack on 2006-06-30
GRATEFUL
I've replied U in this thread:
[http://www.ubuntuforums.org/showthread.php?p=1196209#post1196209](http://www.ubuntuforums.org/showthread.php?p=1196209#post1196209)

Since this is not related to SKYPE anymore I've rather created a new thread,here, so please reply there:
[http://www.ubuntuforums.org/showthread.php?p=1196209#post1196209](http://www.ubuntuforums.org/showthread.php?p=1196209#post1196209)

---

