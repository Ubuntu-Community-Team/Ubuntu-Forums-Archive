---
title: "conversion of audio files to new folder"
date: 2013-12-15
forum: Multimedia Software
---

### Post by arapaho on 2013-12-15
```
for f in *.ogg; do ffmpeg -i "$f" -ab 128k "${f%.ogg}.mp3"; done
```
I need to convert files to a new path. I found the above command but I don't where to place path to destination folder.
In need to do it in terminal, that's why I don't want to use GUI program.

---

### Post by ajgreeny on 2013-12-15
It might be easier to convert with avconv then move the mp3 file you made.
```
avconv -i *.ogg -acodec libmp3lame -aq 5 output.mp3 && mv output.mp3 /full/path/to/output.mp3
```
If you have many files I presume you can edit the command to do what your original command did with them all, but I admit my bash skills are not really up to telling you how to do that.

---

### Post by andrew.46 on 2013-12-15
It is a little aside to your query but perhaps you could experiment a little with *-q:a x* settings as [described here...]("https://trac.ffmpeg.org/wiki/Encoding%20VBR%20%28Variable%20Bit%20Rate%29%20mp3%20audio")

---

### Post by ajgreeny on 2013-12-16
A second thought on this.

If you run the ffmpeg or avconv command from the destination folder and use the full pathway to the files you are converting the output files will be in the folder where you ran the command, so this should kill the two birds with the one command.

---

### Post by Yellow Pasque on 2013-12-16
Why are you doing lossy -> lossy conversion?

---

### Post by mc4man on 2013-12-16
Only in regards to question - 
just put the path in front of "${f%.ogg}.mp3" 

You can either full path to folder desired or use 
./  # target folder is inside current folder
../ # target folder is 1 directory up
../../ # target folder is 2 directories up 

ex. - files to convert are in ~/Music, want to send to folder in Music named mp3
At the ~/Music$ prompt  (red is your username
for f in *.ogg; do ffmpeg -i "$f" -ab 128k  /home/[COLOR="#FF0000"]doug[/COLOR]/Music/mp3/"${f%.ogg}.mp3"; done
or
for f in *.ogg; do ffmpeg -i "$f" -ab 128k ./mp3/"${f%.ogg}.mp3"; done

ex. files are in ~/Music, want to send to folder in home named mp3
At the ~/Music$ prompt
for f in *.ogg; do ffmpeg -i "$f" -ab 128k ../mp3/"${f%.ogg}.mp3"; done

ect., ect., easy to figure out, just make sure your target folder exists

---

### Post by ajgreeny on 2013-12-16
> Why are you doing lossy -> lossy conversion? 						
Probably for the same reason I do occasionally; I have an mp3 player that will not play .ogg files, so no other option.

---

