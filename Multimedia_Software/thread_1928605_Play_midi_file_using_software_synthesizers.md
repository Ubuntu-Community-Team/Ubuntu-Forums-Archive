---
title: "Play midi file using software synthesizers?"
date: 2012-02-20
forum: Multimedia Software
---

### Post by Chiel92 on 2012-02-20
Hi all,

I want to be able to play a midi file using software synthesizers.
I already have everything working for a midicontroller/keyboard, but not for midi files.
How can I link the midi file to a synthesizer, say Aeolus? (I use jack)
Aeolus cannot just open a midi file, but it can process realtime midi data (by linking a midi source to it in Jack).

Does anyone know how I can make Aeolus (and similar programs) play a midi file?

Thanks in advance!

---

### Post by Chiel92 on 2012-02-24
bump

---

### Post by Chiel92 on 2012-03-07
Bump.
Just to clarify: How can I transform a midi file into midi events that can be picked up by other programs (such as software synthesizers)?

---

### Post by shantiq on 2012-03-07
> **Chiel92 said:**
> Hi all,

I want to be able to play a midi file using software synthesizers.
I already have everything working for a midicontroller/keyboard, but not for midi files.
How can I link the midi file to a synthesizer, say Aeolus? (I use jack)
Aeolus cannot just open a midi file, but it can process realtime midi data (by linking a midi source to it in Jack).

Does anyone know how I can make Aeolus (and similar programs) play a midi file?

Thanks in advance!


this might help you to play the file

install timidity    ```
sudo apt-get install timidity
```     then enter ```
timidity name.mid
```


But to use a software synth i think you have to use  QjackCtl  once you have Jackd installed ```
qjackctl
```and click on connect to link everything in the right way play around with that you should find your way through.. 
[CENTER][ATTACH]213864[/ATTACH][/CENTER]



**also** qsynth in software center is probably a lot more evolved than aeolus


[CENTER][ATTACH]213868[/ATTACH][/CENTER]

---

### Post by Chiel92 on 2012-03-07
Thanks for your reply!
I have those programs installed. But I cannot see how I can connect the midi output of timidity to any other program. It appears that timidity has an input port only (Under the alsa tab in jack connections). Do you have suggestions?

---

### Post by shantiq on 2012-03-07
hi Chiel   sadly i only have experience of timidity with rosegarden for midi composition


no doubt someone else knows is this not an output port here on the left  



[CENTER][ATTACH]213870[/ATTACH][/CENTER]


forgot to say i ran ```
timidity -iA
``` in terminal first to get started
it gives you this

> timidity -iA
Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 129:0 129:1 129:2 129:3



to create connections








also maybe ask same question at the [**ubuntu studio**]("http://ubuntuforums.org/forumdisplay.php?f=335") section of forum

---

### Post by lykwydchykyn on 2012-03-07
Basically you need a midi player.  A sequencer like Rosegarden will work, but it might be overkill.

There are a few simple MIDI players in the repos, like pmidi and wildmidi, but I can't personally vouch for them.

---

### Post by shantiq on 2012-03-07
if you are happy to install Rosegarden   do


```
timidity -iA
```


then go File import your midi file in RG

open manage midi devices  [ the keyboard sign with green ]


then pick the lowest port 0 on midi outputs see image

[CENTER][ATTACH]213878[/ATTACH][/CENTER]


This will allow you to play AND edit your midi file

---

### Post by Chiel92 on 2012-03-07
> **lykwydchykyn said:**
> Basically you need a midi player.  A sequencer like Rosegarden will work, but it might be overkill.

There are a few simple MIDI players in the repos, like pmidi and wildmidi, but I can't personally vouch for them.

Yeah, thanks, that works. I tried pmidi, and it works perfectly.
Rosegarden is a bit overkill indeed, but also works of course.
Thanks for your help, guys!

Regards

---

