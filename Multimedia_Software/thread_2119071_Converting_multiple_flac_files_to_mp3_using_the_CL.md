---
title: "Converting multiple flac files to mp3 using the CLI"
date: 2013-02-22
forum: Multimedia Software
---

### Post by rmcellig on 2013-02-22
This is new territory for me. I previously relied on GUI apps to batch convert files from Flac to mp3 and wav and aiff to mp3.

How would I do this using ffmpeg?

I have several folders with aiff, flac and wav files that I want to convert to 192 bit mp3 format. I have a feeling using ffmpeg would be much faster and easier to use than a gui solution. The other reason is that I am determined to use the CLI for most of my tasks instead of always relying on a GUI solution. So far, I am really discovering the power of the CLI and I am really enjoying it (never thought I would say that in a million years :).

Thanks!!

---

### Post by varunendra on 2013-02-24
*Thread moved to **Multimedia & Video**.*
..and bumped :)

---

### Post by andrew.46 on 2013-02-24
Probably the easiest way is to use a *for* loop, but it depends what sort of directory structure you have in place. Are the files all lumped together or separated by type?

---

### Post by fdrake on 2013-02-24
> **rmcellig said:**
> This is new territory for me. I previously relied on GUI apps to batch convert files from Flac to mp3 and wav and aiff to mp3.

How would I do this using ffmpeg?

I have several folders with aiff, flac and wav files that I want to convert to 192 bit mp3 format. I have a feeling using ffmpeg would be much faster and easier to use than a gui solution. The other reason is that I am determined to use the CLI for most of my tasks instead of always relying on a GUI solution. So far, I am really discovering the power of the CLI and I am really enjoying it (never thought I would say that in a million years :).

Thanks!!
mp3 format losses quality when formating to it. Can you use ogg instead?

> 
mkdir /my_ogg_dir
for i in /my_Flac_dir/*.flac
do  
ffmpeg -i $i -strict experimental -acodec vorbis -aq 100 /my_ogg_dir/$i.ogg
done

see also : [http://ubuntuforums.org/showthread.php?t=1626645](http://ubuntuforums.org/showthread.php?t=1626645)

---

### Post by evilsoup on 2013-02-24
Ogg Vorbis is a lossy codec, just like MP3. Well, Vorbis is better than MP3 at a given bit rate - it's on par with AAC-LC - but that's only applicable to very low bit rates; for most people, using consumer audio equipment, most of the time all modern lossy audio encoders produce results indistinguishable from the original CD audio at around 128 kbit/s.

Vorbis is nowhere near as well supported as MP3 on hardware players. Also, the ffmpeg vorbis encoder is sub-par; you should use libvorbis instead.

```

ffmpeg -i input.flac -c:a libvorbis -q:a 5 output.ogg

```

To actually answer the OP question:

```

##  Encode a single file as an MP3:
ffmpeg -i input.flac -c:a libmp3lame -q:a 4 output.mp3

##  Encode a directory of FLAC files to MP3:
for f in *.flac; do ffmpeg "$f" -c:a libmp3lame -q:a 4 "${f/%flac/mp3}"; done

##  Create MP3s recursively (make sure you copy all the quotes):
find . -type f -name "*.flac" -exec bash -c 'ffmpeg -i "$0" -c:a libmp3lame -q:a 4 "${0/%flac/mp3}"' '{}' \;

```

See [this blog post](http://evilsoup.wordpress.com/2013/02/10/general-ffmpeg-encoding-guide-2/) for some basic information about encoding different formats; see [this page](https://ffmpeg.org/trac/ffmpeg/wiki/Encoding%20VBR%20%28Variable%20Bit%20Rate%29%20mp3%20audio) on the ffmpeg wiki for a bit more information on MP3 encoding (and [this HydrogenAudio](http://wiki.hydrogenaudio.org/index.php?title=Lame) page for some in-depth information).

---

### Post by shantiq on 2013-02-24
hi rm     this will do it if you cd to the folder where all your folder files are   say they are all in Music   do   ```
cd Music
```
nullglob means it does not stop if one of the formats listed is absent nocaseglob means it cares not if .mp3 or .MP3


> for i in */
do
 cd "$i"
for f in  nullglob nocaseglob  *.{flac,aiff,wav} ; do ffmpeg -i "$f"  -b:a 192k "${f%.*}.mp3" ; done
cd ..
done



if you want to remove original files **be careful here** :KS you can add   [test it first with lines above]


> for i in */
do
 cd "$i"
for f in  nullglob nocaseglob  *.{flac,aiff,wav} ; do ffmpeg -i "$f"  -b:a 192k "${f%.*}.mp3" ; done  \
 [COLOR="DarkRed"]&& rm *.{flac,aiff,wav}[/COLOR]
cd ..
done




**PS**   love your concise line Esoup

> find . -type f -name "*.flac" -exec bash -c 'ffmpeg -i "$0" -c:a libmp3lame -q:a 4 "${0/%flac/mp3}"' '{}' \;


how do you add wav and aiff to it?   [i tried to add those and messed up with find syntax]

---

### Post by evilsoup on 2013-02-24
I got that find line originally from [this superuser.com]("http://superuser.com/a/521526/180990") answer, so if you have an account there, give that guy an upvote.

I would use regular expressions for finding multiple file extensions, something like:

```

find . -type f -regextype posix-extended -regex ".*flac|.*wav|.*aiff" -exec bash -c 'ffmpeg -i "$0" -c:a libmp3lame -q:a 4 "${0%.*}.mp3"' '{}' \;

##  or (slightly more concise, easier to add more file extensions):
find . -type f -regextype posix-extended -regex ".*\.(flac|wav|aiff)" -exec bash -c 'ffmpeg -i "$0" -c:a libmp3lame -q:a 4 "${0%.*}.mp3"' '{}' \;

```You may have to escape the '|'s, unfortunately my linux computer has suffered physical damage & I'm stuck on Windows 8 til Tuesday, so I'm unable to test if this exact syntax works. Check out the find manpage, I guess. You can also use something like:

```

find . -type f -name "*.flac" -o -name "*.wav" -o -name "*.aiff" -exec bash -c 'ffmpeg -i "$0" -c:a libmp3lame -q:a 4 "${0/%flac/mp3}"' '{}' \;

```...but I prefer the regex way, since it's more concise.

You can also use '-iregex' instead of '-regex' (or '-iname' instead of '-name') to get case-insensitive matches - so it would match both 'whatever.wav' and 'whatever.WAV'

---

### Post by shantiq on 2013-02-24
thanx man   really good ; even goes into folders within folders [truly recursive]   way more elegant than my paltry earlier proposition
just noticed   -q:a 4   does not really hit 192k the asker requested so it seems more accurate to use -b:a 192k instead    what do you think ?  and then the **i**regex is a peach addition  ,   maybe can also trim -c:a libmp3lame   to make it even leaner  [all recent versions of ffmpeg ok that way]

this is very elegant  ....   shall be using from now on and ditching the old method


> find . -type f -regextype posix-extended -iregex ".*\.(flac|wav|aiff)" -exec bash -c 'ffmpeg -i "$0"  -b:a 192k "${0%.*}.mp3"' '{}' \;

---

### Post by evilsoup on 2013-02-24
Outside of specialized applications, VBR modes should be used for all video/audio encoding. '-q:a 4' will offer a very good level of audio transparency; using a lower value will get a higher bit rate (a value of 2 is equivalent - averaged over a large number of encoded files - to about 192 kbit/s), but I seriously doubt that anyone (outside of sound engineers with high-end equipment sitting in a recording studio & actively listening for artefacts... and even then...) will be able to tell the difference.

'-b:a 192k' will always get a bit rate of 192 kbit/s... but I think it would be pretty wasteful. Of course, hard drive space is pretty cheap, and it will subjectively sound as good as a VBR MP3 (again, to most people under most circumstances), so there's little real harm in doing so. I mostly recommend it because 'VBR=good' is a very good rule of thumb for delivery codecs, and is more important with video codecs, where hard drive space can still be an issue.

---

### Post by evilsoup on 2013-02-24
If yopu have a beefy multi-core machine, you may find some advantage in using gnu parallel Note: the parallel in the 12.04 repos is not gnu parallel (I don't know about 12.10 or above), get it from [here]("http://www.gnu.org/software/parallel/").

FFmpeg is multithreaded, so this probably won't give you a massive boost unless you have a very beefy machine (>4 cores), but...

```

find . -type f -name "*.flac" | parallel ffmpeg -i {} -c:a libmp3lame -q:a 4 {.}.mp3

```With GNU parallel, '{.}' is equivalent to bash '${f%.*}'. I don't think it's available in find -exec, hence the 'bash -c'.

Also, yes, the '-c:a libmp3lame' could be safely removed AFAICT.

EDIT: if any of the filenames contain newlines (should never happen...) you'll need to use this construction:

```

find . -type f -name "*.flac" -print0 | parallel -0 ffmpeg -i {} -c:a libmp3lame -q:a 4 {.}.mp3

```

---

### Post by andrew.46 on 2013-02-24
Unlikely to be all that useful but it might be worth using *-iname* instead of *-name* in the find syntax.

---

### Post by evilsoup on 2013-02-24
If you were to use that, the substitution "${0/%flac/mp3}" would have to become "${0%.*}.mp3", to cover both lower and upper cases.

---

