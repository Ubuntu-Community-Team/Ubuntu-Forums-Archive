---
title: "Converting multiples .wav files to .mp3"
date: 2009-12-16
forum: Multimedia Software
---

### Post by tubbe on 2009-12-16
Hey

I am trying to convert an entire directory with .wav files to .mp3. I read about it in some old forum post, and I tried to make a script, but it doesn't seem to work.

Here it is:
```
for f in *.wav; do lame -b 320 "$f" `basename "$f" .wav`.mp3 || echo FAILED;
```Anybody sees what's wrong?

---

### Post by Marlonsm on 2009-12-16
There are quite some sound converters in the Software Centre, take a look there.

---

### Post by andrew.46 on 2009-12-16
Hi tubbe,

Does this work a little better:


```

for f in *.wav
   do 
   lame -b 320 "$f" "${f%.wav}.mp3"
done

```

Mind you *-b 320* might be a little much, some discussion here:

LAME
[http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)

Andrew

---

