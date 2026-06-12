---
title: "ffmpeg trying to convert jpgs to video"
date: 2014-04-18
forum: Multimedia Software
---

### Post by JimLS on 2014-04-18
Trying to convert some time lapse pictures to video.  After some searching and reading I tried what I thought would work to produce something that would play on most PCs (without loading special programs, codecs, etc.).  I ended up with a file that appears to play (the indicator at the bottom moves to the right as expected but the screen is all black).  I did some more searching and found some information that ubuntu uses a variation of ffmpeg and didn't understand all the details of that.

Here is the command I used and output:

```
jim@Netvista:~/picstest/13$ /usr/bin/ffmpeg -r 10 -i "B%05d.jpg" test1.mp4
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:00:59 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, image2, from 'B%05d.jpg':
  Duration: 00:00:10.00, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 1280x1024, 10 fps, 10 tbr, 10 tbn, 10 tbc
Incompatible pixel format 'yuvj422p' for codec 'mpeg4', auto-selecting format 'yuv420p'
[buffer @ 0x8081100] w:1280 h:1024 pixfmt:yuvj422p
[avsink @ 0x8082660] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x80829a0] w:1280 h:1024 fmt:yuvj422p -> w:1280 h:1024 fmt:yuv420p flags:0x4
Output #0, mp4, to 'test1.mp4':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: mpeg4, yuv420p, 1280x1024, q=2-31, 200 kb/s, 10 tbn, 10 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
frame=  100 fps=  5 q=31.0 Lsize=    1312kB time=10.00 bitrate=1074.4kbits/s    
video:1310kB audio:0kB global headers:0kB muxing overhead 0.121365%
jim@Netvista:~/picstest/13$ ls
```

Not absolutely necessary but a lossless method is desired so I don't loose quality and can save some storage space from the individual jpgs and not have to retain jpgs.

My system is Ubuntu 12.04.3

---

### Post by andrew.46 on 2014-04-18
This is not something I have tinkered with myself but there is certainly some worthwhile reading here:

Create a video slideshow from images
[http://trac.ffmpeg.org/wiki/Create%20a%20video%20slideshow%20from%20images](http://trac.ffmpeg.org/wiki/Create%20a%20video%20slideshow%20from%20images)

I suspect that for better results you might be better to use the same wiki and build a newer version of FFmpeg....

---

### Post by SeijiSensei on 2014-04-19
I suggest giving [Imagemagick convert]("http://jupiter.ethz.ch/~pjt/makingmovies.html") a try.  Install it with "sudo apt-get install imagemagick".  

However an easier option might be to use Imagemagick or GIMP and *convert the still frames into an animated gif*.  That's a format that will play in most browsers and image viewers like Gwenview without any additional software.  

In GIMP, open the first frame, then use File > Open As Layers and select the remaining images.  Use File > Export to create an animated gif by specifying an output file with ".gif" as the extension. Check the "animation" box and adjust the delay to however long you'd like each image to remain on screen.  I'd also save a version of the composite image in GIMP's native XCF format using File > Save.  That way if you want to muck with the result, you can just edit the XCF version and re-export. I've made dozens of [animated avatars]("http://forums.animesuki.com/album.php?albumid=115") using this method.  [This one](http://forums.animesuki.com/picture.php?albumid=115&pictureid=51594) is a slideshow composed of images taken from JPEGs.

---

### Post by JimLS on 2014-04-19
I have an 11.10 box and it appears to have the real ffmpeg so may give that a try.  Would like to get it working on the 12.04 box though.

I am a little put off by changing to the main ffmpeg on the 12.04 box.  It looks like compiling is fairly involved - a bunch of dependencies, etc.  There is the static build but it isn't clear to me if that will fix my issues or exactly how to install that.  There are also the ubuntu builds on the site linked above but I am not sure if that would solve my issues.

Things like this and unity have me looking at other distros..

---

### Post by FakeOutdoorsman on 2014-04-20
> **JimLS said:**
> There is the static build but it isn't clear to me if that will fix my issues or exactly how to install that.

No need to install. Just download, extract, and execute like this:

```

# assuming your current directory contains the new ffmpeg
./ffmpeg -i input output
```

or

```
/full/path/to/ffmpeg -i input output
```


> **JimLS said:**
> There are also the ubuntu builds on the site linked above but I am not sure if that would solve my issues.
The PPA? Doubtful. It provides old branches for compatibility for dependencies.

> **JimLS said:**
> Things like this and unity have me looking at other distros..
Probably a good idea. There are lots of choices out there. Many of us long-time frequent visitors to these forums have started with Ubuntu but have moved on to more fitting alternatives.

Most computers these days should be able to handle all or most profiles of H.264 video, so that will be a good start:
```
./ffmpeg -framerate 10 -i "B%05d.jpg" -codec:v libx264 -pix_fmt yuv420p test1.mp4
```
The "-pix_fmt yuv420p" will ensure that the output uses a chroma subsampling scheme that will be compatible with all players (you should only need this for libx264). If your player still doesn't like it add, as an output option, "-profile:v baseline".

See the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide) for more info.

Some timelapse videos work well with [slomoVideo](http://slowmovideo.granjow.net/). It's not just for slow motion.

---

