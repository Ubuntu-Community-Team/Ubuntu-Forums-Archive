---
title: "Extracting audio from video files."
date: 2009-05-24
forum: Multimedia Software
---

### Post by oh n0es on 2009-05-24
I was wondering if anybody knew an application that I could use to extract the audio files from video files (.avi) and use as preferably .mp3 audio tracks?

---

### Post by xzero1 on 2009-05-24
This link should help. [http://linux.byexamples.com/archives/229/extract-audio-from-video-or-online-stream/](http://linux.byexamples.com/archives/229/extract-audio-from-video-or-online-stream/)

---

### Post by logos34 on 2009-05-24
The above link doesn't meniton .avi files

Try Avidemux

>Audio>save

---

### Post by xzero1 on 2009-05-24
> The above link doesn't meniton .avi filesI expect it will work on avi files in a similar manner, though you may have to specify the codecs, but avidemux is also good.

---

### Post by oh n0es on 2009-05-24
Thanks, gave that a shot and it worked extremely quickly.
However, I have a couple of problems.
Firstly, the resulting file for my test was just under 1hr 26mins long. When added to Rythmnbox, the timeline was greyed out, for lack of a better word, and I was unable to skip to other parts of the track.
Secondly, for some reason I can't cd into certain directories. I tried using cd to navigate terminal to a certain directory and it just cut off part of the directory command and said that there is no such directory?

EDIT: @Above, it works fine with .avi files, just tested it.

---

### Post by xzero1 on 2009-05-24
Well mplayer is really not designed to encode standalone audio files. You might try extracting to a wav then use a good encoder like lame to encode the file to mp3. Better yet just pipe it through, if you know what I mean.

---

### Post by oh n0es on 2009-05-24
> **xzero1 said:**
> Well mplayer is really not designed to encode standalone audio files. You might try extracting to a wav then use a good encoder like lame to encode the file to mp3. Better yet just pipe it through, if you know what I mean.

Okay, I'll try converting the file then.
As for 'piping' it, I have no idea sorry. Any ideas about my cd issue also?

EDIT: For some reason SoundConverter won't convert any files. Click convert and nothing happens.

---

### Post by xzero1 on 2009-05-24
When you use the mplayer method mentioned it only dumps the sound, it does not necessarily convert it to mp3. When you do file your_file_name.mp3 what does it say?

---

### Post by logos34 on 2009-05-24
oh, it mentions ffmpeg--great app.  try that It'll convert all in one command, no pipe necessary.

Don't use soundconverter, especially if converting to mp3.  There's a bug in gstreamer lame plugin/it doesn't correctly implement lame options for VBR output
(it uses the same gst libs as Sound Juicer--see warning [here]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding"))

---

### Post by xzero1 on 2009-05-24
This will give you a wav file. 
ffmpeg -i name.avi -vn -f wav name.wav

Pipes are very cool, its worth learning how to use them. Basically, you use the output of one command as input to another. See if this works using pipes:

ffmpeg -i name.avi -vn -f wav - | lame -V2  -  name.mp3

As for the cd issue, try it in a new terminal. If it works close and reopen the old one.

---

### Post by oh n0es on 2009-05-24
When I try the command linked to in the first post, it works fine. When I try the command listed above, I get this;
Unsupported number of channels: 6

Also, my cd issue is not solved, and I have tried making several new terminals.

---

### Post by xzero1 on 2009-05-24
Avi files with 6 channles?

Try it like this:

ffmpeg -i name -ac 2 -vn -f wav - | lame -V2  -  name.mp3

---

### Post by logos34 on 2009-05-24
post the exact dir you're trying to change to.

tip: use the TAB key to autocomplete long dir names/names with spaces (+ '\' character)

---

### Post by logos34 on 2009-05-24
> **xzero1 said:**
> ffmpeg -i name -ac 2 -vn -f wav - | lame -V2  -  name.mp3

but the lame pipe is unecessary--ffmpeg converts directly to .mp3/lossy 

(unless I misunderstood what the O.P. wanted)

---

### Post by oh n0es on 2009-05-24
As a test, I'm trying to extract a (legally backed up) episode of Peep Show to audio.
Dir: /media/HD-CEU2/Stuff/Movies/TV/Peep Show/Season 1
And it gets cut off to this: bash: cd: /media/HD-CEU2/Stuff/Movies/TV/Peep: No such file or directory

It seems that there is a limit of the dir length that cd can handle because as you can see it's cutting off part of the command.

---

### Post by mc4man on 2009-05-24
Maybe double check your path the dir.'s in question
You could install this to either ck. , get path or use instead of manually typing

```
sudo apt-get install nautilus-open-terminal
```

After install restart x and then r.click on the dir. -> open in terminal
It should open at the dir. prompt.

to use path shown when 'nonstandard' 
Ex
r. click on dir.

> doug@doug-desktop:[COLOR="Blue"]~/other/Jerry Garcia and David Grisman (1991) Jerry Garcia and David Grisman[/COLOR]$ 

to use this one (added quotes   [COLOR="Red"]"[/COLOR]
> 
doug@doug-desktop:~$ cd ~/other[COLOR="Red"]"[/COLOR]/Jerry Garcia and David Grisman (1991) Jerry Garcia and David Grisman[COLOR="Red"]"[/COLOR]
doug@doug-desktop:~/other/Jerry Garcia and David Grisman (1991) Jerry Garcia and David Grisman$ 


---

### Post by logos34 on 2009-05-24
yeah, put entire dir or path in " " or tab autocomplete + \

---

### Post by xzero1 on 2009-05-24
> but the lame pipe is unecessary--ffmpeg converts directly to .mp3/lossy Good point. But pipes are more fun and lame has more options for audio encoding and is probably better quality. I don't think it will be that much slower either.

---

### Post by oh n0es on 2009-05-24
Adding quotation marks around the dir. sorted the problem, thanks a lot.
However I'm still having the problem with the timeline bar being greyed out in Rythmnbox, any ideas?

---

### Post by xzero1 on 2009-05-24
When you play the file does the timeline bar move? Try playing a smaller file. Do you have the same problem?

---

### Post by oh n0es on 2009-05-24
It works fine with every other audio file, it just doesn't work with the audiodump file that we made.

---

### Post by logos34 on 2009-05-24
> **xzero1 said:**
> Good point. But pipes are more fun and lame has more options for audio encoding and is probably better quality. I don't think it will be that much slower either.

you can specify lame with option

-acodec libmp3lame

---

### Post by xzero1 on 2009-05-24
Like I mentioned before audiodump does not seem to necessarily convert the file format  -- thats why its so fast. It keeps the original audio format. But I don't know what the original audio type was.  I would reconvert that one using ffmpeg with the -ac option (see my other post).

---

### Post by xzero1 on 2009-05-24
> you can specify lame with option

-acodec libmp3lameDo you get all the lame options available for lame (replay-gain,mode,etc)? Is it as fun and straightforward as using pipes?:p

---

### Post by oh n0es on 2009-05-24
Tried this command;
ffmpeg -i s01e01 -ac 2 -vn -f wav - | lame -V2 - s01e01.mp3
And was given this error:
s01e01: no such file or directory
Warning: unsupported audio format

---

### Post by xzero1 on 2009-05-24
Is s01e01 the name of the file or is it s01e01.avi or something?

---

### Post by oh n0es on 2009-05-24
Damn, can't believe I missed that. It's encoding now, I'll make a new post when I've tested the result in Rythmnbox.
EDIT: And now it works fine in Rythmnbox too. Thanks a lot for the help, everything is sorted now!

---

### Post by FakeOutdoorsman on 2009-05-24
You can also just remove the video and keep the audio from your file without needing to re-encode.  Of course it may not be the format you are looking for.  For this example I will use a Xvid avi. First I find out what the audio format is with this command:
```
ffmpeg -i input.avi
```
FFmpeg spits out file specifications including audio information:
```
Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 160 kb/s
```
Now that I know it is mp3 I run the following command:
```
ffmpeg -i input.avi -acodec copy output.mp3
```
Another example, but this time a MP4 file:
```
ffmpeg -i input.mp4 -acodec copy -vn output.mp4
```
This time I added the -vn option to tell FFmpeg to ignore the video.  You need to do this with containers (mp4, ogg) that can be both audio and/or video. I could have also just used:
```
ffmpeg -i input.mp4 -acodec copy output.aac
```
No re-encoding and no quality loss.  I'm simply copying the audio like you would with a text copy and paste.

---

### Post by mc4man on 2009-05-24
I would think to pipe *to lame* for encoding, rather than ffmpeg doing it itself, something along these lines (in this case just an audio file as an example (blue for stdin

```
ffmpeg -i test.m4a -f wav - | lame -V2 [COLOR="Blue"]"-"[/COLOR]  test.mp3
```

---

