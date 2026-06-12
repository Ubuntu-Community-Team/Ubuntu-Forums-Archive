---
title: "LAME not cooperating in command line"
date: 2013-01-13
forum: Multimedia Software
---

### Post by alreadytaken4536 on 2013-01-13
I've been ripping CD's in .wav and using LAME in Terminal to convert them to .mp3 V0 quality. 

```
~/Music/Dio - (1987) Dream Evil$ ls
01. Night People.wav               06. Overlove.wav
02. Dream Evil.wav                 07. I Could Have Been a Dreamer.wav
03. Sunset Superman.wav            08. Faces in the Window.wav
04. All the Fools Sailed Away.wav  09. When a Woman Cries.wav
05. Naked in the Rain.wav

```:guitar:

To avoid having to run a separate command for each track, I've been using a script type thing that I found in this thread: [http://ubuntuforums.org/showthread.php?t=1521067](http://ubuntuforums.org/showthread.php?t=1521067) My only options when converting to mp3 are -v0 and -q0, so the code looks like this:

```
~/Music/Dio - (1987) Dream Evil$ for f in *.wav; do lame -v0 -q0 "$f" "${f%.wav}.mp3"; done
lame: unrecognized option -0
lame: unrecognized option -0
lame: unrecognized option -0
lame: unrecognized option -0
lame: unrecognized option -0
lame: unrecognized option -0
lame: unrecognized option -0
lame: unrecognized option -0
lame: unrecognized option -0

```This is the first album that I've ripped so far where LAME has given me any lip. So I guess it wants me to separate those options so that it says -v 0 and -q 0 instead? Let's try again.

```
~/Music$ for f in *.wav; do lame -v 0 -q 0 "$f" "${f%.wav}.mp3"; done
lame: excess arg *.mp3

```

Maybe it will only work if I do one of the q presets so that I can put all the options together.

```
~/Music/Dio - (1987) Dream Evil$ for f in *.wav; do lame -hv 0 "$f" "${f%.wav}.mp3"; done
lame: excess arg 01. Night People.mp3
lame: excess arg 02. Dream Evil.mp3
lame: excess arg 03. Sunset Superman.mp3
lame: excess arg 04. All the Fools Sailed Away.mp3
lame: excess arg 05. Naked in the Rain.mp3
lame: excess arg 06. Overlove.mp3
lame: excess arg 07. I Could Have Been a Dreamer.mp3
lame: excess arg 08. Faces in the Window.mp3
lame: excess arg 09. When a Woman Cries.mp3
```

Welp, I guess that doesn't work either. I wonder why LAME all of a sudden decided that the output part of the syntax is unnecessary. This code has ALWAYS worked for me up until this album. I have no idea what I'm doing any differently that it won't work this time. Any insight?

---

### Post by steeldriver on 2013-01-13
I don't know/use lame, but according to the man page, the -v option (variable bit rate) doesn't take a parameter, so it would be

```
for f in *.wav; do lame [COLOR=Red]-v -q0[/COLOR] "$f" "${f%.wav}.mp3"; done
```That would be consistent with it complaining about an extra 0

EDIT: or perhaps you meant capital V? -[COLOR=Red]V[/COLOR]0

```
[COLOR=Red]-v[/COLOR]
use variable bitrate (--vbr-new)
--vbr-old
    Invokes the oldest, most tested VBR algorithm. It produces very good quality files, though is not very fast. This has, up through v3.89, been considered the "workhorse" VBR algorithm. 
--vbr-new
    Invokes the newest VBR algorithm. During the development of version 3.90, considerable tuning was done on this algorithm, and it is now considered to be on par with the original --vbr-old. It has the added advantage of being very fast (over twice as fast as --vbr-old). 
[COLOR=Red]-V n[/COLOR]

0 <= n <= 9
    Enable VBR (Variable BitRate) and specifies the value of VBR quality (default = 4). 0 = highest quality.
```

---

### Post by alreadytaken4536 on 2013-01-13
> **steeldriver said:**
> I don't know/use lame, but according to the man page, the -v option (variable bit rate) doesn't take a parameter, so it would be

```
for f in *.wav; do lame [COLOR=Red]-v -q0[/COLOR] "$f" "${f%.wav}.mp3"; done
```That would be consistent with it complaining about an extra 0

EDIT: or perhaps you meant capital V? -[COLOR=Red]V[/COLOR]0

Oops! You're absolutely right; it needed to be a capital V. It's all working as expected now. Just goes to show how careful you have to be with specificity in your commands. Thank you for pointing that out.

---

