---
title: "script to convert M4A to MP3 with tags"
date: 2010-06-22
forum: Multimedia Software
---

### Post by ginjabunny on 2010-06-22
LATE BREAKING NEWS: see my post #5 further down the page, I found "pacpl (Perl Audio Converter)" which does all this so much better, it is in the Ubuntu repository. You can still use (or alter) mine if you like.
- - - - - - - - - - - - - - - - - - - - 

I am no expert on scripting but have been meaning to do this for years, so just spent 3 days writing this (not that good with bash script), this is quite basic and seems to work, could probably do with more error checking so feel free to add to it.

Basically, it dumps the tag info from the m4a into a file then reads it into some variables, then converts the file using faad and directly pipes it into lame, then adds the tags to the mp3, seems to work, comment out the last 4 lines if you want to keep the original m4a, or ensure you have a backup.

To get prerequisites run 
```
sudo apt-get install faad id3v2 lame
``` 

copy code below into faad2mp3.sh in your home folder, then chmod +x faad2mp3.sh 
```
#!/bin/bash
# you need to cd to the dir where the your sub-dirs/files are
# and then run - find -name '*.m4a' -exec ~/faad2mp3.sh "{}" ";"
# required - sudo apt-get install faad id3v2 lame
m4afile="$@"
mp3file="${m4afile%.m4a}.mp3" 	
rm /tmp/mp4info
echo "- - - - - - - - - - - - - - - - - - - - - - - - - - - -"
echo "Processing: $m4afile"
echo "Extracting tags..."
faad -i "$m4afile" 2>  /tmp/mp4info
artist=`grep "artist: " /tmp/mp4info | sed -e "s/artist: //g"`
album=`grep "album: "   /tmp/mp4info | sed -e "s/album: //g"`
title=`grep "title: "   /tmp/mp4info | sed -e "s/title: //g"`
year=`grep "date: "     /tmp/mp4info | sed -e "s/date: //g"`
track=`grep "track: "   /tmp/mp4info | sed -e "s/track: //g"`
genre=`grep "genre: "   /tmp/mp4info | sed -e "s/genre: //g"`
echo "Tags: artist=$artist album=$album track=$track title=$title year=$year" 
echo "Converting to mp3..." 
faad -q -o - "$m4afile" | lame -S - "$mp3file" 
echo "Adding tags..." 
id3v2 -a "$artist" -A "$album" -t "$title" -T "$track" -y "$year" "$mp3file"  
if [ -f "$mp3file" ]; then
  rm "$m4afile"
  echo "Deleted: $m4afile"
fi
```

To run it, cd into the dir which contains all the sub-dirs/files you want to convert then run
```
find -name '*.m4a' -exec ~/faad2mp3.sh "{}" ";"
```

(updated: I changed it so the script only needs to be in your home folder)

---

### Post by ginjabunny on 2010-06-22
BTW it takes about 20 seconds to do a 4 minute track on my old Sempron 3400.

Any comments are most welcome

---

### Post by ron999 on 2010-06-22
Posted in error, sorry.

---

### Post by ron999 on 2010-06-22
Hi
I'm running the script now.
But it's running very slowly on my machine.
Maybe the faad decoder is slow, or maybe the lame quality settings are too high for my computer.
Your script seems to work.
Artist, album, title, track, and year tags are OK.
The script doesn't seem to set the  genre tag.

By the way, SoundConverter converts from m4a to mp3 OK and keeps the tags.

Keep up the good work.
:guitar:

---

### Post by ginjabunny on 2010-06-23
Good news, I found something miles better than my script, it's well hidden in Synaptic and it's called pacpl (Perl Audio Converter) and does lots of formats and preserves tags, and it is fast.

I just tried it, I have a folder with mixed mp3 and m4a, it will convert the m4a to mp3 with tags and if it finds any non-m4a files it just copies them, or you can get it to convert in place. There are so many options, and you can even change the en/decoders it uses if you want.

Obviously written by someone which knows what they are doing (so thanks to Philip Lyons)

---

### Post by josejuan05 on 2011-02-09
I found a script like this a few years ago and have been slowly modifying it as I see fit. This is what I've got so far. I believe that it copies most of the fields present in iTunes purchases, but some of the tags might not map precisely to the correct id3v2 field.

```
#!/bin/bash
if ! which faad >/dev/null; then echo "faad executable not found." >&2; exit 1;fi
if ! which metaflac >/dev/null; then echo "metaflac executable not found." >&2; exit 1;fi
if ! which lame >/dev/null; then echo "lame executable not found." >&2; exit 1;fi
if ! which id3v2 >/dev/null; then echo "id3v2 executable not found." >&2; exit 1;fi

for m4afile in *.m4a
do
mp3file=$(echo "$m4afile" | sed s/\.m4a/.mp3/g)

ARTIST=$(faad -i "$m4afile" 2>&1 | grep '^artist: ' | sed 's/^artist: //')
TITLE=$(faad -i "$m4afile" 2>&1 | grep '^title: ' | sed 's/^title: //')
ALBUM=$(faad -i "$m4afile" 2>&1 | grep '^album: ' | sed 's/^album: //')
GENRE=$(faad -i "$m4afile" 2>&1 | grep '^genre: ' | sed 's/^genre: //')
TRACKNUMBER=$(faad -i "$m4afile" 2>&1 | grep '^track: ' | sed 's/^track: //')
DATE=$(faad -i "$m4afile" 2>&1 | grep '^date: ' | sed 's/^date: //')
COMMENT=$(faad -i "$m4afile" 2>&1 | grep '^comment: ' | sed 's/^comment: //')
CONGROUP=$(faad -i "$m4afile" 2>&1 | grep '^contentgroup: ' | sed 's/^contentgroup: //')
COMPOSER=$(faad -i "$m4afile" 2>&1 | grep '^writer: ' | sed 's/^writer: //')
PERFORMER=$(faad -i "$m4afile" 2>&1 | grep '^performer: ' | sed 's/^performer: //')
ALBARTIST=$(faad -i "$m4afile" 2>&1 | grep '^album_artist: ' | sed 's/^album_artist: //')

echo "$m4afile -> $mp3file"
faad -q -o - "$m4afile" 2>/dev/null | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$mp3file" 2>/dev/null

echo -e "$ARTIST / $ALBUM [$DATE] / $TRACKNUMBER - $TITLE"
id3v2 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" -c "$COMMENT" --TORY "$DATE" --IPLS "$ALBARTIST" --TCOM "$COMPOSER" --TIT1 "$CONGROUP" --TIT2 "$TITLE" --TOPE "$PERFORMER" --TPE1 "$ARTIST" --TPE2 "$ALBARTIST" --TRCK "$TRACKNUMBER" "$mp3file" 2>/dev/null
done
echo "Conversion complete!"
```

I named the script 'm4a2mp3' and made it executable:
```
chmod +x m4a2mp3
```

I use [Dropbox]("https://www.dropbox.com/referrals/NTQ0MDg5NzM5") on my computers, so I have a folder of userscripts that I keep in ~/Dropbox/scripts. I copied 'm4a2mp3' to that folder, and I have the following lines at the end of my '~/.bashrc' file:
```
PATH=$PATH:~/Dropbox/scripts/
export PATH
```

Then all I have to do to run the command is to cd into the directory where the m4a files are and run 'm4a2mp3'. I could modify it to use the 'find' command as ginjabunny does. Already I see a couple of steps to improve my code.

---

