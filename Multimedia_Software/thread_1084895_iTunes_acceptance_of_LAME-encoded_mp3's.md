---
title: "iTunes acceptance of LAME-encoded mp3's"
date: 2009-03-02
forum: Multimedia Software
---

### Post by squishywalrus on 2009-03-02
Alright, so a little background.  I have a rather large CD collection at my parents house, but as I move around alot (still a student), I digitized the whole thing to flac, and keep the flacs on my desktop.  Now, I recently purchased an iPhone, and need to transcode my flacs to mp3 (for reasons of acceptance with iTunes, and to save space on the device).  In summary:  I have valid lisences for all of my music, its just quite inconvenient to access the physical cd's as opposed to my flac rips.

SO, I attempted to transcode them by calling the following command in a script:

"flac -dc example.flac | lame --preset standard - - > example.mp3"

to transcode each of the files, and though the resulting mp3's play fine in ubuntu, when I copy them to a macbook to transfer to the iPhone and import into iTunes, iTunes ignores (and seems to delete) all of the trancoded files on import.  Is there something about lame's standard preset that iTunes doesn't like?  Has anyone else had similar troubles?

thanks,
nick

---

### Post by punx45 on 2009-03-02
Audacity uses LAME to encode MP3s and everything i have created that way works with itunes.  

do you know what the preset standard is?   my suggestion would be to find out what that is, and then search the apple support and discussion forums for issues with those.

---

### Post by mc4man on 2009-03-02
> Is there something about lame's standard preset that iTunes doesn't like?

I'm not sure about that though I can't imgine why it would.
 I've had no trouble with  some different lame paramters, so the problem may be the mac version of itunes or your method of converting (I've tested with the win version of itunes, though normally I'll use amarok to add albums.

I just batch convert an album from flac to mp3, tranfering the 'tags' at the same time.
The main difference between amarok and itunes is for itunes I need to rename the folder the mp3's are transferred to to the album name, in amarok I can leave it as is (temp)

If you want to try, the script is below, what's marked in blue is where the lame parameters go, you can use any valid lame ones (see lame --longhelp

You need to install or have installed id3

Basically I just use nautilus-open-terminal to open the album folder at a terminal prompt and just point it to the script. (if the script is in home folder, then ~/scriptname
```
sudo apt-get install nautilus-open-terminal
```

Then Ctrl+backspace to enable

Ex.
> doug@doug-desktop:/media/MUSIC/flac/Pink Floyd (1974) The Dark Side Of The Moon$ ~/convertflac
```

#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$f" | lame -[COLOR="Blue"]-replaygain-accurate -q 0 --vbr-new -V 3[/COLOR] - "$OUTF"
id3 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"
done
mkdir temp
mv *.mp3 ./temp
```

screen shows ipod, just added pink floyd in itunes, garcia in amarok, no problems

Or just try installing soundconverter or soundkonverter, both have several lame setting and will 'tag'

---

