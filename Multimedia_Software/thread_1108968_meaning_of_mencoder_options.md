---
title: "meaning of mencoder options"
date: 2009-03-28
forum: Multimedia Software
---

### Post by linuxrockz on 2009-03-28
Hi I may sound stupid but would anyone plz tell me the meaning of the various options used in these commands. I know what they do but I can't seem to follow what the parameters mean.
```
$ mencoder vcd//:2 -oac lavc -ovc lavc -o filename.avi
```

```
mencoder -vf rotate=1 -ovc lavc -oac file1.avi -o file2.avi
```

Plz explain what these "-oac lavc -ovc lavc -o " parameters mean

Thanks.

---

### Post by andrew.46 on 2009-03-29
Hi linuxrockz,

> **linuxrockz said:**
> Hi I may sound stupid but would anyone plz tell me the meaning of the various options used in these commands. I know what they do but I can't seem to follow what the parameters mean.

```
$ mencoder vcd//:2 -oac lavc -ovc lavc -o filename.avi
```

[LIST=1]
[*]**vcd//:2** Open track 2 of a video CD
[*]**-oac lavc** Encode the audio with a libavcodec codec (a library of codecs created and maintained by FFmpeg and used by MPlayer)
[*]**-ovc lavc** Encode the video with a libavcodec codec (a library of codecs created and maintained by FFmpeg and used by MPlayer)
[*]**-o filename.avi** Create an output file called filename.avi
[/LIST]

And the next commandline:

> 
```
mencoder -vf rotate=1 -ovc lavc -oac file1.avi -o file2.avi
```

[LIST=1]
[*]**-vf rotate=1** Use a video filter called 'rotate' and spin the image by 90 degrees clockwise
[*]**-ovc lavc**  Encode the video with a libavcodec codec (a library of codecs created and maintained by FFmpeg and used by MPlayer)
[*]**-oac** There is something missing here, this is a direction to encode the audio but with exactly *what* is missing :-).
[*]**file1.avi** This is the input file.
[*]**-o file2.avi** This specifies the output file
[/LIST]

Normally if you specify '-ovc lavc' you would also specify which video codec you would like to use from this group of codecs. For example to encode to MPEG-2 video you would specify:

```
mencoder input.avi **[COLOR="Red"]-ovc lavc -lavcopts vcodec=mpeg2video[/COLOR]** -oac copy output.avi
```

and the same idea operates with '-oac lavc' where you would specify which audio codec you would like to use. To use wma audio for example you would do the following:

```
mencoder input.avi -ovc copy **[COLOR="Red"]-oac lavc -lavcopts acodec=wmav2 [/COLOR]**output.avi
```

I hope this has made it all a little clearer? You can see a description of the lavc codecs here:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html)

Andrew

---

### Post by linuxrockz on 2009-03-29
Thanks a lot Andrew you have made it very clear.
I am just getting a hand on the ultimate power of the terminal and people like you are a blessing. :-)
Thanks a lot again

Cheers
-Linuxrockz

---

