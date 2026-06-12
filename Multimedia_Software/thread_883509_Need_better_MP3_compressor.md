---
title: "Need better MP3 compressor"
date: 2008-08-08
forum: Multimedia Software
---

### Post by dileepm on 2008-08-08
Hi,I had to compress a couple of MP3s to my mobile so i did some querying in this forum and got suggested with a compressor called a2mp3 well that works fine for me but the size of the file after compression seems to be not really small,5.3 MB compressed to 4.1 MB.When i used to use windows i had better choice;ofcourse i can use it through WINE but i dont want to;i want to be **"100% Pure Ubuntu"**...:wink:

---

### Post by mcduck on 2008-08-08
Try Grip. Or Sound Converter if you already have the audio files on your computer.

Anyway, the file size is simply a result of the bit rate you use. HIgher bitrate will produce larger files, no matter what progtram you use to do the job. Also you haven't even mentioned what type the original file is, if you are recompressing already compressed files it's just normal that they won't get much smaller any more..

Or, you could just open any package management tool In Ubuntu and use the search to find all the available sound compressing tools.. ;)

---

### Post by mc4man on 2008-08-08
You could look here for grip and mp3, It's aimed for high quality, you'd just go the other way. For a mobile you could go with much lower quality settings.
read the longhelp for parameters or just try a higher -V # like 7- 9.

Maybe in the case of mobile you'd use a cbr at low bitrate (don't know , don't have one)
[http://ubuntuforums.org/showthread.php?p=5546268#post5546268](http://ubuntuforums.org/showthread.php?p=5546268#post5546268)

---

### Post by dileepm on 2008-08-08
Ya i know about the bitrate concept.Anyway thanks i will try them once...

---

### Post by Gadgetech on 2008-08-18
I wrote a script to resample mp3 files and rewrite the ID3 tags.  The script depends on lame and mid3v2 (part of the python-mutagen package).

To install them:
```
sudo apt-get install lame python-mutagen
```

The full instructions and the 2 scripts can be found on my blog at [http://linugadgetech.blogspot.com/2008/08/how-to-resample-mp3-audio-files-on.html]("http://linugadgetech.blogspot.com/2008/08/how-to-resample-mp3-audio-files-on.html").

To increase the compression more, find the line in the cptag script that says:
lame -V5 --vbr-new --resample 44.1 "$1" "resample/$1"

and change the number after the -V to a higher number (up to 9).  The number can range from 0-9 with 9 being the highest compression (lowest quality) and 0 being least compression (highest quality).

---

### Post by skag on 2010-04-29
ive seen a track that had 56kbps bitrate and the sound quality was as good as 192 or even 256... and the track was 4 minutes and only 1.86 MB... how did this track was compressed?:S

---

### Post by Chronon on 2010-04-29
A bit of thread necromancy.  But I will suggest that the codec was probably not mp3 -- possibly HE-AAC.

---

### Post by skag on 2010-04-29
dunno.... but i saw and stuck..... at codec it says mpeg 2 audio, layer 3(mp3) and below the bitrate is 56kbps -_-

---

### Post by Andrew_P on 2011-10-27
> **Chronon said:**
> A bit of thread necromancy ...

Necromancy?  What do think the purpose is for storing discussions on nonvolatile media for access via the Internet?  If you want ephemeral information, use the telephone. :roll:

---

### Post by coffeecat on 2011-10-27
> **Andrew_P said:**
> Necromancy?

Indeed.

Thread closed.

---

