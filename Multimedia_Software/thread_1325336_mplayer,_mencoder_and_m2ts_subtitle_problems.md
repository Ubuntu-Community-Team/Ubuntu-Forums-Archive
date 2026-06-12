---
title: "mplayer, mencoder and m2ts subtitle problems"
date: 2009-11-13
forum: Multimedia Software
---

### Post by doragasu on 2009-11-13
I have a DLNA compatible NAS, and I'm using it to store my films ripped from BluRays and play them in my PS3. I use mencoder and x264 (both downloaded and compiled from the svn/git repositories) for the video encoding, and it works great, but now I have to encode a movie that has a forced subtitle track, and I want to burn that track into the encoded video.

I have extracted the track with tsMuxer as a .sup file, but as far as I know, .sup files aren't supported by mplayer, so I converted the .sup file to .sub/.idx format using BDSup2Sub 3.9.8.

Then I tried to display the subtitle track with mplayer, using -vobsub option, but I couldn't get subtitles to work. I tried using a lot of combinations with -sid, -slang and -vobsubid, switches, but none of them worked.

Are .sub files converted from BluRay films supported?
How can I properly display them with mplayer?
Once displayed by mplayer, will I be able to burn them with mencoder?

Thanks in advance.

Regards,

doragasu

---

### Post by lovinglinux on 2009-11-13
Convert the subtitles to ssa. I use Jubler to do that. Then hardcode the subtitles with mencoder:

```
mencoder moviesource.avi -sub moviesubtitles.ssa -a*s*s -a*s*s-color FFFF0000 &#8722;a*s*s&#8722;font&#8722;scale 3 -o movie output.mp4 -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=libx264:vbitrate=1200
```

Note: the asterisks in the code is because the forum doesn't allow to post the word "a s s", which is the file extension.

---

### Post by doragasu on 2009-11-13
Thanks a lot for help, I'll give that method a try.

I suppose Jubler is an OCR program, right? If possible I would prefer using a method that doesn't use OCR and burns the subtitles exactly as they are in the .sup file...

---

### Post by BlackXIII on 2009-11-13
its a subtitle editor.

---

### Post by doragasu on 2009-11-26
Finally I got some time to test Jubler, and it doesn't work for me. It recognizes neither sup nor sub/idx subtitles (it only shows garbage). I suppose that's because what I need is one of these:

a) (preferred) to find a way to get mplayer to show sub/idx subtitles, that are supposed to be supported (but I can't get them to work).

b) to find a way to convert sup or sub/idx subtitles to ssa or srt, then burn them with mencoder. I have to remark that the sup subtitles found in BluRays are NOT text strings, they are bitmaps. sub/idx files converted from sup files (and also the ones found in DVDs) are also bitmaps, and to convert them to ssa or srt files, usually a OCR program is used (I used SupRip when in windows, but it doesn't work even with wine).

Any suggestions?

---

