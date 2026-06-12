---
title: "Rosegarden MIDI configuration tutorial for non-midi sound cards?"
date: 2012-02-24
forum: Multimedia Software
---

### Post by InnerBushman on 2012-02-24
Hi. I'm no musician so i don't have lot of experience with MIDI.
I installed Rosegarden, JACK and some other stuff but i haven't found a resonable instructions how to set this thing to play sound.
I bet that if i plug in some midi device i'll manage to direct the midi both ways (did that once before) but i have no idea how to configure this thing to play out sound on my integrated sound card.

Does any one of you know any decent step-by-step tutorial how to set this thing up?
Thanks in advance,
Bushman

---

### Post by shantiq on 2012-02-25
best route is timidity  

 [TiMidity++ version 2.13.2 -- MIDI to WAVE converter and player]


enter   ```
 timidity -iA
```   in terminal


and will see

> timidity -iA
Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 129:0 129:1 129:2 129:3



then read info [**here**]("http://ubuntuforums.org/showpost.php?p=11100906&postcount=4")


and check image &#9658;&#9658;&#9658;&#9658; **[ATTACH]198837[/ATTACH]**   in Rosegarden


should be all fine     if not ask for more details     :KS

---

### Post by InnerBushman on 2012-02-25
Ok, thanks. That works for me. (not always tho but i'll debug it later)

---

