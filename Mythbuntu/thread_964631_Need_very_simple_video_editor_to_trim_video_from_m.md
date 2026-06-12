---
title: "Need very simple video editor to trim video from mythtv"
date: 2008-10-31
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-10-31
All I need is to be able to trim the start and finish of the occasional video file copied from my mythtv box.  What is the easiest way to do this outside of mythtv?  Something that works as easily as the editor built into myth would be perfect.

---

### Post by ashmew2 on 2008-10-31
I dont know about mythtv but kino should work!
Its in the repos..

---

### Post by ubnewbie2 on 2008-10-31
> **ashmew2 said:**
> I dont know about mythtv but kino should work!
Its in the repos..

When I try to open the .mpg video, Kino says something to the effect that this is not a DV file, do you want to import it.  I say OK, and it says "failed to load media file "/path.mpg.dv".

Not a good start :)

---

### Post by ubnewbie2 on 2008-10-31
Found out why it was doing that. Apparently it needs ffmpeg and mencoder - but they were not installed by the package.  I thought prerequisites were supposed to be added as needed by Synaptic?

Anyway, it is sitting importing a video now, but boy is it SLOW.  I short video, only about 3GB, is taking ages to import.  I think an editor that can work on mpg files natively is needed.

---

### Post by ubnewbie2 on 2008-10-31
Did I say slow?  Over an hour, still going, and the 3GB file has turned into a 14 GB file - still growing.

---

### Post by volkswagner on 2008-10-31
I have not tried this, but it was included with Ulitimate Edition.

Avidemux is listed as a simple visual video editor.

---

### Post by OffAxis on 2008-10-31
there's also pitivi in the repos.

```
sudo apt-get install pitivi
```

[http://www.pitivi.org/wiki/Overview]("http://www.pitivi.org/wiki/Overview")

---

### Post by fenian on 2008-10-31
Avidemux (in the repos) is  good for making minor edits (making simple cuts,joining clips ,etc...).

---

### Post by ubnewbie2 on 2008-11-01
I have been trying avidemux.  Unfortunately the results of a simple start and end trim exhibit very bad audio sync problems.

---

### Post by perspectoff on 2009-04-24
> **ubnewbie2 said:**
> All I need is to be able to trim the start and finish of the occasional video file copied from my mythtv box.  What is the easiest way to do this outside of mythtv?  Something that works as easily as the editor built into myth would be perfect.

FFMPEG is your friend.

To trim a file, use:

```
ffmpeg -i sampleinputvideo.mpg -sameq -ss 00:00:00 -t 00:01:00 sampleoutputvideo.mpg
```

-i specifies the input file, which in this example is sampleinputvideo.mpg (which can be an MPEG-2 video), but can be of any format, including .flv (Flash video), .wmv (windows video), .avi (or any of a myriad other different formats)

-sameq means to retain the same quality

-ss means to start at the timepoint indicated (hh:mm:ss), which in this example is at the beginning, or 00:00:00

-t means to process this much of the sampleinputvideo (in hh:mm:ss), which in this example is 1 minute of video.

FFmpeg recognises which output format you desire by the ending of the output file name. If you want a Flash video output instead, for example, simply name the output file sampleoutputvideo.flv. 

Example:

My sampleinput.mpg video is 1 hour, 20 minutes, and 43 seconds long (01:20:43), but I only want the video from 00:45:05 to 01:10:00, which is a segment that is 24 minutes and 55 seconds (00:24:55) long. To create a new file with only this segment, my command would be:

ffmpeg -i sampleinputvideo.mpg -sameq -ss 00:45:05 -t 00:24:55 sampleoutputvideo.mpg

This can be done for any type of video file. Much, much easier than fiddling around with GUI editors.

If you don't know the timepoints of the video segment you want to select, use a player like VLC or MPlayer, each of which displays timepoints as you watch the video.


Also, although I've never tried it, I assume the usual concatenation command will join segments (of the same type) together (presumably in a lossless manner):

cat samplevideo1.mpg samplevideo2.mpg > samplevideo12.mpg

---

### Post by itlarson on 2009-04-24
Nice explanation!  I've wanted to do this from time to time myself.  I wish there was a big wiki full of simple howto's like this for linux.  Man pages aren't helpful unless you already know how to use the program.

---

### Post by FakeOutdoorsman on 2009-04-24
> **perspectoff said:**
> FFMPEG is your friend.

To trim a file, use:

```
ffmpeg -i sampleinputvideo.mpg -sameq -ss 00:00:00 -t 00:01:00 sampleoutputvideo.mpg
```

This example can be improved.  If you use *-ss* and *-t* as input file options instead of output file options it will seek before decoding the input.  If *-ss* and *-t* are applied as output options as in your example, the input file will be decoded first and then the seeking applied.  This usually isn't a big deal unless you are trimming something that's CPU intensive to decode such as 1080i h264.

More importantly you can trim without re-encoding by using *-acodec copy* and *-vcodec copy*.  This will preserve the quality of the original and be much faster because you're not re-encoding anything:
```
ffmpeg -ss 00:10:00:00 -t 00:00:30:00 -i sampleinputvideo.mpg -acodec copy -vcodec copy sampleoutputvideo.mpg
```

---

### Post by perspectoff on 2009-04-24
> **FakeOutdoorsman said:**
> This example can be improved.  If you use *-ss* and *-t* as input file options instead of output file options it will seek before decoding the input.  If *-ss* and *-t* are applied as output options as in your example, the input file will be decoded first and then the seeking applied.  This usually isn't a big deal unless you are trimming something that's CPU intensive to decode such as 1080i h264.

More importantly you can trim without re-encoding by using *-acodec copy* and *-vcodec copy*.  This will preserve the quality of the original and be much faster because you're not re-encoding anything:
```
ffmpeg -ss 00:10:00:00 -t 00:00:30:00 -i sampleinputvideo.mpg -acodec copy -vcodec copy sampleoutputvideo.mpg
```

Thank you, thank you! -acodec copy means keep the same audio codec and -vcodec copy means keep the same video codec. I could never figure that out from the FFMPEG documentation.

I have a related question about cropping off the top and bottom without re-encoding.

Would that command be similar to the following?

```
ffmpeg -i sampleinputvideo.mpg -croptop 102 -cropbottom 112  -acodec copy -vcodec copy sampleoutputvideo.mpg
```

---

### Post by FakeOutdoorsman on 2009-04-24
> **perspectoff said:**
> I have a related question about cropping off the top and bottom without re-encoding.
I think *-vcodec copy* will ignore any cropping or other options that would alter the video so I believe you will have to re-encode.  That option basically tells FFmpeg to copy the original stream, like a copy and paste.

---

### Post by 4ebees on 2009-07-23
> Also, although I've never tried it, I assume the usual concatenation command will join segments (of the same type) together (presumably in a lossless manner):

cat samplevideo1.mpg samplevideo2.mpg > samplevideo12.mpg

Good advice. Though I'm not sure I agree with the 'fiddling with GUI editors' comment <grin> I love 'em -I certainly agree wholeheartedly about the utility of these commands. I just used it to put together four videos. I wanted to have the same intros and endings (including credits). After creating the four 'body' videos, I then easily added the front and back videos without having to open another editor in each instance.

Very nice and easy. Particularly when you can sequence the commands using a space, a semicolon and then another space between each, e.g.:

cat name.intro.mpeg sysadmin.part.1.mpeg name.credit.mpeg > sysadmin.final.pt1.mpeg ; cat name.intro.mpeg sysadmin.part.2.mpeg name.credit.mpeg > sysadmin.final.pt2.mpeg ; cat name.intro.mpeg sysadmin.part.3.mpeg name.credit.mpeg > sysadmin.final.pt3.mpeg ; cat name.intro.mpeg sysadmin.part.3.mpeg name.credit.mpeg > sysadmin.final.pt3.mpeg

Works a treat.


>  
ffmpeg -i sampleinputvideo.mpg -sameq -ss 00:45:05 -t 00:24:55 sampleoutputvideo.mpg

This can be done for any type of video file. Much, much easier than fiddling around with GUI editors.


One small thing I've noticed is you have to be careful about the audio quality as well. In this instance I agree with Fake Outdoorsman (post further on)

> ffmpeg -ss 00:10:00:00 -t 00:00:30:00 -i sampleinputvideo.mpg -acodec copy -vcodec copy sampleoutputvideo.mpg

Many thanks for the information. I found it very useful and helped me build on the bits I do know, using the more you know :))

Much appreciated.

---

### Post by 4ebees on 2009-07-23
Hey FakeOutdoorsman,

Please see my other post. 

Many thanks for the information.

---

### Post by SiHa on 2009-12-26
Post Deleted - wrong thread.

oops.

---

### Post by nickrout on 2009-12-26
dvbcut is what you  want. Works perfectly and maintains audio sync.

projectx also does the job well.

kino works only in DV video (the sort you get from a DV camera, which most pre-HD video cameras used) and therefore converts anything else to DV, which takes a long time and produces large files.

---

### Post by SiHa on 2009-12-26
Thanks I'll look at dvbcut, might have to jump into sql to get the cutpoints out of the db, so I can script it.
I've played with ProjectX quite a bit in Windowsland as well, never thought of using it under Linux!

---

### Post by nickrout on 2009-12-26
> **SiHa said:**
> Thanks I'll look at dvbcut, might have to jump into sql to get the cutpoints out of the db, so I can script it.
I've played with ProjectX quite a bit in Windowsland as well, never thought of using it under Linux!


Even if you just demux the file with projectx and then mux it back together again, you'll lose the audio sync problems and open it up to using other editors, ones that might otherwise accentuate the audio problems.

dvbcut will also get rid of audio sync errors.

audio sync problems often arise where there is a recording glitch, which is quite common.

my usual capping/encoding process is:
[LIST]
[*]record with mythtv
[*]transfer to desktop computer
[*]run thru dvbcut to get rid of ads, as it has a nice interface for scrubbing through video and finding cut points
[*]open in avidemux and encode to h264/aac
[/LIST]

---

