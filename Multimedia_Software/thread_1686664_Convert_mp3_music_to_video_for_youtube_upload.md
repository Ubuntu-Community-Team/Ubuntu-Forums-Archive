---
title: "Convert mp3 music to video for youtube upload"
date: 2011-02-12
forum: Multimedia Software
---

### Post by bennettg on 2011-02-12
hi i am a noon and have been searching for a program to convert my music mp3 files to video files to upload on youtube.  does anyone know of one, especially if it will bulk convert.  i know i need to add a jpeg or something too.  thanks

---

### Post by ron999 on 2011-02-12
Hi
If you have a jpg file and an mp3 file you can use ffmpeg to do the job:-
```
ffmpeg -loop_input -i picture.jpg -i music.mp3 -shortest -acodec copy video.mp4
```

To use this for bulk conversion you would probably need to write a script.
:)

---

### Post by bennettg on 2011-02-12
> **ron999 said:**
> Hi
If you have a jpg file and an mp3 file you can use ffmpeg to do the job:-
```
ffmpeg -loop_input -i picture.jpg -i music.mp3 -shortest -acodec copy video.mp4
```

To use this for bulk conversion you would probably need to write a script.
:)

Thanks....i'll need to find a primer on writing a script somewhere.  I'm surprised that there isnt a program

---

### Post by bennettg on 2011-02-13
anyone?

---

### Post by SushiR on 2011-10-05
I second that. A script to fill in the parameters would be great. I'm too stupid to do it...

---

### Post by shantiq on 2011-10-06
> **bennettg said:**
> hi i am a noon and have been searching for a program to convert my music mp3 files to video files to upload on youtube.  does anyone know of one, especially if it will bulk convert.  i know i need to add a jpeg or something too.  thanks



kdenlive will do that for you beautifully here is[** one**]("http://www.youtube.com/watch?v=b0MIB8V3SCc") i made with kdenlive from 3 spliced mp3 and 3 jpeg


kdenlive is in your synaptic


or you can install from terminal    ```
sudo apt-get install kdenlive
```


easy to use    drag photos into project tree then down to video 1
and insert your mp3 same way into audio line


then click on render choose format and presto

REALLY stable program and good fun:KS

---

### Post by aeiah on 2011-10-06
in python. takes two arguments - the image and the mp3 file (in either order), and outputs the video with the same name as the mp3 (but with a mp4 extension). either drag image+mp3 onto the script, use on the cli or use as a nautilus action.

```

#! /usr/bin/env python

import sys, os

inputOne = sys.argv[1]
inputTwo = sys.argv[2]

for i in sys.argv[1:]:
    if '.mp3' in i:
        output = i.replace('mp3','mp4')

cmd = 'ffmpeg -loop_input -i "'+inputOne+'" -i "'+inputTwo+'" -shortest -acodec copy "'+output+'"'

os.system(cmd)


```

it'd be more or less as simple in bash, but i cant get bash syntax right off the top of my head

---

### Post by shantiq on 2011-10-06
looks brill aeiah   not sure how to use this tried to run it and 

since i do not understand the code it is probably my mistake put the script and mp3 and jpg in folder and ran  ```
./mp3plusjpg
```



and got

```
./mp3plusjpg
Traceback (most recent call last):
  File "./mp3plusjpg", line 5, in <module>
    inputOne = sys.argv[1]
IndexError: list index out of range
```

---

