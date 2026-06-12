---
title: "How do I convert multiple wav files with LAME?"
date: 2010-06-30
forum: Multimedia Software
---

### Post by eladamri on 2010-06-30
I can't seem to figure out how to convert multiple wav files to mp3s on the command line with LAME without doing them one-by-one. It seems like a command such as the following would work:
```
> lame *.wav
```
My directory looks like this:
```
> ls
track01.wav
track02.wav
track03.wav
track04.wav
track05.wav
track06.wav
track07.wav
track08.wav
track09.wav

```
When I run lame this way here is the error I get:
```
> lame *.wav
lame: excess arg track03.wav
```

I wrote this simple script for it that has been working fine for the last few years:
```
mkdir wav
for file in *.wav
do
  basename="$(basename "$file" .wav)"
  lame --preset standard "$basename.wav" "$basename.mp3"
  mv "$basename.wav" wav/
done
```
It just seems like there should be a simple command for this process. Let me know there is a simple way to accomplish this that I am missing.

---

### Post by mc4man on 2010-06-30
You could use a for loop, the basic command is (blue is where any lame parameters go
```
for f in *.wav; do lame [COLOR="Blue"]-V 1[/COLOR] "$f" "${f%.wav}.mp3"; done
```

This can be expanded upon in various ways either as command or in script (ouput to another dir, create dir and output there and so on.
 if outputing   elsewhere path is directly in front of "${f%.wav}.mp3"
Ex.
```
for f in *.wav; do lame -V 1 "$f" [COLOR="blue"]~/Music/mp3/[/COLOR]"${f%.wav}.mp3"; done
```

---

### Post by deebocean on 2010-11-17
> **mc4man said:**
> You could use a for loop, the basic command is (blue is where any lame parameters go
```
for f in *.wav; do lame [COLOR="Blue"]-V 1[/COLOR] "$f" "${f%.wav}.mp3"; done
```

This can be expanded upon in various ways either as command or in script (ouput to another dir, create dir and output there and so on.
 if outputing   elsewhere path is directly in front of "${f%.wav}.mp3"
Ex.
```
for f in *.wav; do lame -V 1 "$f" [COLOR="blue"]~/Music/mp3/[/COLOR]"${f%.wav}.mp3"; done
```
Works great, thank you so much

---

