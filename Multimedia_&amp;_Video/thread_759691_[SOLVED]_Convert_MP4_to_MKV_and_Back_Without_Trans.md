---
title: "[SOLVED] Convert MP4 to MKV and Back Without Transcoding"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by deejross on 2008-04-19
I have several movies in mp4 and wanted to convert them to mkv. And in the future, if I need to, convert back to mp4 if I need to put a movie on my ipod or something. The mp4 files I already have were encoded with x264 and aac and I've read in several places that it is possible to move the streams from one container to the other without actually transcoding the streams, but no one ever tell you how.

So does anyone know how to do this? I don't think it would be that complicated since there's no actual audio/video conversion going on. Thanks in advance for your help.

---

### Post by disturbedite on 2008-04-19
an extremely simple solution:
avidemux

---

### Post by deejross on 2008-04-19
It took me a minute to figure out how to save in the container format I wanted. When you click Save, it only gives you an option to use AVI or MPEG, but if you have selected MKV as the format on the sidebar before saving, you can simply add the '.mkv' to the output filename and it saves it.

However, playing the file in Totem, I can't seek through it. Trying to seek resets the movie to the beginning. It doesn't work in VLC either. Is there some kind of indexing that needs to be done in Avidemux to make it work or something?

---

### Post by soga_genzo on 2008-04-19
MP4 to MKV:

Just use the original, [mkvtoolnix](http://www.bunkus.org/videotools/mkvtoolnix/)'s *mkvmerge*. It comes with a nice GUI and can be found in the repositories.

MKV to MP4:

Extract the individual streams from an MKV file with *mkvextract*, then create MP4 with *mp4box* (which is contained in the package *gpac*).

---

### Post by deejross on 2008-04-19
The mkvmerge works great and the GUI is pretty good too....I like that it has the ability to batch convert multiple files. So far, I haven't found any side effects of using it to convert mp4 to mkv. So thank you SO much for that.

As for the mk4v to mp4, I haven't tried that yet, but I've seen a similar method used for other mp4 conversions. So thanks for that one too. I'm sure I can figure it out from here.

---

### Post by disturbedite on 2008-04-20
> **deejross said:**
> It took me a minute to figure out how to save in the container format I wanted. When you click Save, it only gives you an option to use AVI or MPEG, but if you have selected MKV as the format on the sidebar before saving, you can simply add the '.mkv' to the output filename and it saves it.

However, playing the file in Totem, I can't seek through it. Trying to seek resets the movie to the beginning. It doesn't work in VLC either. Is there some kind of indexing that needs to be done in Avidemux to make it work or something?
of course that is how it works, you have to select the container then save. i think you could rebuild the frames to fix seeking, that might work...

---

