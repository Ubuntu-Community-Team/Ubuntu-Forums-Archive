---
title: "[gimp] crop/cut something out of an image #2"
date: 2015-10-15
forum: Multimedia Software
---

### Post by FakeOutdoorsman on 2015-10-15
This is a continuation of the closed thread [[gimp] crop/cut something out of an image](http://ubuntuforums.org/showthread.php?t=2298664). I didn't get why it was closed, but it prevented me from providing a more efficient answer. I attempted to contact the moderator who closed the thread and received no reply, and also received no reply in #ubuntuforums. (So go ahead and merge if you like).

The question:
[quote="joe.koenig"]I can't seem to be able to perform one single, simple task: cut/crop a portion from the middle of an image. Just a portion in the middle the picture. I.e: Imagine a pictiue. Divide it into three vertically equally sized parts. Cut/crop the middle part out and make a new picture of the two remaining fragments.[/quote]

This can be done with a single command using ffmpeg for any sized image or video:
```
ffmpeg -i input -filter_complex "[0:v]crop=iw:ih/3:0:0[top];[0:v]crop=iw:ih/3:0:ih-oh[bot];[top][bot]vstack" output
```

If your ffmpeg is too old for the vstack filter, then simply [download a recent build](http://ffmpeg.org/download.html) (also see [how to use](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu#Usage)).

---

### Post by shantiq on 2015-10-16
so cool Fake how would you modify the syntax here [i tried and failed] to divide crop and splice horizontally [the other way] ?

---

### Post by coldraven on 2015-10-16
> **shantiq said:**
> so cool Fake how would you modify the syntax here [i tried and failed] to divide crop and splice horizontally [the other way] ?

FakeOutdoorsman is the Chuck Norris of the ffmpeg world! Not only can he chop down mountains but he uses ffmpeg to butter his toast in the mornings :)
Maybe we should start a separate thread on this theme :lolflag:

---

### Post by shantiq on 2015-10-16
[+1]Yes Cold Bird maybe we are a smidgeon off topic but then again maybe not as praise and gratefulness cannot be out of topic ...   for he is a Master

Yes he is that good he probably could run a dating site with it :]

PS   and to be back in topic i tried twelve or thirteen permutations to get the horizontal cut worked out but hey I need a masterclass here; so we await with bated breath ....   please tell us Great FF    and thank you!

PS2 [only for comedy lovers]
Some say there is even an ffmpeg command which might allow one to walk on H[SUB]2[/SUB]O

---

### Post by FakeOutdoorsman on 2015-10-17
> **shantiq said:**
> so cool Fake how would you modify the syntax here [i tried and failed] to divide crop and splice horizontally [the other way] ?
I find breaking up the command so each filterchain is on its own line makes filtering easier to follow:
```
ffmpeg -i input -filter_complex \
"[0:v]crop=iw/3:ih:0:0[l]; \
 [0:v]crop=iw/3:ih:iw-ow:0[r]; \
 [l][r]hstack" \
output
```

The 4 colon separated parts of crop consist of:
```
crop=width:height:x position:y position
```

Imagine a 640x480 input. The second crop in the example:
```
crop=iw/3:ih:iw-ow:0
```
would be the same as:
```
crop=640/3:480:640-(640/3):0
```
which is the same as (approximately since I rounded):
```
crop=213:480:426:0
```
From the 640x480 sized input this will make a 213x480 sized output. The 426 means the starting position from the crop will be 426 pixels over to the right.

See the [crop filter documentation](https://ffmpeg.org/ffmpeg-filters.html#crop) for info on each of those options.

[QUOTE=coldraven]...he uses ffmpeg to butter his toast in the mornings[/QUOTE]
Thank you for the kind words, but butter sometimes gives me gas. To borrow andrew.46's signature:
[quote=Morpheus]You think that's air you're breathing now?[/quote]

[quote=shantiq]...he probably could run a dating site with it :][/quote]
"Likes: filtergraphs, stream specifiers, muxing."

Ladies, please form an orderly queue.

---

### Post by shantiq on 2015-10-17
Thanx Fake no wonder I was short of the mark :] great explanations
This is TRULY astounding software !

Ps: also entered in my terminal ffmpeg  -i EurasianPrincess -i MiddleAgedFrenchDude --"Likes: filtergraphs, stream specifiers, muxing"  BlissfulCouple.mkv

Will report :]

---

