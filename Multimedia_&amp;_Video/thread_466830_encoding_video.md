---
title: "encoding video"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by finite9 on 2007-06-07
I'm trying to encode my home made movies into some format that will last a long time and has high quality, plus a format that has good compression.

I have looked at MPEG-2 for high quality, H.264 for best compression and XviD for TV/DVD player compatibility for those of us who don't yet have a BluRay player.

My source material is raw DV from a canon MVX4i DV cam at 1056x576 widescreen 25fps interlaced.

I use FFMPEG to convert the dv into MPEG-2 and I deinterlace it at the same time.

I use mencoder to convert to H.264/AAC in two modes: One best quality, according to options on Mencoder html docs, and another version for compatibility with Quicktime7.

I also use Mencoder for XviD creation at best quality according to Mencoder html docs site.

You can read the code below if you're interested.

I am not too impressed with the quality of H.264, and wonder if someone can enlighten me?  When I encode to MPEG2, I see all detail in video that exists in DV original, but when I encode H.264, it becomes blurry in the fine details (note that in my script below, it is not best quality, but I have tried best quality according to mencoder website and it is the same).  Yes, I am well aware that best compression means lower quality, but how come Bluray uses H.264 and has better quality than DVD videos in MPEG2 format then?  Do they use a much cleaner source material?  Do they have more fine tuned encoding parameters?  I suspect that they have an encoder that is simply much better than what is currently available with x264-bin.  Is this true?


Another question regarding interlacing.  I deinterlace in ffmpeg and it looks pretty good, although the docs do say there will be loss.  I deinterlace in Mencoder and it looks pretty bad.  There are like 10 different deinterlacers in mencoder, which is 9 too many, and most of them are poor.  I tried yadif and kerndeint and yadif seems best apart from green artefacts in the image, even with svn build, so I use kerndeint at the moment.  Don't know why they can't just do it right like ffmpeg does?  Anyway, according to ffmpeg docs, you get loss with deinterlacing, so they recommend to use -flags +ilme plus two other flags I cannot remember.  It still looks jagged though!  Is this just so that you can wath it on TV where the interlacing is less apparent?  I don't really want loss if I can help it but I don't want motion to look jagged...is there a way to deinterlace without loss?

Im a bit disheartened that there are so many ways of encoding in GNU/Linux but none of them seem perfect.  I haven't even tried the GUI apps out there (suspect they all use ffmpeg/mencoder as backend anyway) and have not looked at transcode.  Does anyone know of a tool that can encode H.264/AAC with great quality that will work on a bluray player?  


```
#!/bin/bash
# convert to MPEG-2
infile=DVcapture20070314-mini.dv
infile2=$(echo "$infile" | sed s/"\."/".\n"/g | grep "\.")
file="$infile2"mp4

## convert raw dv straight into MPEG-2 AC-3 2ch with ffmpeg and deinterlace
ffmpeg -i $infile -deinterlace -threads 2 -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd "$infile2"mpg
```


```
#!/bin/bash
#convert to H.264/AAC
infile=DVcapture20070314-mini.dv
infile2=$(echo "$infile" | sed s/"\."/".\n"/g | grep "\.")
file="$infile2"mp4

ffmpeg -i $infile /tmp/"$infile2"wav
faac /tmp/"$infile2"wav -o /tmp/"$infile2"m4a

## following will create Quicktime7 compatible MP4 file, but is not
## best quality possible with x264
mencoder $infile -o /dev/null \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=1:turbo=1 \
-nosound
## second pass
mencoder $infile -o /tmp/"$infile2"h264 \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=2 \
-nosound

MP4Box $file -add /tmp/"$infile2"h264 -add /tmp/"$infile2"m4a

rm /tmp/"$infile2"wav
rm /tmp/"$infile2"m4a
rm /tmp/"$infile2"h264

echo 'Conversion of ' $infile ' to H.264/AAC in MP4 container complete.'
```

---

### Post by moeFinley on 2007-06-09
H264 is a better encoding technology than MPEG2.  But what ever you are using it's all down to the bitrate and keyframes.  MPEG2 on standard DVDs goes no higher than 10MB/s and is normally about 7MB/s.  H264 on HD DVDs can go as high as 40Mb/s.

But you can also use H264 to encode videos for mobile phones that have a bitrate of 36Kb/s.  Needless to say the quality ain't the same as a HD DVD!

I'm not sure where mencoder is getting it's bitrate in that command line?  I normal use a frontend for all that stuff :)

Where ever it is, upping the bitrate is probably what you need to do.  But why not just keep the DV files?  They can't be much larger than a high bit rate H264 and are much better for future conversion.

As for deinterlacing, are your DV files interlaced in the first place?  This should be very apparent when you play them back on your computer as any moving object will be broken into lines.  Interlacing is a way of compressing 50fps into 25fps by showing only half the lines of each frame and is only relevant to old PAL TVs and cameras.  Most modern cameras will record progressively (not interlace) and will therefore not need deinterlacing.

Many deinterlacing methods can have strange effects on clips that aren't interlaced in the first place.

Hope some of this helps.

---

### Post by finite9 on 2007-06-11
> **moeFinley said:**
> H264 is a better encoding technology than MPEG2.  But what ever you are using it's all down to the bitrate and keyframes.  MPEG2 on standard DVDs goes no higher than 10MB/s and is normally about 7MB/s.  H264 on HD DVDs can go as high as 40Mb/s.

I dont know where it is getting its bitrate from, I just took the example settings from mencoders homepage for best quality.  I will look at the bitrate to see if it makes any difference.

> Where ever it is, upping the bitrate is probably what you need to do.  But why not just keep the DV files?  They can't be much larger than a high bit rate H264 and are much better for future conversion.

The dv file I tested with is 2.5GB and after conversion to H.264 or XviD it was about 200MB.  Quite a difference.  No doubt MPEG-2 will have been about 700-800MB, but still less than half the original dv file.

> As for deinterlacing, are your DV files interlaced in the first place?  This should be very apparent when you play them back on your computer as any moving object will be broken into lines.  

Yes they are definitely interlaced--play them in Totem and movement produces many jaggies.  The dv camera is a high end consumer cam, pretty new.  Must say im a bit disappointed with it.

---

### Post by moeFinley on 2007-06-11
Remember the bitrate affects the end file size.  Yes you will reduce the file size but most editors and other videos apps will only open DV files and alike.  MPEG2 and H264 weren't designed to be edited.  Plus you will lose quality.

Setting the bitrate is done with ```
bitrate=<value>
``` and for the audio ```
abitrate=<value>
```
There's a great guide [here]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide")

---

### Post by finite9 on 2007-06-12
cool...bitrate fixed my problem.  Set it to 2500 and quality was as good as original.  Actually better as I ran hqdn3d filter on it.

I will be saving the original minidv tapes with original footage of course, so I can edit later, and for archive purposes, but to be able to easily view a final edit, I wanted a format that would last a while (h264) and a format that is available to the masses now (Xvid).  It wasn't feasable to send friends a 2.5GB dv file, but a 200MB x264 is ok.

Now for the final question...MP4 container or Matroska??????  Who the heck can play Matroska?

---

