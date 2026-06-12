---
title: "Convert mkv to avi - poor result"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by sonic167 on 2007-11-30
I’m trying to convert a sample mkv file to avi (my real goal is to convert a 1Gb 720p mkv file right after
!)
I use the command 
ffmpeg -i film.mkv -acodec mp3 -vcodec mpeg4 -r 30 -b 4000 -f avi -y film.avi

The problem is both mkv and resulting avi files indicate a resolution of 768x432, but the avi resolution appear to be quite poor when viewed (squares pixels everywhere).

The avi file size is also much smaller (16.782 kb versus 36.096 for the mkv)

What did I do wrong to get such poor avi file?

Do I have to use the -s tag to specify the resolution (defaulting to 320x240, as just seen in other posts?) , and if so, will I have to put the 720p resolution (whatever that is ... can't remember) when converting my big file?

Thanks,

Vince

---

### Post by eye208 on 2007-11-30
> **sonic167 said:**
> I use the command 
ffmpeg -i film.mkv -acodec mp3 -vcodec mpeg4 -r 30 -b 4000 -f avi -y film.avi
The squares you see are blocky compression artifacts.

Try this line instead:
```
ffmpeg -i film.mkv -acodec mp3 -vcodec mpeg4 -sameq film.avi
```

The -sameq option makes ffmpeg use variable bit rates in order to preserve the quality of the original file. (The -r and -f switches can usually be omitted.)

Edit: If the .mkv file already contains MPEG-4 video and MP3 audio, and all you want to do is change the container to .avi, you should try this first:
```
ffmpeg -i film.mkv -vcodec copy -acodec copy film.avi
```
This will prevent quality loss entirely since the streams are just copied into the new container unchanged.

---

### Post by sonic167 on 2007-11-30
Thanks eye208.
I'll try that asap.

Vince

---

### Post by sonic167 on 2007-12-01
I tried the simple container "copy" command, but the resulting avi still appears poor in quality (ffmpeg -i film.mkv -vcodec copy -acodec copy film.avi)
This is the input/output data:

Duration: 00:03:06.1, bitrate: N/A
  Stream #0.0: Video: h264, yuv420p, 768x432, 30.00 fps(r)
  Stream #0.1: Audio: aac, 44100 Hz, stereo
Output #0, avi, to 'film.avi':
  Stream #0.0: Video: h264, yuv420p, 768x432, q=2-31, 30.00 fps(c)
  Stream #0.1: Audio: aac, 44100 Hz, stereo
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 5581 q=-10245534.5 Lsize=   36243kB time=186.0 bitrate=1596.0kbits/s    
video:34091kB audio:1913kB global headers:0kB muxing overhead 0.664146%

Any idea why when viewing the avi it looks like a poor quality?

Thanks,

Vince.

---

### Post by sonic167 on 2007-12-01
Ok, the -sameq flag worked and the avi quality is great, but the file size is 5 times bigger. Is that normal?

If I run this on my 1Gb file, it will probably take forever and will require 5Gb???

Thanks for enlighting me about ffmeg!

Vince.

---

