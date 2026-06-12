---
title: "mpg123 stream multiple files"
date: 2009-09-11
forum: Multimedia Software
---

### Post by worty on 2009-09-11
Hi All,

I have a simple bash script I use to stream mp3s from my home machine. I am wondering if there is a way to continuously stream multiple mp3s. 

For example, I can do something like:
```
cat file1.mp3 | mpg123 -   
```
and it works fine.

Is there a way to get something like
```
cat file1.mp3 file2.mp3 | mpg123 - 
```
to work?

What happens when I do that is that mpg123 plays the first file just fine but then pauses indefinitely without playing the second file. 

Any help with this would be appreciated!

---

### Post by lloyd_b on 2009-09-11
Why are you even messing with the "cat"?  mpg123 is capable of accepting multiple files from the command line:```
mpg123 file1.mpg file2.mpg file3.mpg ...
```

Assuming that won't work for you, then you can use a bash script with a loop as an alternative:```
#!/bin/bash
FILES=file1.mpg file2.mpg file3.mpg
for FILE in $FILES; do
    cat $FILE > mpg123 -
done
```which will loop through all of the entries in FILES and play them one at a time (note: this will break if there are spaces in the filenames!).

Lloyd B.

---

### Post by worty on 2009-09-12
Sorry, should have made myself clearer. I am trying to stream over ssh. The mp3s are located at home and I'd like to stream them over ssh. I know that there are probably other ways of doing it but I'm interested in doing it over th cmd line.

---

### Post by rob-ward on 2009-09-12
This may not be appopriate for what you want but have you tried SSHFS, this wil allow you to essecially mount your home computers file system over SSH, that way you can use any local media player to play them back in any order you like

You should be able to use a commandline like this(out of memory)

sshfs rob@robserver:/home/rob /mnt/myserver

sshfs supports all of the standard ssh stoff like specifying ports(usefull for getting round peoples port blocks :-) )

---

### Post by worty on 2009-09-12
Thanks! Although it doesn't solve the problem the way I was hoping, it works just as well :D

---

### Post by rob-ward on 2009-09-12
Glad it works for you, don't know what I would do without ssh and sshfs.

---

### Post by sobukus on 2010-02-14
I wonder why the initial attempt does not work for you. It works fine for me using mpg123 1.10.0:

shell$ cat /data/thorma/var/music/metallica/kill_em_all/*.mp3 | mpg123 -t -
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	version 1.10.0; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes

Playing MPEG stream 1 of 1: - ...
Title:   hit the lights                  Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
MPEG 1.0 layer III, VBR, 44100 Hz joint-stereo
Title:   the four horsemen               Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   motorbreath                     Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   jump in the fire                Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   (anesthesia) - pulling teeth    Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   whiplash                        Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   phantom lord                    Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   no remorse                      Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   seek & destroy                  Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock
Title:   metal militia                   Artist: metallica
Comment: 1.633592                        Album:  kill em all
Year:    0                               Genre:  Rock

[51:20] Decoding of - finished.

If that really does not play for you, then please consider making a bug report for mpg123.

---

