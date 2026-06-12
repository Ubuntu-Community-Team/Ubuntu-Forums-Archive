---
title: "Joining .ogv files causes slight pause."
date: 2014-03-11
forum: Multimedia Software
---

### Post by brunomatti on 2014-03-11
Hi All!  I have a small problem.  I am recording screencasts with gtk-recordmydesktop.  I like to record in small bursts, to save on editing, and join the file later.  When I try this, the image... stutters... while the audio continues.  So, I will be talking about my next point, but the video image has not moved on.    I have tried justing .ogv files using openshot, and  ```
cat foo-01.ogv foo-02.ogv > foo-03.ogv
``` ```
oggCat foo-01.ogv foo-02.ogv > foo-03.ogv
```  But they all have these pauses in the video.  Any ideas how I can join them smoothly?  Thanks guys!

---

### Post by ssam on 2014-03-11
cat just sticks all the bytes in the 2 files together. That works fine for joining text files, but not for much else. You video player is probably seeing the start of the second file (which will contain a new header) as corruption in the file, but manages to recover and continue.

I'd recommend using an actual video editor, such as openshot, pitivi (you might want to get a recent version from [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa) ) kdenlive or one of several others.

If you want to use the command line it looks like you can join files with avconf/ffmpeg [https://stackoverflow.com/questions/18552901/how-to-merge-videos-by-avconv](https://stackoverflow.com/questions/18552901/how-to-merge-videos-by-avconv) [http://trac.ffmpeg.org/wiki/How%20to%20concatenate%20%28join,%20merge%29%20media%20files](http://trac.ffmpeg.org/wiki/How%20to%20concatenate%20%28join,%20merge%29%20media%20files)

---

### Post by brunomatti on 2014-03-11
Hi Ssam.    Thanks for the swift response!  I tried the commands in the link you included, and neither worked.  The first ```
avconv -i concat:foo-1.ogv\|foo-2.ogv -c copy foo-3.ogv
``` just desynchronised the audio for the first clip, ignored the rest!  the second command in the thread ```
mencoder -oac pcm -ovc copy -o foo-3.ogv ls *.ogv
``` just errored out complaining about .avi files.    As you can see in my original post, I did also try openshot with the file in the first instance, but with the same short pause.

---

### Post by FakeOutdoorsman on 2014-03-11
Try the [concat demuxer](http://ffmpeg.org/ffmpeg-formats.html#concat-1) in ffmpeg (the real one from FFmpeg, not the buggy, fake one in the repo which lacks this feature).

Get a recent ffmpeg build from the [FFmpeg Download](http://ffmpeg.org/download.html#LinuxBuilds) page.

Or do this:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
tar xzvf ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
```

Then make a text file listing your files. The contents should look like:
```
file 'foo-1.ogv'
file 'foo-2.ogv'
file 'foo-3.ogv'

```

Then run ffmpeg (note the **./** before ffmpeg):
```
./ffmpeg -f concat -i input.txt -codec copy output.ogv
```

As already mentioned by ssam see [How to concatenate (join, merge) media files](https://trac.ffmpeg.org/wiki/How%20to%20concatenate%20%28join,%20merge%29%20media%20files) for more information.

---

