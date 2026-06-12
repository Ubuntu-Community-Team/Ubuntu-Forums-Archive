---
title: "Soft subtitles to Hard subtitles?? How to....??"
date: 2010-11-14
forum: Multimedia Software
---

### Post by Katty2008 on 2010-11-14
Okay, so here's the deal. I've been using ubuntu, but barely know how to use anything on it. I only really use it to surf the web, write my reports and watch movies/listen to music. Now, I'm hard of hearing, so I have to have subtitles in order to understand everything that is on in the videos. I download this knoean drama that I like and found soft subtitles for it (the video doesn't have any). Now, I want to find a way to turn the soft subtitles into hard. The videos on AVI format and the subtitles on SRT format. I know that I can get it to work with VLC media player, but I would like to able to put it on my PS3 or be able to play on my bluray player that has a USB port (so, I want it on a jumpdrive). What program would be the best for me use to do that or is there something that I need to do to the code?? Please, don't use big words!! I'm not that smart with computers, but I"m willing to learn. Thank you for your time.

---

### Post by lovinglinux on 2010-11-14
I'm not sure if PS3 can play mkv, but you could use mkvtoolnix-gui to mux the subtitles with the video, so there is no need to re-encode it to hardcode the subs.

If that doesn't work, you can use mencoder.

```
sudo apt-get install mencoder
```

The command I use to hardcode the subs is:

```
mencoder source.avi -sub source.srt -\a\s\s -\a\s\s-color FFFF0000 &#8722;\a\s\s&#8722;font&#8722;scale 3 -subpos 5 -o output.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

You need to replace "source" and "output" with the correct file paths.

---

