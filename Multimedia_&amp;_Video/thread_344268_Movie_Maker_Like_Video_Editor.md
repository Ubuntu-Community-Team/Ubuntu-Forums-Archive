---
title: "Movie Maker Like Video Editor"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by allwin on 2007-01-22
I have a camera which records video to a SD format card in .ASF format.  Under Windows, I can import the video, chop it into clips, trim and reorder the clips, add titles and render a new video suitable for something like YOUTUBE.  The total time to process such a video in that environment is seldom more than 5 times the running length of the video (say, 10 minutes to render 2 minutes of the final cut with effects, titles, etc.).

My short question is, does any package exist in Linux that can just as easily and quickly do the same job as Windows Movie Maker?  I've tried Cinelerra, but it won't accept the .asf files directly, and neither will FFMPEG transcode them into anything which I could successfully use to produce anything but noisy skipped frames in Cinelerra, at rates comparable to glaciers melting (even in these days of global warming):biggrin: .

---

### Post by meng on 2007-01-22
I use kino, which has the functionality and ease of use you describe with WMM. However, it accepts DV files. I don't know if it can accept asf files.

---

### Post by allwin on 2007-01-22
> **meng said:**
> I use kino, which has the functionality and ease of use you describe with WMM. However, it accepts DV files. I don't know if it can accept asf files.

Thanks.  BTW, .ASF files appear to be MPEG4, and I have managed to get them to play and even iconize on the Gnome desktop at least, so the codecs exist...I'm too much of a noob to tell where they came from.

Is there something that natively handles MPEG4 (say, 640x480 30FPS)?  Am I missing something in Cinelerra that would help?

---

### Post by glabouni on 2007-01-29
from my old days in video editing under windows, I learned to keep away from asf files.

If i remember correctly, asf is a container format, inside you can find a variety of codec encoded streams. if you can find which ones are inside your asf files, you might be able to convert them to a more easily used format:
[https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen](https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen)

---

### Post by allwin on 2007-01-29
> **glabouni said:**
> from my old days in video editing under windows, I learned to keep away from asf files.

If i remember correctly, asf is a container format, inside you can find a variety of codec encoded streams. if you can find which ones are inside your asf files, you might be able to convert them to a more easily used format:
[https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen](https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen)

Thanks for the information.  I have been down that road with little success.  The video is MP4 within the ASF file and when I used FFMPEG to convert it, it kept complaining about skipping frames.  The result of that conversion was pretty much hash...a good frame here and there, audio out of sync with video, only about half the frames there, etc.

Besides that, the conversion process took 5 times as long as the original clip.  With Windows Movie Maker, the .asf file goes right in to the editor and there is no transcoding step that I'm aware of.  I can visually click and trim the clips, glue them together, and put out a WMV file which then goes right into YouTube.

I will have to try Kino...it's on the list...and play with ffmpeg again.  But for now, this remains a reason why I can't get rid of Windows.

---

### Post by bribaetz on 2007-11-04
anything in Ubuntu that can handle avi files enough to edit them i mean i downloaded a heap of crap for it but no go. any programs cinelerra is a little difficult for me it looks kool but i dont know if i have the patience for it

---

