---
title: "Is it possible to convert multiple mkv files using mkvdts2ac3.sh?"
date: 2012-11-13
forum: Multimedia Software
---

### Post by 2d2f on 2012-11-13
How?

---

### Post by andrew.46 on 2012-11-13
You should be able to use this script in a *for* loop if the script itself will not accept multiple input files.

---

### Post by evilsoup on 2012-11-14
Maybe paste the script in between [ code][/code] tags or, if it's too long for that, put it in an attachment?

Andrew' suggestion is probably going to be the easiest, but we can't give any more useful information until we know how the script works, or at least its syntax. Give an example of how you would use the script for a single file, and a for loop would be trivial to construct.

---

### Post by shantiq on 2012-11-15
sorry had a thought but not useful here

---

### Post by shantiq on 2012-11-16
hi there Andrew   would you create the loop inside the [**script**]("https://bitbucket.org/ishitori/home-scripts/raw/f8d613d38cd72cafbf67f129ba3986f44148470d/mkvdts2ac3.sh")


or outside?   i thought outside once it has been placed in the folder where the mkvs are




> for f in *.mkv do ./mkvdts2ac3.sh "${f%.*}" ; done     is not quite right is it?

---

### Post by evilsoup on 2012-11-16
That seems like a really overlong script, for what it does.

*If* the standard usage is 
```
./mkvdts2ac3.sh input.mkv
```
then
```
for f in *mkv; do mkvdts2ac3.sh "$f"; done
```
No need for squiggly brackets, so far as I can see - you use those mostly for substitutions, i.e. changing 'mkv' to 'mp4' for a *for* loop containing ffmpeg - and you need a semicolon before the 'do'.

---

### Post by andrew.46 on 2012-11-16
> **shantiq said:**
> hi there Andrew   would you create the loop inside the [**script**]("https://bitbucket.org/ishitori/home-scripts/raw/f8d613d38cd72cafbf67f129ba3986f44148470d/mkvdts2ac3.sh")


or outside?   i thought outside once it has been placed in the folder where the mkvs are

With a very appreciative nod to the creator of this script I have to admit that for my own personal usage I would tend *not* to use such scripts. With a little work and experimentation it is possible to do most of this sort of work 'by hand'. But if using it I would use a method similar to that described by evilsoup.

---

