---
title: "why wont this bit of (sound related) bash work reliably?"
date: 2008-05-25
forum: Multimedia Software
---

### Post by CrazyGuy123 on 2008-05-25
I've narrowed my problem down to this code:

```
while [ true ]; do
 echo hello my name is foo | flite -o /dev/stdout | aplay -r 16000 -f S16_LE
done

```

The loop will go round 25 or so times, and then suddenly fail on the 26th.  It fails randomly - next time I run the script it might fail on the 5th time, and another time it might fail on the 100th time.

The following however works forever:
```
while [ true ]; do
 echo hello my name is foo | flite -o /dev/stdout > testfile
 cat ./testfile | aplay -r 16000 -f S16_LE
 rm ./testfile
done

```

so basically there's some problem with the pipe between flite and aplay.

When it fails, it makes no sound and doesn't output anything on the console.  Ctrl+C kills the process and continues the loop successfully.

---

