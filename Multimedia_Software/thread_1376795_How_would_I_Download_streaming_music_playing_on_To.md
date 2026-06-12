---
title: "How would I Download streaming music playing on Totem"
date: 2010-01-09
forum: Multimedia Software
---

### Post by dark2023 on 2010-01-09
There is a piece of streaming music I want, when I open it, the song plays using totem browser plug in.

 Is there a way I can capture the song and keep it as a file (or put it on my mp3 player), preferably without downloading anything.

(this is the link to the streaming music file, if that's any help, [link]("http://atomiku.com/files/music/atomiku%20-%20Voodoo%20People.mp3"))

---

### Post by xc3RnbFO8P on 2010-01-09
Record music in VLC

Copy the link address
then paste into
Media > Convert/Save > Network > **Address** ,
Convert/Save (button)
Destination File: (what ever you choose)
Profile:  Audio - Vorbis (Ogg)

---

### Post by dark2023 on 2010-01-09
I got his message


 [COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG Audio layer 1/2/3.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue.[/COLOR]

---

### Post by xc3RnbFO8P on 2010-01-09
This works:
**Profile: Audio - Vorbis (Ogg)**

---

### Post by dark2023 on 2010-01-09
ok, It gave me a text file

---

### Post by xc3RnbFO8P on 2010-01-09
Rename it to *.ogg

---

### Post by sdowney717 on 2010-01-09
for VLC select advanced controls, this will give you a red record button.
play the stream, click the red button, it records audio mp3 and video mpeg2.

---

### Post by ron999 on 2010-01-09
..

---

### Post by ron999 on 2010-01-09
Hi
If you'd like to try downloading that song using the command line.
Here goes.

Using mplayer:-
```
mplayer -dumpstream -dumpfile whatever1.mp3 http://atomiku.com/files/music/atomiku%20-%20Voodoo%20People.mp3
```

Using VLC:-
```
vlc http://atomiku.com/files/music/atomiku%20-%20Voodoo%20People.mp3 :demux=dump :demuxdump-file=whatever2.mp3
```

:)

---

### Post by gacb on 2012-08-27
In Firefox, right click on a blank area of the page and select 'view page info'. Under the media tab there may be what you're looking for. Select and save the file.

---

### Post by The Cog on 2012-08-27
Closing thread for necromancy, and becaue we don't support copyright violation.

---

