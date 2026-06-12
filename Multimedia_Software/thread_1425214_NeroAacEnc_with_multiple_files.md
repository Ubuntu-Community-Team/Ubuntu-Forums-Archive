---
title: "NeroAacEnc with multiple files"
date: 2010-03-08
forum: Multimedia Software
---

### Post by Animortis on 2010-03-08
I would like to create AAC files using NeroAAC.

I have directories of wav files I need to encode and I cannot figure out how to do this with the neroAacEnc command on the command line. The program will not accept neroAacEnc -if *.wav -of *.aac as a valid command, though FAAC, LAME and OggEnc will accept similar commands.

I lack the coding skills to write a proper script for it. I'd just like to be able to type in a command and have an entire directory converted from wavs to aacs with the Nero codec. Is this possible? If not, can it be programmed? How?

Thanks.

Reference: NeroAac files [http://www.nero.com/eng/technologies-aac-codec.html](http://www.nero.com/eng/technologies-aac-codec.html)

---

### Post by mc4man on 2010-03-08
At the directory prompt for folder containing .wav's try this - (blue is adjustable, 0.375 is around 128k

```
for f in *.wav; do neroAacEnc -q [COLOR="Blue"]0.65[/COLOR] -if "$f" -of  "${f%.wav}.m4a"; done
```
or if you wish an .aac ext. (some players don't like the .aac ext 
```
for f in *.wav; do neroAacEnc -q [COLOR="Blue"]0.65[/COLOR] -if "$f" -of  "${f%.wav}.aac"; done
```

Note this will give you same name files, - spaces/characters  don't matter

---

### Post by Animortis on 2010-03-08
Amazing! Thank you! I am going to post this on Hydrogenaudio.org too, for people to use with credit to you.

---

### Post by mc4man on 2010-03-08
A very adaptable command, either alone or in a script.

you can adjust the save path by adding directly in front of
"${f%.wav}.m4a"

Ex. to Music dir in home
for f in *.wav; do neroAacEnc -q 0.65 -if "$f" -of [COLOR="Blue"]~/Music/[/COLOR]"${f%.wav}.m4a"; done

or make a dir in the pwd and save there
mkdir m4a
for f in *.wav; do neroAacEnc -q 0.65 -if "$f" -of [COLOR="Blue"]./m4a/[/COLOR]"${f%.wav}.m4a"; done

ect., ect.

---

