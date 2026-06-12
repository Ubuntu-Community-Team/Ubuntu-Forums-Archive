---
title: "Converting m4p to mp3?"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by Yes on 2007-08-15
I have some files that I bought off of iTunes, and I need to convert them to .mp3 .  Right now, they are .m4p .  I tried opening them in Audacity, and then exporting them as an mp3, but the song was only five seconds for some reason.  I know there are tools to do this in Windows, but is there any way to do it in Ubuntu?

Thanks.

---

### Post by kdub432 on 2007-08-15
I would use vlc

```

vlc file.mp4 --sout '#transcode{acodec=mp2a, ab=96}:std{access=file, dst= "/path/to/file.mp3", mux=ts}'

```

that should work, if i remember my vlc commands right. Look up the manuals on videolan.org if you need more help.

btw, this is transcoding a 96kbps file...

---

### Post by Yes on 2007-08-15
I tried that, and it said "Encrypted DVD support unavailable".  Any other programs?

Thanks.

---

### Post by Yes on 2007-08-15
I'm beginning to think that the only way to do this is burning the songs to a CD and then converting the CD files to mp3.  So I have two questions:

I've heard that this will kill the song's quality.  Is it really bad?  Is it even worth doing if the songs lose so much quality?

Will copying them to a CD and then to an mp3 even work?

Thanks.

Edit:  I just tried to copy the files to a CD using the Serpentine Audio CD Creator.  When I tried opening the files it gave me an error that said that it couldn't open the files because they were an unsupported filetype.  It said to make sure that I had the proper GStreamer plugins, but I tried searching in Add/Remove Programs for GStreamer and m4p, and I couldn't find anything.  Does that mean that I can't even put my files on a CD?

---

### Post by univremonster on 2007-09-05
I have been using SoundKonverter successfully for some time, although I have never tried to convert an mp4.  I used it to change all my old .mp3 into .ogg just fine, a little slow but faster than burning to a cd.  Also you can pick what quality you want to keep, everything from very low to lossless

---

### Post by fenian on 2007-09-05
In a termial type this....

> sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs

that  should give you all the gsstreamer plugins.

---

### Post by kurros on 2007-09-06
You aren't going to be able to convert DRM protected m4p files. You would have to burn them to an Audio CD in iTunes and re-rip them. Yes this may reduce the audio quality, but no more than transcoding the song if it weren't protected.

---

