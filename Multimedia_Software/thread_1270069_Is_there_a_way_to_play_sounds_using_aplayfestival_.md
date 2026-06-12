---
title: "Is there a way to play sounds using aplay/festival while amarok is playing?"
date: 2009-09-19
forum: Multimedia Software
---

### Post by KIAaze on 2009-09-19
Is there a way to play sounds using aplay/festival while amarok is playing?

It seems when amarok (or any other GUI player) is playing, I can't play sounds from the command-line using aplay, mplayer or festival. :(

Either I get a "can't open /dev/dsp" message, or it waits until I quit the blocking app.
What's strange is that I can hear the sound of a movie while listening to music in Amarok, so sound mixing is definitely possible.

---

### Post by KIAaze on 2009-09-19
Solved by using "padsp":
```
echo $MESSAGE | padsp festival --tts
padsp aplay $FILE 1>/dev/null 2>&1 &

```

I tried it before and it failed, but maybe that's because I tried a lot of different things.
I also have this in "~/.festivalrc"
```
;use ALSA
(Parameter.set 'Audio_Method 'Audio_Command)
(Parameter.set 'Audio_Command "aplay -q -c 1 -t raw -f s16 -r $SR $FILE")

```

For some reason, I can even use aplay and festival without padsp now while amarok is running... :confused:
Is it enough to run the padsp command only once? :confused:

So, solved, but remains to be seen how well.

---

