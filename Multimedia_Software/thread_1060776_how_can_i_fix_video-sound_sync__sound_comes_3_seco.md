---
title: "how can i fix video-sound sync ? sound comes 3 second late"
date: 2009-02-05
forum: Multimedia Software
---

### Post by turna on 2009-02-05
i have a video which have video-sound sync problem. 
the sound comes 3 second after the video. how to fix this ? can  ffmpeg do this ? what shoul be the command ?

---

### Post by ohgodnotanother1 on 2009-02-05
Looks like ffmpeg can provide this feature...

> `-itsoffset offset'
    Set the input time offset in seconds. [-]hh:mm:ss[.xxx] syntax is also supported. This option affects all the input files that follow it. The offset is added to the timestamps of the input files. Specifying a positive offset means that the corresponding streams are delayed by 'offset' seconds. 

Too lazy to search youself?;)

---

### Post by turna on 2009-02-07
what is the command

ffmpeg hv.flv -itsoffset offset 3

this it not working

---

### Post by ohgodnotanother1 on 2009-02-08
Try:
ffmpeg hv.flv -itsoffset 3

---

### Post by turna on 2009-02-08
thank you but i got this ;

> File 'hv.flv' already exists. Overwrite ? [y/N] y
Must supply at least one input file

---

### Post by ohgodnotanother1 on 2009-02-09
You must supply an input file. Do it like this:

ffmpeg -itsoffset 3 -i hv.flv output.flv

---

### Post by turna on 2009-02-09
thank you. works perfectly.

---

