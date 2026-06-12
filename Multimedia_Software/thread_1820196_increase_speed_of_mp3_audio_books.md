---
title: "increase speed of mp3 audio books"
date: 2011-08-07
forum: Multimedia Software
---

### Post by iconoclast hero on 2011-08-07
When I was using rockbox on an iPod mini, I was able to increase the playback speed.  When it did this, it also lowered the pitch so that it sounded like a person (please no chipmunk jokes).  I was playing with audacity and was able to get it to put out an acceptable file @ 1.4x speed.  I was wondering if there was a way to do this via CLI so that I could automate this process...  some audio books are lengthy and I don't want to negate the time I save per audio book by having to do this all manually.  :)

Any thoughts?

Thanks...

---

### Post by FakeOutdoorsman on 2011-08-07
Have you tried SoX?
```
ffmpeg -i in.mp3 -f wav - | sox -t s16 - -t wav - tempo 1.5 | lame -V5 - out.mp3
```
If you [compile SoX with mp3 support](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8) you could shorten this command (I'm not sure of the current status of mp3 support in the repo SoX).

---

### Post by iconoclast hero on 2011-08-07
> **FakeOutdoorsman said:**
> Have you tried SoX?
```
ffmpeg -i in.mp3 -t wav - | sox -t s16 - -t wav - tempo 1.5 | lame -V5 - out.mp3
```If you [compile SoX with mp3 support]("http://ubuntuforums.org/showpost.php?p=9859875&postcount=8") you could shorten this command (I'm not sure of the current status of mp3 support in the repo SoX).

If I went in with a low bit-rate mono mp3 could i go out with a wav?  I like the codec I use for converting from wav to mp3...  It looks like if I leave the command after the last | out, it will put out a wav, correct?

---

### Post by FakeOutdoorsman on 2011-08-07
> **iconoclast hero said:**
> If I went in with a low bit-rate mono mp3 could i go out with a wav?
Yes, you can do that. See the example below.
> **iconoclast hero said:**
> I like the codec I use for converting from wav to mp3...
What is this codec? I don't know anything better than LAME for mp3 encoding.
> **iconoclast hero said:**
> It looks like if I leave the command after the last | out, it will put out a wav, correct?
Not quite, but it can be modified to do that:
```
ffmpeg -i in.mp3 -f wav - | sox -t s16 - out.wav tempo 1.5
```
Although the beauty of using pipes lets you go from program to program so you don't have to deal with intermediate files.

---

### Post by AlphaLexman on 2011-08-07
'vlc' can adjust the playback speed without writing to disk.

---

### Post by FakeOutdoorsman on 2011-08-07
So can mplayer:
```
mplayer -af scaletempo -speed 1.5 input.mp3
```

---

### Post by iconoclast hero on 2011-08-07
> **FakeOutdoorsman said:**
> Yes, you can do that. See the example below.

What is this codec? I don't know anything better than LAME for mp3 encoding.

Not quite, but it can be modified to do that:
```
ffmpeg -i in.mp3 -t wav - | sox -t s16 - out.wav tempo 1.5
```Although the beauty of using pipes lets you go from program to program so you don't have to deal with intermediate files.

Ok, first, since you asked about the codec.  It is:
```

*       Fraunhofer IIS MP3 Surround Commandline Encoder V1.5       *
*                                                                  *
*                                                                  *
*           Encoder-Library V04.01.01 (build 2008-05-02)    
```
I don't want to get into a debate about LAME vs. IIS vs. speax, let's just say that I'm very happy with the size of low-quality audio book encoding with the IIS encoder and don't feel like screwing around with LAME since I already have this one optimized to my liking and have been using it for years.  When I've played around with LAME in the past, I could not get it to spit out a ca. 11 MB mono for a whole CD.

I'm thinking I could also | the new example command to something like the one I use now:

```
mp3sEncoder -if "$fn" -of "$n".mp3 -br 24000
```

...but I will give sox a whirl...

Come to think about it, since my convoluted process is CDex under wine to extract it as a mono 16-bit wav file and then the IIS codec to make an mp3 out of it, I probably could also divert the wav directly to sox using the "sox -t s16 - out.wav tempo 1.5" command, no?

---

### Post by iconoclast hero on 2011-08-07
Sorry...  I wasn't clear.  My iPod mini blew up when I attached the wrong AC/DC converter into the USB hub it was plugged into.  I am now using a Creative ZEN Vision:M which, at last check, is not portable with Rockbox.  I am looking to convert the files to ca. 1.4x speed before putting them on the ZEN, thus, mplayer or VLC won't help...  (As a matter of fact though, I'm watching something on VLC at ca. 1.1x now.)

Thanks

---

### Post by AlphaLexman on 2011-08-07
> **iconoclast hero said:**
> Sorry...  I wasn't clear.  My iPod mini blew up when I attached the wrong AC/DC converter into the USB hub it was plugged into.  I am now using a Creative ZEN Vision:M which, at last check, is not portable with Rockbox.  I am looking to convert the files to ca. 1.4x speed before putting them on the ZEN, thus, mplayer or VLC won't help...  (As a matter of fact though, I'm watching something on VLC at ca. 1.1x now.)

Thanks
Ohh, so you **DO** need to write... my bad!

---

### Post by iconoclast hero on 2011-08-07
> **AlphaLexman said:**
> Ohh, so you **DO** need to write... my bad!

Yeah, as I explained, my convoluted process is set up to mimic what I used to do with CDex/Windows...  CDex spits out a wav using its "WAV Output Encoder" in WAV format using compression "None (PCM)" at 44100 Hz sample rate in Mono.  From there I take the IIS codec and keep it in mono but downcode it to a bitrate of 24000.  

This gets me the following file sizes for the 5 discs of *Into Thin Air*:
```

-rw-r--r--  1 admin 13023720 2011-07-06 22:21 Into Thin Air -- Disc 1.mp3
-rw-r--r--  1 admin 12837222 2011-07-06 22:23 Into Thin Air -- Disc 2.mp3
-rw-r--r--  1 admin 12650958 2011-07-06 22:19 Into Thin Air -- Disc 3.mp3
-rw-r--r--  1 admin 13258890 2011-07-06 22:22 Into Thin Air -- Disc 4.mp3
-rw-r--r--  1 admin 12467424 2011-07-06 22:18 Into Thin Air -- Disc 5.mp3

```I could probably reduce the bitrate a bit further, and still be ok, but this is reasonable.

Now I'm looking to store them as standard standard speed mp3s and then make them 1.4x speed mp3s to listen to on my mp3 player.

---

### Post by FakeOutdoorsman on 2011-08-07
Personally I would rip CD to wav using abcde, or maybe just cdparanoia (which abcde can use anyway), process with SoX, and encode with LAME.
```
for input in *.wav; do sox "$input" -f wav - tempo 1.5 | lame --abr 56 -mm - "${input%.wav}.mp3"; done
```
Ignoring that, I recommend trying LAME at least one more time using similar options from this example.

I would not encode to a normal speed mp3 and then re-encode that to a faster mp3. I would encode both the standard mp3 and the fast one from the wav inputs. This will preserve the quality because it would avoid going from a lossy input to a lossy output.

---

### Post by iconoclast hero on 2011-08-07
> **FakeOutdoorsman said:**
> Personally I would rip CD to wav using abcde, or maybe just cdparanoia (which abcde can use anyway), process with SoX, and encode with LAME.
```
for input in *.wav; do sox "$input" -t wav - tempo 1.5 | lame --abr 56 -mm - "${input%.wav}.mp3"; done
```Ignoring that, I recommend trying LAME at least one more time using similar options from this example.

I would not encode to a normal speed mp3 and then re-encode that to a faster mp3. I would encode both the standard mp3 and the fast one from the wav inputs. This will preserve the quality because it would avoid going from a lossy input to a lossy output.

Yeah, I know about lossy >> lossy = extra lossy so I do want to avoid that...  that being said, quality is of little concern because it is just voice.  I will try LAME with the next book I rip and report back.

---

### Post by iconoclast hero on 2011-08-07
Ok, I took the LAME challenge with the first disc of Rushdie's *Luka and the Fire of Life*:

Output from cdparanoia (cdparanoia 1-14 "Luka and the Fire of Life -- Disc 1.wav")
```

-rw-r--r--  1 admin 756128060 2011-08-07 18:53 Luka and the Fire of Life -- Disc 1.wav
```Output from lame (lame --abr 56 -mm -a "Luka and the Fire of Life -- Disc 1.wav" "Luka and the Fire of Life -- Disc 1.mp3")
```
-rw-r--r--  1 admin  30280392 2011-08-07 21:54 Luka and the Fire of Life -- Disc 1.mp3

```Output from CDex downmixing .wav from cdparanoia to mono:
```
-rw-r--r--  1 admin  378064052 2011-08-07 22:08 Luka and the Fire of Life -- Disc 1.wav

```Output from IIS mp3 codec:
```
-rw-r--r--  1 admin   12799176 2011-08-07 22:09 Luka and the Fire of Life -- Disc 1.mp3

```

Now note that I have not soxed anything and am not going to get to that tonight, but while the LAME output sounds nice, it is ca. 3x bigger.

---

### Post by iconoclast hero on 2011-08-07
OK, to compare, more or less, apples to apples, LAME does work out fine:
lame --abr 22 -mm -a "Luka and the Fire of Life -- Disc 1.wav" "Luka and the Fire of Life -- Disc 1.mp3"
```
-rw-r--r--  1 admin  12467160 2011-08-07 22:18 Luka and the Fire of Life -- Disc 1.mp3

```Which sounds, through my Dell H-K speakers, just fine and indistinguishable from the IIS codec... at least with the fans on.  I could probably reduce the abr a bit further.  (Still, I wish to be stubborn and continue to do the same thing I've always done!  :) )

---

### Post by iconoclast hero on 2011-08-23
> **FakeOutdoorsman said:**
> Personally I would rip CD to wav using  abcde, or maybe just cdparanoia (which abcde can use anyway), process  with SoX, and encode with LAME.
```
for input in *.wav; do sox "$input" -t wav - tempo 1.5 | lame  --abr 56 -mm - "${input%.wav}.mp3"; done
```Ignoring that, I  recommend trying LAME at least one more time using similar options from  this example.

I would not encode to a normal speed mp3 and then re-encode that to a  faster mp3. I would encode both the standard mp3 and the fast one from  the wav inputs. This will preserve the quality because it would avoid  going from a lossy input to a lossy output.
  
I'm having a little problem:

```

sox WARN wav: Length in output .wav header will be wrong since can't seek to fix it
LAME 3.98.4 32bits (http://www.mp3dev.org/)
CPU features: MMX (ASM used), SSE (ASM used), SSE2
Autoconverting from stereo to mono. Setting encoding to mono mode.
Resampling:  input 44.1 kHz  output 16 kHz
Using polyphase lowpass filter, transition band:  5484 Hz -  5677 Hz
Encoding <stdin> to The Price of Everything -- Disc 12.mp3
Encoding as 16 kHz single-ch MPEG-2 Layer III (16x) average 16 kbps qval=3

```

That  sox warning at the beginning seems to be screwing me up later when I  try to ...  what is the word here ...  advance through the track,  particularly after the 22 minute mark, on my Zen.

---

### Post by iconoclast hero on 2011-08-23
> **FakeOutdoorsman said:**
> Have you tried SoX?
```
ffmpeg -i in.mp3 -t wav - | sox -t s16 - -t wav - tempo 1.5 | lame -V5 - out.mp3
```If you [compile SoX with mp3 support]("http://ubuntuforums.org/showpost.php?p=9859875&postcount=8") you could shorten this command (I'm not sure of the current status of mp3 support in the repo SoX).

BTW, I was messing with this and the first pipe segment (please let me know what it should be called) doesn't work.  I forget what -t is, but it doesn't set the type to wav.  The command set for ffmpeg is daunting so if you could let me know what to use, that would be stellar.

---

### Post by iconoclast hero on 2011-08-23
Just as another note, I compiled sox with mp3 support following this as a guide:
[http://techblog.netwater.com/?p=4](http://techblog.netwater.com/?p=4)

I did manually compile LAME because it didn't work otherwise when I did the ./compile for SoX...  other than that, I think it was relatively straight forward...  there was one thing I had to remove in the libmad Makefile.  The error was rather straight forward and just deleting -fforce-mem from the line ```
CFLAGS = -Wall -march=i486 -g -O -fforce-mem -fforce-addr -fthread-jumps -fcse-follow-jumps -fcse-skip-blocks -fexpensive-optimizations -fregmove -fschedule-insns2 . . .
``` was all that was necessary to get it to compile.

So now I'm using ```
for input in *.mp3; do sox "$input" -t mp3 1.4/"$input" tempo 1.4; done
``` to advance the tempo 1.4x.

---

### Post by FakeOutdoorsman on 2011-08-23
> **iconoclast hero said:**
> BTW, I was messing with this and the first pipe segment (please let me know what it should be called) doesn't work.  I forget what -t is, but it doesn't set the type to wav.  The command set for ffmpeg is daunting so if you could let me know what to use, that would be stellar.

Good catch. That should have been "-f wav". I'll change that.

I only included FFmpeg in my example command because in your original post I assumed your source files were also MP3, and SoX from the repo doesn't accept MP3 input if I recall correctly. In the example FFmpeg is used to decode MP3 to a format that can be piped to SoX to avoid any unnecessary intermediate files (and who doesn't like using pipes?).

> **iconoclast hero said:**
> Just as another note, I compiled sox with mp3 support following this as a guide:
[http://techblog.netwater.com/?p=4](http://techblog.netwater.com/?p=4)
I provided a link to some concise and Ubuntu specific [SoX compile guide](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8) in one of my earlier posts of this thread.

> **iconoclast hero said:**
> I did manually compile LAME because it didn't work otherwise when I did the ./compile for SoX.
You probably just needed **libmp3lame-dev** as shown in the guide I mentioned.

---

### Post by iconoclast hero on 2011-08-23
> **FakeOutdoorsman said:**
> Good catch. That should have been "-f wav". I'll change that.

I only included FFmpeg in my example command because in your original post I assumed your source files were also MP3, and SoX from the repo doesn't accept MP3 input if I recall correctly. In the example FFmpeg is used to decode MP3 to a format that can be piped to SoX to avoid any unnecessary intermediate files (and who doesn't like using pipes?).


I'm happy using pipes, I am still puzzling my way through the syntax!


> 
I provided a link to some concise and Ubuntu specific [SoX compile guide]("http://ubuntuforums.org/showpost.php?p=9859875&postcount=8") in one of my earlier posts of this thread.

You probably just needed **libmp3lame-dev** as shown in the guide I mentioned.D'oh, so you did...  I just googled it...  however from that guide, 
```

sed -i 's/--without-lame //' debian/rules sed -i 's/libmagic-dev, /libmagic-dev, libmp3lame-dev, /' debian/control sed -i 's/Write support not available yet.//' debian/control fakeroot debian/rules binary sudo dpkg -i ../*.deb fakeroot debian/rules clean

```
is unnecessary with the other one...  interestingly, without all of that sed stuff, you see
```

AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb au avi avr cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 ffmpeg fssd gsm hcom htk ima ircam la lpc lpc10 lu m4a maud mp2 mp3 mp4 mpg nist prc raw s1 s16 s2 s24 s3 s32 s4 s8 sb sf sl smp snd sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vox wav wavpcm wmv wve xa
PLAYLIST FORMATS: m3u pls
AUDIO DEVICE DRIVERS: oss ossdsp

```
when you execute sox @ cli.

It looks like it is two ways to the same end.

Since we're on the subject, besides executing cdparanoia from the command line twice to extract whole discs (cdparanoia -vsQ / cdparanoia 1-? "name.wav") is there a gui way to extract whole discs?

---

### Post by stevethefiddle on 2011-08-29
> **iconoclast hero said:**
> When I was using rockbox on an iPod mini, I was able to increase the playback speed.  When it did this, it also lowered the pitch so that it sounded like a person (please no chipmunk jokes).  I was playing with audacity and was able to get it to put out an acceptable file @ 1.4x speed.  I was wondering if there was a way to do this via CLI so that I could automate this process...  some audio books are lengthy and I don't want to negate the time I save per audio book by having to do this all manually.  :)

Any thoughts?

Thanks...

If you use Audacity you can set up a "*Chain*" of commands for batch processing.

"*Truncate Silence*" is an effect that reduces the silences between words and can thus increase the playback speed by making the words closer together. 

After using Truncate Silence you can then apply "*Change Speed*" and/or "*Change Tempo*" to increase the playback speed further. The "*Change Speed*" effect alters both the pitch and tempo (like playing a tape faster). "*Change Tempo*" increases the tempo by squashing the sound together without changing the pitch (a type of time stretching).

Adjusting the amount of each of these effects will allow a greater or lesser amount of speed-up which you can tweak for maximum speed and intelligibility.

All commands that I've "*quoted*" can be looked up in the Audacity manual for further details. [http://manual.audacityteam.org/index.php?title=Main_Page](http://manual.audacityteam.org/index.php?title=Main_Page)

---

### Post by iconoclast hero on 2011-08-29
> **stevethefiddle said:**
> If you use Audacity you can set up a "*Chain*" of commands for batch processing.

"*Truncate Silence*" is an effect that reduces the silences between words and can thus increase the playback speed by making the words closer together. 

After using Truncate Silence you can then apply "*Change Speed*" and/or "*Change Tempo*" to increase the playback speed further. The "*Change Speed*" effect alters both the pitch and tempo (like playing a tape faster). "*Change Tempo*" increases the tempo by squashing the sound together without changing the pitch (a type of time stretching).

Adjusting the amount of each of these effects will allow a greater or lesser amount of speed-up which you can tweak for maximum speed and intelligibility.

All commands that I've "*quoted*" can be looked up in the Audacity manual for further details. [http://manual.audacityteam.org/index.php?title=Main_Page](http://manual.audacityteam.org/index.php?title=Main_Page)

I did not know about *truncate silence*.  I'll play with that one a bit.  Does sox have an equivalent?  I did test out the audacity chains and was using the tempo and pitch commands to fine tune the overall effect better than just change speed.

---

### Post by iconoclast hero on 2011-10-06
> **iconoclast hero said:**
> I did not know about *truncate silence*.  I'll play with that one a bit.  Does sox have an equivalent?  I did test out the audacity chains and was using the tempo and pitch commands to fine tune the overall effect better than just change speed.

Haven't played with it, but here is an example:  [http://digitalcardboard.com/blog/2009/08/25/the-sox-of-silence/](http://digitalcardboard.com/blog/2009/08/25/the-sox-of-silence/)

---

