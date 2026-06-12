---
title: "[SOLVED] ID3 command line tagger with regexp capability"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by chochem on 2008-02-16
For fast harmonization of id3 tags nothing beats a command line solution. But i've only been able to find eyeD3 and though it seems an excellent little tool it sadly lacks regexp capabilities. Does anyobyd know of something that would have that? Or am I going to have to write a script that reads out the tags and leave the editing to sed?

EDIT: Okay I've found a couple more but still no regexp. And far more puzzling: Apparently simply reading out the value of a specified tags is also not an option ???

---

### Post by chochem on 2008-02-16
Oh well, I figured I might as well use whatever means wre available and make the best of it. Using the two little utils id3v2 (for reading) and eyeD3 (for writing), here's a solution.

Reading tags out into variables:
```
artist="$(id3v2 -l "$filename" | grep -E TPE?1 | sed -e 's/^.*:\ //g')"
album="$(id3v2 -l "$filename" | grep -E TALB? | sed -e 's/^.*:\ //g')"
title="$(id3v2 -l "$filename" | grep -E TI?T2 | sed -e 's/^.*:\ //g')"
track="$(id3v2 -l "$filename" | grep -E TRC?K | sed -e 's/^.*:\ //g')"
(...)
```

The grep command targets the line we're interested in and the sed command isolates the string value of tag in the question.The question mark in the grep line is for the variations in naming between id3v1 and id3v2.

eyeD3 has more options with regard to writing tags so it's good addition:
```
eyeD3 --artist="$artist2" --album="$album2" --title="$title2" --track="$track2" "$filename"
```

And in between all the usual things one can do with variables, e.g. going all lowercase:
```
artist=$(echo $artist  | tr  [:upper:] [:lower:])
album=$(echo $album | tr  [:upper:] [:lower:])
title=$(echo $title | tr  [:upper:] [:lower:])
(...)
```

---

### Post by chochem on 2008-02-16
oops

---

### Post by chochem on 2008-05-20
Somehow this developed into a sprawling monster of a script... If you're interested, check it out [here]("http://bash.viharpander.dk/#sego3").

---

### Post by soxs on 2008-05-20
Exactly what I was searching for.. doing it via GUI simply sucks (easytag, works fine, but don't want to spend my time by relabeling mp3tags..) and takes a hell lot of time

---

### Post by chochem on 2008-05-20
Cool - I hope it proves useful. If you have any thoughts, ideas, complaints etc. please let me know. I know that the documentation sucks but I kinda lost track of everything that it does and the exact reasons why. As the --help says, be sure to do a backup until you know what you're in for.

---

