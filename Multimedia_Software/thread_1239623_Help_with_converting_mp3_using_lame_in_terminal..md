---
title: "Help with converting mp3 using lame in terminal."
date: 2009-08-13
forum: Multimedia Software
---

### Post by Blue Dolphins on 2009-08-13
I want to convert some 320 mp3s to 160, and looking for information I found this bit of code for converting multiple mp3's with lame, but the thread was archived so I couldn't ask there.

for f in *.mp3 ; do lame --mp3input -b 160 $f <path_to_destination>/$f

Can someone explain to me how this work, or give me an example?  In particular, I don't understand "for f in *.mp3" or the "$f".  where would I type the name of the folder I want to convert?

---

### Post by andrew.46 on 2009-08-14
Hi Blue Dolphins,

You have a *for loop* there, or at least part of one :-). A slightly cleaned up version would be, with thanks to mc4man:

```
for f in *.mp3
do 
lame --mp3input -b 160 "$f" "${f%.mp3}_160.mp3"
done
```

This could still do with some work which I invite others to chip in on! You need to run this in a terminal in the actual directory with all of your mp3s. It finds all files that end in *.mp3*, runs the lame command across them and names the output file ***[COLOR="Red"]input_name[/COLOR]**_160.mp3*. The naming of the output file is a little twisted, although it works and I am not entirely sure if --mp3input is really needed here. Still if nobody renovates this syntax I shall work a little more on it :-).

Andrew

---

### Post by mc4man on 2009-08-14
While i haven't tried I'd think the --mp3input is needed because lame normally expects a .wav as input. 
To resolve the adding to name just output to a different dir., either somewhere else or make a dir. inside the current one and output there.(just put path directly in front
Ex. dir inside current working dir. named 160k

./160k/"${f%.mp3}.mp3"

The main problem using lame like this is you'll lose any tags, so to retain you'd need to script in somehow. (no different than mp3 to wav to mp3, tags are lost

I don't know how to do that except for a method I use for files that don't have any to begin with - aac's I ripped with neroAac before figuring how to tag during rip and for extracting concert dvd tracks or for wma lossless which I haven't found a converter that reads the tags.

 In those cases I use a series of echo and reads in various scripts to set the overall tags (album, artist, year, genre and a cut-sed-cut to give each the proper track name and track number.

Otherwise soundkonverter will transcode mp3 to mp3 and rewrite the current tags

So if sk can re-tag I'm sure it could be scripted in, my silly read,echo isn't suitable in this particular case I wouldn't think

---

### Post by andrew.46 on 2009-08-15
Hi mc4man,

> **mc4man said:**
> While i haven't tried I'd think the --mp3input is needed because lame normally expects a .wav as input.

I have revisited this particular for loop and I have found that the --mp3input is actually not required, certainly not for lame 3.98. I delved into the man pages and saw the answer there:

```

--mp3input
   Assume the input file is a MP3 file.
   Useful for downsampling from one mp3 to another.  As an example,
   it can be useful for streaming through an IceCast server.
  ***[COLOR="Red"] If  the  filename  ends in ".mp3" LAME will assume it is an MP3.[/COLOR]***
   For stdin or MP3 files which do not end in .mp3 you need to  use
   this switch.

```

Anyway it is a minor point but this leaves a slightly cleaner syntax.

All the best,

Andrew

---

