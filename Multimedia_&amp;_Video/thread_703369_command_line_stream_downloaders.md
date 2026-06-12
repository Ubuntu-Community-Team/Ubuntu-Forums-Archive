---
title: "command line stream downloaders"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by pedrotuga on 2008-02-21
Hey there.
I want to download some files from some tv and radio stations website so i can listen/view them in my portable player.

I remember there was a command line tool to do that, But i can't remember the name of the damn thing.

IT is possible to download streams using mplayer like this

```
mplayer -streamdump rstp://url.to/stream -streamfile whatever.rm
```

This works but sometimes the url poins to a files that has another url inside it which is pretty anoying as I have to manualy open it and copy it to the command line.

i think ffmpeg also allows similar rocedure, if anybody is familiar with it please post a snippet

Then there is miims which i haven't try and that damn other command line tool i cant remember the name of. Something with four leters...

I want to downlaod both video and audio, mostly wma and rm formats.

If anybody has more tips on stream download using text console, please repply

---

### Post by andrew.46 on 2008-02-22
Hi,

 I have had more experience with streaming audio than video so I can suggest a better syntax for audio:

```
$ mplayer -playlist <url> -ao pcm:file=filename.wav -vc null -vo null
```

 This leaves a big wav file to be converted to mp3 or ogg. This is a command line I have used a lot over the last 12 months and it *almost* always works well :-)

    Andrew

---

### Post by pedrotuga on 2008-02-24
thank you
that's useful indeed!

Other methods are still wellcome

---

### Post by lambono on 2008-02-26
If you save the stream with the following command 
```

mplayer -dumpstream -playlist $STREAMADDRESS -dumpfile "$SHOWNAME".dump -vc dummy -vo null &

```

You could then convert it to mp3 as follows 

```

mkfifo $RECORDINGNAME.pipe

lame -h -v -b 64 --tt $SHOWNAME --ta "Artist" --tl "${STATIONNAME}" --ty "2008" $RECORDINGNAME.pipe" "$RECORDINGNAME".mp3 & mplayer -vc dummy -vo null -ao pcm:file="$RECORDINGNAME.pipe" "$RECORDINGNAME".dump

rm $RECORDINGNAME.pipe
rm $RECORDINGNAME.dump


```

Using this pipe method might be better as you will not have to create a huge wav file.

---

