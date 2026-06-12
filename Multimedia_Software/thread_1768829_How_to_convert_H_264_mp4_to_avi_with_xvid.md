---
title: "How to convert H 264 mp4 to avi with xvid?"
date: 2011-05-27
forum: Multimedia Software
---

### Post by resander on 2011-05-27
How to convert H 264 mp4 to avi with xvid?

I have a file (300mb) containing a video encoded as h264 mp4. It runs on movie player, but I want to run on the tv using a (fairly modern) dvd player that accepts avi xVid as input from cd or usb.

How do I convert from h264 mp4 to avi(xvid)?

Ken

---

### Post by ron999 on 2011-05-27
> **resander said:**
> 
How do I convert from h264 mp4 to avi(xvid)?

Hi
With FFmpeg you could try a command something like this:-
```
ffmpeg -i filename.mp4 -vcodec libxvid -b 1200k -acodec libmp3lame -ab 128k output.avi
```

---

### Post by andrew.46 on 2011-05-28
Mind you it might be worthwhile trying a small variation of Ron's syntax and use:

```
-vcodec mpeg4 -vtag XVID
```

This often fools some devices and some will argue that FFmpeg's native mpeg4 encoder produces a better result than libxvid, while just as many will argue the opposite :).

---

### Post by resander on 2011-05-28
Many thanks,

That worked very well. Conversion time about 10 min/100mb on a 2.4 ghz P4. Made several avis and burned onto cds. Now I can view these on the tv and a portable dvd player, which is exactly what I wanted.

However, one avi failed playing with the video player showing the message 'resolution 640x704 not supported', but Movie player displayed without problems. Nautilus properties for the mp4 file showed the resolution indeed was 640x704. I did not know how to resolve this, but tried the size option -s vga for the output file and converted the mp4 again. The video player accepted it, but the output appeared as a band in the middle of the wide-screen tv with a height about one third of the height of the screen. The band spanned the whole screen horizontally, so everything in the band was stretched horizontally. How do I convert to make it look reasonable on the tv screen?   

Ken

---

### Post by montini on 2012-04-12
is there a GUI frontend?

---

### Post by andrew.46 on 2012-04-12
There is WinFF but IMHO it is well worthwhile learning to use FFmpeg instead...

---

