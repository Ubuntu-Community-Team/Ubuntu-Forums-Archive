---
title: "FLAC to mono mp3/vorbis"
date: 2014-01-14
forum: Multimedia Software
---

### Post by Yellow Pasque on 2014-01-14
I have a situation where I can only listen through one earbud of my mp3 player (Sansa Clip). Obviously, stereo files don't work well for that.

So I have .flac files that I want to re-encode in mono lossy format (preferably vorbis, but mp3 works). I tried ffmpeg (2.2.1) to encode to vorbis mono, but the Clip played them with horrible static sound even though they played fine on my home stereo.

This is the script I'm using (not worried about tags right now).
```
#!/bin/sh

for f in *.flac; do
  # give output correct extension
  #OUTF="${a[@]/%flac/mp3}"

  # get the tags
  #ARTIST=$(metaflac "$f" --show-tag=ARTIST | sed s/.*=//g)
  #TITLE=$(metaflac "$f" --show-tag=TITLE | sed s/.*=//g)
  #ALBUM=$(metaflac "$f" --show-tag=ALBUM | sed s/.*=//g)
  flac -c -d "$f" | lame -m m --preset extreme --noreplaygain - "$f"mono.mp3
done

```

I'll update this more when I have time tonight. I just wanted to see if anyone has done something similar.

---

### Post by FakeOutdoorsman on 2014-01-14
Please show your ffmpeg command and the complete ffmpeg console output.
Does oggenc also produce static in the Sansa Clip?
Is your script using lame working as expected?

---

### Post by shantiq on 2014-01-15
or [SIZE=1]**[SIZE=2][COLOR=#000000]Temüjin [/COLOR][/SIZE]**[/SIZE]you can use   this

[B]for mp3
[/B]
```
for f in *.flac; do sox "$f" -C 192 -c 1 "${f%.flac}.mp3" ;done



```


-c   for channel number   -C for bitrate

**for ogg**   [-C  here goes 1-10]

```
for f in *.flac; do sox "$f" -C 8 -c 1 "${f%.flac}.ogg" ;done




```



[B]if not yet installed sox
[/B]

> [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install sox libsox-fmt-all[/FONT][/COLOR][COLOR=#000000]

[/COLOR]


---

### Post by Yellow Pasque on 2014-01-15
@Outdoorsman: thanks for the idea about oggenc. It was much simpler than ffmpeg because it preserves tags and automatically renames the file.
```
oggenc --downmix -q 5 file.flac
```
I'm going to test the files on my mp3 player tonight. I'll let you know...

@shantiq: I'll keep sox in mind for easier mp3 processing if the oggenc files play static too.

---

### Post by Yellow Pasque on 2014-01-15
Oh, and Outdoorsman, I was using a fairly simple ffmpeg command, something like:
```
ffmpeg -i file -c 2 -ac libvorbis file.ogg
```
I don't have the exact error it kept spitting out, but for almost every file, it said something like: "stream 0:0 has 100 buffers waiting. Something may be wrong."

---

### Post by Yellow Pasque on 2014-01-15
Okay, so I just gave it a quick test and the oggenc files also play with static. I guess my Clip doesn't like mono vorbis files for some reason.. (stereo vorbis plays well).

---

### Post by FakeOutdoorsman on 2014-01-15
> **Temüjin said:**
> @Outdoorsman: thanks for the idea about oggenc. It was much simpler than ffmpeg because it preserves tags and automatically renames the file.
ffmpeg should preserve metadata (I'm not sure about the fake "ffmpeg" or avconv in the repository).

> **Temüjin said:**
> Okay, so I just gave it a quick test and the oggenc files also play with static. I guess my Clip doesn't like mono vorbis files for some reason.. (stereo vorbis plays well).
What version of Ubuntu are you using, or more specifically, what version of libvorbis are you using?

> **Temüjin said:**
> Okay, so I just gave it a quick test and the oggenc files also play with static. I guess my Clip doesn't like mono vorbis files for some reason.. (stereo vorbis plays well).
Another option would be to create a stereo file but with both channels in uhh... both channels. If that makes sense.

```
ffmpeg -i input -af "pan=stereo:c0<c0+c1:c1<c0+c1" -acodec libvorbis -qscale:a 4 -vcodec copy output.ogg
```

Libav does not support the [pan audio filter](http://ffmpeg.org/ffmpeg-filters.html#pan), so you'll have to use a real ffmpeg from FFmpeg (isn't it great that Ubuntu switched?). You can follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) or simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds). For the lazy/efficient:

```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
./ffmpeg -i input ...
```

---

### Post by Yellow Pasque on 2014-01-15
I'm actually using Debian sid(uction)
ffmpeg (not libav) 2.1.2  (from debmultimedia repo)
libvorbis 1.3.2-1.3
vorbis-tools 1.4.0

> ffmpeg should preserve metadata
Actually, I guess it did for the .oggs. 
It didn't autocomplete tags for mp3's, but I'll worry about tagging spcriptfu later. I just have the player shuffle through the whole library anyway (it's all upbeat working music and I don't have time to select specific artists/albums while I'm working).

---

### Post by FakeOutdoorsman on 2014-01-15
Attached are a mono and a mixed stereo sample (from a friend's band) from ffmpeg using libvorbis 1.3.3. If the mono works maybe a bug was fixed in libvorbis (but I doubt libvorbis is at fault), but if not then I think it is safe to blame the Sansa Clip.

---

### Post by Yellow Pasque on 2014-01-18
Thanks for the samples! The clip played your mono file just fine. There have only been a few commits to libvorbis for 1.3.3 and I don't see anything that looks even remotely related to my issue.

I'm thinking it may have something to do with my libflac? Investigation continues...

---

### Post by FakeOutdoorsman on 2014-01-18
If you provide a flac sample that results in the static I can encode it to try to reproduce the issue.

My ffmpeg commands were (input was mp3 in this case):
```
ffmpeg -i input.mp3 -ss 52 -to 1:21 -ac 1 -q:a 4 -c:a libvorbis mono.ogg
ffmpeg -i input.mp3 -ss 52 -to 1:21 -af "pan=stereo:c0<c0+c1:c1<c0+c1" -q:a 4 -c:a libvorbis mixed.ogg
```

---

### Post by Yellow Pasque on 2014-01-18
Well, I found a better solution... Rockbox firmware. It allows you to play in mono. So no reencoding my mp3's and I can play files in stereo if I want.

At any rate, thanks for the assistance.

---

### Post by robinofsussex on 2014-01-20
```


#!/bin/bash


# converts flac files to mp3 and converts spaces and tabs
# to underscores in the file names.

# people who put spaces in files names should be put in poorly supplied
# penal colonies along with pedos and terrorists.

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
for f in *.flac
do
  echo "  f  " $f
  u=`echo $f | sed 's/[         ]/_/g'`
  echo  u is $u remove all those stupid spaces in filenames
  cp $f $u
  t=`echo $u | sed 's/flac$/mp3/'`
  ls -l \'$u\'
  echo  dollar u: $u becomes dollar t: $t
  echo "PROCESSING: " avconv -i \'$f\' -f mp3 $t  
  avconv -analyzeduration 20000000 -i $u -qscale:a 0 -f mp3 output.mp3
  echo -------------------------- CONVERTED $f
  ls -l output.mp3
  mv output.mp3 $t 
  rm -rf $u
done
IFS=$SAVEIFS

```

This one converts flac to mp3 at VBR 0, and also removes annoying spaces in filenames.

---

### Post by Yellow Pasque on 2014-01-20
Thanks, but like I said, mono mp3's were playing fine and I prefer just to use lame. I also don't care about filespaces in names. Linux handles them just fine...

---

### Post by Yellow Pasque on 2014-01-22
Rockbox allows me to play opus. The opus files are a bit larger and opusenc defaults to full quality (10) whereas I was using 4 or 5 with oggenc. I'll play around with it some more this weekend and see if I can hear a difference between vorbis and opus when using comparable settings. I kind of doubt I'll be able to using earbuds, but I'll also test with home stereo equipment. I'm also going to looking at encode speed and file size. What will probably end up happening is that I'll use opus going forward but leave the current vorbis files in place.

So my final script looks like:
```
#!/bin/bash

for f in *.flac; do
  # give output correct extension
  OUTFILE=${f//.flac/.opus}
  
  # get the tags
  ARTIST=$(metaflac "$f" --show-tag=ARTIST | sed s/.*=//g)
  TITLE=$(metaflac "$f" --show-tag=TITLE | sed s/.*=//g)
  ALBUM=$(metaflac "$f" --show-tag=ALBUM | sed s/.*=//g)
  
  flac -c -d "$f" | opusenc --artist "$ARTIST" --title "$TITLE" --album "$ALBUM" - "$OUTFILE" 
done


```

---

