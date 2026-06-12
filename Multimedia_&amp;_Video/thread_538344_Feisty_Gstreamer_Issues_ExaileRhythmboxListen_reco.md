---
title: "Feisty Gstreamer Issues: Exaile/Rhythmbox/Listen recognizes mp3 but there is no sound"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by klepto on 2007-08-29
I've searched the forums here and google for an answer to know end. I've solved the problem before in Edgy but I don't remember how. Here's the gist: 

I have installed xine/gstreamer codecs including lame/fluendo/etc When I load Rhythmbox or Listen Music Player it sees my mp3 songs imports them but when I play it acts like it is playing but there is no sound.  I ran gstreamer-properties and it gave me a test sound so I know my audio is working perfectly. 

Anyone got any ideas. Thanks for you time.

---

### Post by the_darkside_986 on 2007-08-29
Did you attempt to play your media by double-clicking the files and confirming that you want to install the forbidden packages? I assume you did. Since that is failing, you should search the repos for mplayer and vlc media player. I'm not sure what VLC requires to get forbidden codecs running but with mplayer, go to the mplayer headquarters and download the win32 codecs packages. Extract the files into either /usr/local/lib/codecs or /usr/local/lib/win32 (not sure which one just make a sym link i guess) and mplayer should be able to play your media files.

I am currently learning how to convert my music to the superior .ogg format. The method of converting an mp3 using mplayer (after installing it and win32 codecs is)
```

mplayer -quiet -vo null -vc dummy -af volume=0,resample=44100:0:1 -ao pcm:waveheader:file="Songname.wav" "songname.mp3"

```
and then
```

oggenc Songname.wav

```
at the commandline. Ogg vorbis takes up much less space than the mp3 that has the same sound quality.

Now, I just have to figure out how to convert video files to ogg theora...

---

### Post by klepto on 2007-08-29
mplayer plays mp3's just fine. I think it is gstreamer issue.

---

