---
title: "converting flac files to mp3 results in 0.047 seconds silence in beginning"
date: 2012-02-18
forum: Multimedia Software
---

### Post by nickleus on 2012-02-18
i've exported some flac files from hydrogen 0.9.6-svn-exported. when i run the following command in the terminal:
```
for f in *.flac;do flac -cd "$f"|lame -h - "${f%.flac}.mp3";done
```

the resulting mp3 files all have 0.047 seconds of silence at the beginning of the file. anybody else experience this or know what i could possibly be doing wrong?

flac file info:
sample rate: 48000 Hz
bitrate: 1676 kbps

resulting mp3 file info:
codec: MPEG 1 audio, layer 3 (mp3)
sample rate: 48000 Hz
bitrate: 128 kbps

flac version: 1.2.1
lame version: 3.98.4 64bits

i've attached a sample flac source file, plus the resulting mp3

this appears to be a "lame" bug because converting from both flac and wav results in mp3 files with the 47 milliseconds of silence in the beginning.

when i try convert a flac to mp3 using sox (which uses libsox-fmt-mp3 14.3.2-1ubuntu1):
```
sox input.flac output.mp3
```

i get 0.023 seconds of silence in the beginning of the mp3 file instead of 0.047.

---

### Post by Chronon on 2012-02-18
MP3 isn't natively gapless.  You have to tell LAME to write header information for specific sequence of files.  Maybe you are seeing something related to that.  I don't see any --nogap/--nogaptags switches in your command.

---

### Post by nickleus on 2012-02-22
> **Chronon said:**
> MP3 isn't natively gapless.

i've never experienced this before, so i am thinking this must be the result of some ~recent change.

> **Chronon said:**
> I don't see any --nogap/--nogaptags switches in your command.

from the lame man page:
> --nogap file1 file2 ...
              gapless encoding for a set of contiguous files

```
lame -h --nogap *.wav
```

still produces the beginning silence.

with nogaptags (not in the man page, but visible with "lame --longhelp"):
```
lame -h --nogaptags --nogap *.wav
```

creates an even longer silence/delay in the beginning.

---

### Post by nickleus on 2012-02-25
the problem was pulseaudio:
[http://sourceforge.net/mailarchive/forum.php?thread_name=20120224084621.674dc3cc%40orgis.org&forum_name=lame-dev](http://sourceforge.net/mailarchive/forum.php?thread_name=20120224084621.674dc3cc%40orgis.org&forum_name=lame-dev)

when played with ALSA only, and not ALSA running under pulse, then it loops correctly. the silence was apparently expected/default behavior when encoding to mp3.

---

