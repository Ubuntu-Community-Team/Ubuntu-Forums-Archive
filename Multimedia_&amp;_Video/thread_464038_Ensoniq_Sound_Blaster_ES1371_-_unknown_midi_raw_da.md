---
title: "Ensoniq Sound Blaster ES1371 - unknown midi raw data"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by sdil on 2007-06-04
my soundcard:

$ lspci -v <enter>
        00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 3
        I/O ports at e800 [size=64]
        Capabilities: <access denied>

i use ALSA. 

---------

i've installed ES1371 on my pc today and it works perfectly in playing mp3 and wave sound. but, when i play midi instruments (midi keyboard and midi drum), i got unknown midi raw data:

$ cat /dev/midi
[this is filled with one " ", SPACE everytime i press my midi keyboard] :o

before this, i use VIA soundcard and the midi raw data is:

$ cat /dev/midi
[this is filled with 2 character SYMBOL everytime i press my midi keyboard] :)

LMMS and Rosegarden can understand midi data from VIA soundcard, but i can't use my midi keyboard as midi input in LMMS and Rosegarden using Creative's  ES1371 (i'm preety sure LMMS and rosegarden cannot understand raw midi data of "spaces").

any idea?

---

