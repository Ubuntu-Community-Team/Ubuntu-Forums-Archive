---
title: "video conversion for aviread?"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by Dekster on 2008-01-28
Hi all!

I am taking my first steps in video editing, as I need to collect sequences out of all sorts of video files, and feed them to the "aviread" function in Matlab for a school project.

aviread supports 8-bit frames, for indexed and grayscale images, 16-bit grayscale images, or 24-bit truecolor images.

I have Ubuntu at home, where I have time to spend editing, and my lab has Red Hat and XP with Matlab 2006b. Matlab can only read uncompressed avi files on UNIX, and I was able to read div3 on the XP, but not xvid. Maybe I could get the administrator to install more codecs but I doubt it...

I read around this forum and google, and installed Avidemux, VLC and LiVEX, hoping for an easy way to convert edited files to the right format. I found Livex to be especially easy and intuitive for editing, but I couldn't get the codec right when saving. When I tried using the ffmpeg as the encoder for divx in LiVEX it couldn't create the file, so I read the man page for ffmpeg, and after trying my best and failing (I could create the wanted file, but only xvid MPEG-4).

I now have a whole bunch of edited short movies I want to use, but they are all in "Motion JPEG", fourcc "IJPG" which can't be read by aviread...

I read the man page for mencoder and tried some forcing, using the '-ovc raw' option for uncompressed and '-vf format', but the best I could get was an uncompressed YUV file named something.avi not fooling anyone but myself.

Somehow along the way I did manage to create a div3 avi file, but it was not "24-bit truecolor" so I was yet again rejected by Matlab, and I can't remember how I did it anyway so even if I had got it right I still wouldn't get it right for the next 300 movies I need to process.

Much frustrated I confess to this forum - I don't have a clue, I don't know what I'm doing :cry:

Very long story short - how can I convert anything to a format and codec that can be read by "aviread"?!
Can anyone give me an example on how to do it with mencoder or ffmpeg from the command line?

I should mention I am a Feisty Fawn (7.04) 64 bit user.

I thank any help in advance, sorry for the long whiny post.

---

### Post by Dekster on 2008-01-29
After reading some more, and a little lucky googling, I found this command:

```
mencoder -o output_file.avi -ovc lavc -lavcopts vcodec=msmpeg4:vbitrate=5000:vhq -ofps 30 your_movie.mov
```

and now I can continue my work. MEncoder rocks!

---

### Post by sixmoney on 2008-03-18
I used ffmpeg
do like this:
ffmpeg -i input_file.avi -vcodec bmp output_file.avi
This is the only video codec that matlab reads as far as I know.

---

### Post by skela on 2008-07-15
sixmoney, i love you!

---

