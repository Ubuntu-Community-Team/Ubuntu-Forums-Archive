---
title: "scan folder and convert AAC to mp3?"
date: 2009-01-05
forum: Multimedia Software
---

### Post by nixie21 on 2009-01-05
Is there a way to scan /home/nixie21/music and find all aac files, convert them to mp3 and get rid of aac?

Thanks

---

### Post by amauk on 2009-01-05
**not tested**
(so you may want to do a dry run on a small selection of copies before hand)

open Gedit, paste the following in
save as aac2mp3.sh
in nautilus, right click on aac2mp3.sh
properties > permissions > check "allow executing as a program"

double click and say "run in terminal"

```
#! /bin/bash

export IFS=$'\n'

AAC_FILES=`find "/home/nixie21/music/" -type f -iname '*.aac'`

for AAC_FILE in $AAC_FILES
do
	NEW_NAME=`echo "$AAC_FILE" | sed 's/aac$/mp3/'`
	MV_AAC_TO=`echo "$AAC_FILE" | sed 's|/home/nixie21/music/|/home/nixie21/music/old_aac_files/|'`
	MV_DIR=`echo "$MV_AAC_TO" | grep -o '^/\{0,1\}\([^/][^/]*/\)*'`

	ffmpeg -i "$AAC_FILE" "$NEW_NAME"

	mkdir -p "$MV_DIR"
	mv "$AAC_FILE" "$MV_AAC_TO"
done

export IFS=$' \t\n'
```

---

### Post by nixie21 on 2009-01-05
Thanks, will try later...curious, which commande does the actual aac to mp3 conversion?

---

### Post by amauk on 2009-01-05
ffmpeg -i "$AAC_FILE" "$NEW_NAME"

---

### Post by rodeh on 2012-08-27
leaving this here in case anyone is still looking, like I was:

Amauk's script didn't work for me, it resulted in 0 size files. Fixed by adding "-acodec copy" to the ffmpeg command, thusly:

changing
```
    ffmpeg -i "$AAC_FILE"  "$NEW_NAME"
```to:

```
    ffmpeg -i "$AAC_FILE" -acodec copy "$NEW_NAME"
```so the whole thing looks like this:


```

#! /bin/bash  

export IFS=$'\n'

AAC_FILES=`find "/home/USER/DIRECTORY/" -type f -iname '*.aac'`

for AAC_FILE in $AAC_FILES 
do

        NEW_NAME=`echo "$AAC_FILE" | sed 's/aac$/mp3/'`
        MV_AAC_TO=`echo "$AAC_FILE" | sed 's|/home/USER/DIRECTORY/|/home/USER/DIRECTORY/old_aac_files/|'`
        MV_DIR=`echo "$MV_AAC_TO" | grep -o '^/\{0,1\}\([^/][^/]*/\)*'`

        ffmpeg -i "$AAC_FILE" -acodec copy "$NEW_NAME"

        mkdir -p "$MV_DIR"
        mv "$AAC_FILE" "$MV_AAC_TO"
done 

export IFS=$' \t\n'

```follow the rest of the instructions:

Open Gedit, copy/paste in code

Make sure you've edited the /home/USER/DIRECTORY/ to where your files are and where you want them to go.

save as aac2mp3.sh

then in nautilus, right click on aac2mp3.sh

select properties > permissions > check "allow executing as a program"

double click and select "run in terminal"



whammo! worked for me.

Thanks Amauk for doing the difficult bit! ):P

---

### Post by shantiq on 2012-08-28
> **nixie21 said:**
> Is there a way to scan /home/nixie21/music and find all aac files, convert them to mp3 and get rid of aac?

Thanks





open terminal and copy as one block the following:

> cd /home/nixie21/music &&  for f in *.aac; do ffmpeg -i "$f" -acodec libmp3lame -ab [COLOR="DarkRed"]**192k**[/COLOR] "${f%.*aac}.mp3"; done && rm *.aac &&

for i in */
do
cd "$i"
for f in *.aac; do ffmpeg -i "$f" -acodec libmp3lame -ab [COLOR="DarkRed"]**192k**[/COLOR] "${f%.*aac}.mp3"; done && rm *.aac
cd ..
done


i set it to 192k but of course you can pick 128,256,320 
up to you

the first line takes care of the loose tracks && the for i... section takes care of the ones in folders

---

### Post by FakeOutdoorsman on 2012-08-28
> **shantiq said:**
> open terminal and copy as one block the following:

shantiq's solution is the best so far as it actually re-encodes the audio to MP3 instead of copying the AAC stream.

```
cd /home/nixie21/music && for f in *.aac; do ffmpeg -i "$f" -ab 192k "${f%.*aac}.mp3"; done && rm *.aac &&

for i in */
do
cd "$i"
for f in *.aac; do ffmpeg -i "$f" -ab 192k "${f%.*aac}.mp3"; done && rm *.aac
cd ..
done 
```
I recommend adding *-acodec libmp3lame* as an output option; otherwise ffmpeg may use the MP2 audio encoder if libmp3lame is unavailable, IIRC, but will fail with error if libmp3lame is unavailable.

> **shantiq said:**
> i set it to 192k but of course you can pick 128,256,320 
up to you
Another option is to replace *-ab 192k* with *-aq 4* for VBR.

---

### Post by shantiq on 2012-08-28
thanx Fake will update this

i also remembered only in the last few versions does ffmpeg KNOW to encode to mp3 without using -acodec so to add that extra info will cover all bases since i do not know which ubuntu version the asker currently uses

---

