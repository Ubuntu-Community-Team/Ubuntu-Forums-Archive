---
title: "convert FLAC to Nero AAC ?"
date: 2010-02-07
forum: Multimedia Software
---

### Post by lucasart on 2010-02-07
Hello

Does anyone know how to use neroaacencoder (in CLI) to convert a flac file to AAC ? Is it also possible to encode in WMA in Linux ?

Thank you

---

### Post by FakeOutdoorsman on 2010-02-07
> **lucasart said:**
> Hello

Does anyone know how to use neroaacencoder (in CLI) to convert a flac file to AAC ? Is it also possible to encode in WMA in Linux ?

Thank you

You can either pipe an input to neroAacEnc or convert the FLAC to a WAV and use that as an input.  Here's the most basic example of piping by using FFmpeg:
```
ffmpeg -i input.flac -f wav - | neroAacEnc -if - -ignorelength -of output.mp4
```
I'm unsure what output settings neroAacEnc uses by default, but you can find out more with *neroAacEnc -help*.

**Update:**  I forgot about the WMA question.  FFmpeg can be used for this too:
```
ffmpeg -i input.flac -acodec wmav2 -ab 192k output.wma
```

---

### Post by mc4man on 2010-02-07
You can also just use flac and pipe to nero, a simple command for single or batch converting. 
Nero uses -q settings and defaults to -q 0.5, that can be adjusted up or down. Firgure -q 0.375 is around 128k, over 0.75 is probably wasted.
( cd to a folder holding the .flac(s)

```
for f in *.flac; do flac -c -d "$f" - | neroAacEnc -if -  -q 0.65 -of  "${f%.flac}.m4a"; done
```

( not sure if the ignorelengh matters here.

Now this will not transfer tags, though that can be done later.
I've never used the nero tagger, but do use atomicparsley when ripping with either rubyripper or abcde to acc with nero. 
I guess it could be worked in.

I don't have time now but poosibly adapting this flac to mp3 w/ tags script I use would work (for batch, same name w/ tags
```

#!/bin/bash
echo "Name of folder to save mp3's in?"
N= read N

for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$f" - | lame --vbr-new -V 2  - "$OUTF"
id3v2 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"
done
mkdir "$N" && mv *.mp3 ./"$N"
```

so the beginning to change would maybe be this - need to work the tagger (atomic parsley..? ) in where the 1d3v2 line was

```
#!/bin/bash
echo "Name of folder to save m4a's in?"
N= read N

for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.m4a/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$f" - | neroAacEnc -if -  -q 0.65 -of  "$OUTF"
<tagging commands>
done
mkdir "$N" && mv *.m4a ./"$N"
```

---

### Post by lucasart on 2010-02-08
thanks, i'll do my own *.sh file with subdirectories etc. it's a god way to understand the CLI, I'm a Linux beginner, just converted myself away from windows :-)
i'll surely manage to find the stuff to add the tags to an *.mp4 file on internet somewhere.

---

### Post by lucasart on 2010-02-08
thanks! actually it's much simpler than i thought, especially wma encoding :) i was looking for a format that is better than lame mp3, and popular/compatible, hence wma/mp4

---

### Post by andrew.46 on 2010-05-10
Hi FakeOutDoorsman,

> **FakeOutdoorsman said:**
> I'm unsure what output settings neroAacEnc uses by default, but you can find out more with *neroAacEnc -help*.

I am coming perilously close to necroposting but I have just installed the newest version of nero AAC and in the docs there is a nice table for the '-q' settings, the *default* of course being 0.5:

```

The variable data rate quality settings result in the 
following average bitrates:
-------------------------------
**[COLOR="Black"]Quality     Bitrate (kbit/s)[/COLOR]**
-------------------------------
0.05             16 
-------------------------------
0.15             33
-------------------------------
0.25             66 
-------------------------------
0.35             100  
-------------------------------
0.45             146 
-------------------------------
0.55             192
-------------------------------
0.65             238
-------------------------------
0.75             285 
-------------------------------
0.85             332 
-------------------------------
0.95             381 
-------------------------------

```

Andrew

---

### Post by mc4man on 2010-05-10
> just installed the newest version of nero AAC and in the docs 
 Never noticed here any 'doc's', but *now that you've mentioned* do see a .pdf in the main folder.

---

### Post by andrew.46 on 2010-05-10
Hi mc4man,

> **mc4man said:**
> Never noticed here any 'doc's', but *now that you've mentioned* do see a .pdf in the main folder.

I will admit that I only noticed it when I was scavenging around [looking for the tagging application]("http://lists.slackbuilds.org/pipermail/slackbuilds-users/2010-May/005568.html") and then repackaging the new version + docs. The pdf is of course aimed fairly solidly at windows users but there is a little general information as well...

Andrew

---

### Post by mc4man on 2010-05-10
> when I was scavenging around looking for the tagging application and

Interesting - I'm assuming you've added  to use - have you been able to integrate it (neroAacTag) into a rip/encode/tag method?

---

### Post by andrew.46 on 2010-05-10
Hi mc4man,

> **mc4man said:**
> Interesting - I'm assuming you've added  to use - have you been able to integrate it (neroAacTag) into a rip/encode/tag method?

It is a busy time for me at the moment so I have not had much of a look at it yet. I have made a small note on one of my favourite pages:

[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

but I have not gone too much further than that, and certainly there are no great advantages using NeroAacEnc with such radio streams.... But I will certainly investigate, as I wrote on that page, 'while I should be doing other things..' :).

Andrew

---

### Post by FakeOutdoorsman on 2010-05-11
> **andrew.46 said:**
> Hi FakeOutDoorsman,



I am coming perilously close to necroposting but I have just installed the newest version of nero AAC and in the docs there is a nice table for the '-q' settings...

Nice find.  Next time I use neroAacEnc I'll throw away the bones and consult the table.

---

### Post by pnewman on 2010-07-11
In case it helps others, here's a couple of scripts I wrote, to transcode my library from flac to aac using neroAacEnc. It also copies all tags. Some tags are renamed, in line with the standard tag names shown by:
```
neroAacTag -list-standard-meta
```Per-file script: transcode.sh <flacFile>
```

#!/bin/bash

file="$1"
fileOut="${file%.flac}.m4a"
result=0

if [ -f "$fileOut" ]; then
  echo Already exists: "$fileOut"
  exit
else
  # Transcode from flac to aac
  flac -c -d "$file" - | neroAacEnc -if -  -q 0.5 -of  "$fileOut" >/dev/null 2>&1
  result=$?
  if [ $result -eq 0 ]; then
    echo Transcoded: "$file"
  else
    echo Error code $result on "$file"
    exit
  fi
fi

mungeTag()
{
# Converts tags created by Banshee in flac to those expected by neroAacTag
  case "$tagName" in
    "DATE")        tagName="year"; tagValue=${tagValue:0:4};;
    "TRACKNUMBER") tagName="track";;
    "TRACKTOTAL")  tagName="totaltracks";;
    "DISCNUMBER")  tagName="disc";;
    "DISCTOTAL")   tagName="totaldiscs";;
    *) tagName=`echo "$tagName" | tr '[:upper:]' '[:lower:]'`;;
  esac
}

# Copy the tags from source to destination file
IFS=$'\012' # separate on newlines, ignoring spaces
tags=`metaflac "$file" --export-tags-to=-`
count=0
for tag in $tags; do
  tagName=`echo "$tag" | cut -d "=" -f 1`
  tagValue=`echo "$tag" | cut -d "=" -f 2`
  mungeTag
  #echo $tagName="$tagValue"
  neroAacTag "$fileOut" -meta-user:"$tagName"="$tagValue" >/dev/null 2>&1
  ((count++))
done

echo $count tags written

```Script for all files below a directory: transcodeAll.sh <basePath>
```

#!/bin/bash

# Error codes
ARGUMENT_NOT_DIRECTORY=10

path="$1"
if [ ! -d "$path" ]; then
  echo "Path "$path" is not a directory"
  exit $ARGUMENT_NOT_DIRECTORY
fi

find "$path" -type f -name *.flac -exec ./transcode.sh '{}' \;

```

---

### Post by okmat on 2011-10-26
> **pnewman said:**
> In case it helps others, here's a couple of scripts I wrote, to transcode my library from flac to aac using neroAacEnc. It also copies all tags. Some tags are renamed, in line with the standard tag names shown by:

BIG Thanks!! it worked for me, just had to change a bit a line in the transcodeAll.sh file:

```
find "$path" -type f -name *.flac -exec ./transcode.sh '{}' \;
```

to

```
find "$path"*.flac -type f -exec transcode.sh '{}' \;
```

This works as long as the files transcode.sh and transcodeAll.sh, as well as neroAacEnc and neroAacTag are in /usr/bin directory with permissions to execute

---

