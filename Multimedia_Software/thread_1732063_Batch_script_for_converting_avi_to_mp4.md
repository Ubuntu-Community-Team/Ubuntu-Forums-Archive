---
title: "Batch script for converting avi to mp4"
date: 2011-04-17
forum: Multimedia Software
---

### Post by vladoportos on 2011-04-17
Hello all,

This might be useful for somebody... 

I made script for converting avi to mp4 for streaming, works fine on my server and for past 3 weeks there was no issue, wowza media server streams this kind of converted videos without an issue...

But I would welcome some help to perfecting the conversion and add more features... but I want to avoid complicating setting just script that do all for user it self :)

See script and how to use here :KS [http://vladoportos.sk/scripting/batch-video-convert-script-avi-to-mp4/]("http://vladoportos.sk/scripting/batch-video-convert-script-avi-to-mp4/")

---

### Post by DaithiF on 2011-04-17
Hi,
nice script.  3 minor suggestions:
1. The thread variable has no default value, if the user doesn't pass a parameter as $1 I'm not sure how the conversion program will like the -threads <blank> -s etc...
you can give it a default value like:
thread=${1-2}  # defaults to the value 2 if $1 is not supplied

2. no need for chaining together multiple calls to tr, instead tr -d '() ' will delete each of the characters (, ) and space

3. you mix $( ... ) and backticks ``for executing external commands ... probably better to be consistent and use one consistently ... $( ... )

---

### Post by vladoportos on 2011-04-17
Ah thanks, will do, there is actually parameter for threads that lets ffmpeg choose how many he use.. 

Will change the tr as soon as I can + the external commands.

Many thanks for pointers :KS

---

