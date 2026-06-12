---
title: "Speed Up Video Playback"
date: 2012-09-07
forum: Multimedia Software
---

### Post by mastermindg on 2012-09-07
I've got a bunch of informational videos that I'd like to speed up so I can knock them out faster :)

I've tried using ffmpeg setpts but it's dropping the audio:

```
ffmpeg -i input.mp4 -r 8 -vf setpts=0.25*PTS -an Output.mp4
```

Is there a way to speed up a video (with audio) on Ubuntu without losing frames?

Thanks!

---

### Post by FakeOutdoorsman on 2012-09-07
Why not speed it up duing playback instead of having to re-encode it? MPlayer will do this just fine. According to the man page:
```
[ and ]
    Decrease/increase current playback speed by 10%.
{ and }
    Halve/double current playback speed.
BACKSPACE
    Reset playback speed to normal.
```
However, if you must re-encode you will probably have to process the audio separately, such as with *sox*, and then mux with ffmpeg:
```
ffmpeg -i video.mp4 -i audio.wav -c:v copy -c:a libmp3lame -q:a 4 out.mkv
```

---

### Post by qyot27 on 2012-09-07
The setpts option isn't dropping the audio in that example, the -an is.

Really, the easiest way to speed up playback is to do so in the video player (well, it's also possible to do it rather easily with an AviSynth script, but that requires additional types of setup* first).  If you want the audio to stay in sync with the video, speeding it up like that will render it almost unlistenable due to chipmunking and music getting garbled something awful.

*AviSynth proper (2.6a3, but you can augment it with one of SEt's multithreading-capable trunk builds which are more recent) requires Wine; AvxSynth, the Linux port of 2.5.8, requires you to build it yourself (I've not tested whether the audio functionality is completely working, but AssumeFPS should work).


EDIT: FakeOutdoorsman beat me to it.

---

### Post by mastermindg on 2012-09-09
I'm running ffmpeg v0.8.3-4....newest on 12.04. When I try to run the command:

```
ffmpeg -i video.mp4 -i audio.wav -c:v copy -c:a libmp3lame -q:a 4 out.mkv
```

I get the following error:

Unrecognized option 'c:v'
Failed to set value 'copy' for option 'c:v'

Any ideas?

---

### Post by mastermindg on 2012-09-09
Fixed it by upgrading to ffmpeg v10.4:
[URL="https://launchpad.net/~jon-severinsson/+archive/ffmpeg"]
ppa:jon-severinsson/ffmpeg[/URL]

Works like a beauty! Thanks!

---

