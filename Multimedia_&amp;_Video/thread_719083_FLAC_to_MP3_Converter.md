---
title: "FLAC to MP3 Converter"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by holdie on 2008-03-08
Hey everybody, I'm trying to find a program that will easily convert my FLAC files to MP3 (V0, V2, etc)...I tried soundconverter, but it's not communicating well with LAME apparently and is resulting in a bunch of 128 kbs files...

any ideas?

---

### Post by MetalMusicAddict on 2008-03-08
Here's a script I use. I just cd into the dir and run the script. Change the stuff in [COLOR="Red"]red[/COLOR] to fit you.

```
#!/bin/sh

for a in *.flac
do
       OUTF=`echo "$a" | sed s/"\.flac$"/"\.mp3"/g`

       ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
       TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
       ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
       GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
       TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
       DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

       flac -c -d "$a" | lame [COLOR="Red"]-V 3 --vbr-new[/COLOR] - "$OUTF"
       id3v2 [COLOR="Red"]-t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE"[/COLOR] "$OUTF"
done

#  mkdir "$ARTIST" && mkdir "$ARTIST"/"$ALBUM"
#  mv *.mp3 "$ARTIST"/"$ALBUM"/.
#  cp *.png "$ARTIST"/"$ALBUM"/.
#  tar -cvf "$ARTIST - $ALBUM"-MP3.tar "$ARTIST"/"$ALBUM"/*.mp3 "$ARTIST"/"$ALBUM"/cover.png
#  rm -fr "$ARTIST"
#  mv *.tar ~/
```

I commented out the stuff thats specific to me but you might find useful. This script has actually grown quite a bit (I can go to multiple formats) but should get you started.

Depends on the flac, lame and id3v2 packages.

---

### Post by yabbadabbadont on 2008-03-08
Here are a couple of scripts that I have found for this.  One is a perl script and the other bash.  (I've only tested the bash version)

---

### Post by wolfen69 on 2008-03-08
> I'm trying to find a program that will ***easily*** convert my FLAC files to MP3
you could just install sound converter. it is in synaptic. works great for me. and it's easy. (drag and drop)

---

### Post by holdie on 2008-03-09
I downloaded that bash converter you suggested and it worked perfectly....people like you guys make me want to take a semester off of college so I can learn to do more with linux other than relatively simple command line stuff

thanks very much

---

### Post by disturbedite on 2008-03-09
if you convert to mp3 from you'll be throwing away quality, not recommended, unless you absolutely have to.

i use soundkonverter for my conversions tho.
(i don't convert from lossless (like flac) to lossy (like mp3) tho)...

---

### Post by yabbadabbadont on 2008-03-09
> **disturbedite said:**
> if you convert to mp3 from you'll be throwing away quality, not recommended, unless you absolutely have to.

i use soundkonverter for my conversions tho.
(i don't convert from lossless (like flac) to lossy (like mp3) tho...

The OP didn't say, but I would imagine that they wanted to convert in order to transfer music to a portable player.  That's why I had both scripts handy.

---

### Post by disturbedite on 2008-03-10
> **yabbadabbadont said:**
> The OP didn't say, but I would imagine that they wanted to convert in order to transfer music to a portable player.  That's why I had both scripts handy.
i know, when i said "unless you absolutely have to", its cuz most of the time that ppl have to, it is for portable media players.

but good idea to cover all the bases.

---

### Post by dotdot on 2008-04-21
cheers pal... who needs gui when you have cli.

ttfn

---

### Post by disturbedite on 2008-04-21
> **dotdot said:**
> cheers pal... who needs gui when you have cli.

ttfn
windoze users.  :lolflag:

---

