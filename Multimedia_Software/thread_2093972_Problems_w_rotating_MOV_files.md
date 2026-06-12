---
title: "Problems w/ rotating MOV files"
date: 2012-12-12
forum: Multimedia Software
---

### Post by dgavenda on 2012-12-12
I'm looking for a way to inspect a mov file to see if it's needs to be rotated and if so, rotate it.  All thru cmd line since I want to script this.  The mov files are coming from a Canon T3i DSLR.  

I've tried ffmpeg and mencoder to no avail.  I was able to manage to convert the mov to avi then rotate the avi.  That worked but sound went missing and quality degraded.  I do not want to chg format nor lower quality.  

Is there an easy way to do this in ffmpeg/avconv or anything else? 

Thx,
Dan

---

### Post by bcarlowise on 2012-12-12
I use AVIdemux to rotate my video files. I have a Canon T4i so it records videos as .mov files as well. It won't allow you to keep teh file as .mov but I've never had any quality issues saving/converting them to other formats. I save all my video files as mpeg or mp4 files. The plus side is that the file sizes are much smaller without any noticeable quality loss. 
To rotate the files, once you select your Video codec, just click on the "Filters" button and select the option to rotate and select the appropriate amount of rotation.
I usually leave the Audio codec to "Copy" so as not to convert the audio at all.

Hope this helps.

---

### Post by dgavenda on 2012-12-12
bcarlowise,
I've used avidemux before and it works w/o problems.  I'm looking for a cmd line way.  After reading/experimenting w/ avconv, I think I've found an easy way using mencoder.  I'm still playing w/ the options but this works:

mencoder <infile> -vf rotate=2 -oac pcm -ovc x264  -o <outfile> 

Also, I learned that 'avconv -i <infile>' will display the orientation which will tell me if it needs to be rotated.  So, the combo of using avconv and mencoder should do the trick.  

I'll post the final script if anyone cares to use it.

---

### Post by SeijiSensei on 2012-12-12
I posted a [script]("http://ubuntuforums.org/showpost.php?p=11814807&postcount=2") some time back to rotate images that might prove helpful as a starting point.

---

### Post by FakeOutdoorsman on 2012-12-12
You can rotate upon playback so you don't have to re-encode. ffmpeg has the *transpose* filter (also *hflip* and *vflip*) if you do want to re-encode:

```
ffmpeg -i input -vf transpose=2 -vcodec libx264 -preset medium -crf 23 -acodec copy output.mkv
```

See the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for more info on the -preset and -crf options.

---

### Post by andrew.46 on 2012-12-12
A recent enough copy of FFmpeg will have the transpose filter:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -filters  2>/dev/null | grep transpose[/COLOR]**
transpose        V->V       Transpose input video.

```

which is well worth a look at, I will admit that the options look like a degree of experimentation would be in order :)

**Edit:** D'oh! Beaten by the FakeOutdoorsman!!!

---

### Post by dgavenda on 2012-12-14
I have a solution using mencoder (posted previously).  It's good enough for my wife/family/etc to see our 18 month son walk on the floor not the wall.  :^) 

I've kept the originals (in MOV) so I can play w/ the quality settings. 
 
What are the major differences between ffmpeg/avconv and mencoder?  It seems ffmepg/avconv have more options. Is that correct?  

Thx,
Dan

---

