---
title: "dv video stripped from camcorder editor to trim end of file?"
date: 2012-12-30
forum: Multimedia Software
---

### Post by sdowney717 on 2012-12-30
I want to trim off the end. I tried openshot. I can trim off the end.
Problem is it can only save it as an encoded export???

Is there an editor that can accept DV video and edit it, then just save the file without having to do a compression encoding? Which takes hours.

This is like loading a document into word, then make changes and when you goto save the file, it forces you to convert it to another format.

---

### Post by vanadium on 2012-12-30
Try avidemux, a linear video editor.

---

### Post by sdowney717 on 2012-12-30
avidemux can not open a dv file that was captured with kino.

dv video is what you get captured with kino. I am able to open those files in all the other editors I have tried.

---

### Post by sdowney717 on 2012-12-30
What I was interested in was capturing video from a digital8 camera.
Then edit the film, strip out blank video.
then save the dv file which so far is impossible.

then convert the edited dv video file using handbrake to h264.
Handbrake has a special feature to enable web video streaming. None of the others mention this.

So far I can not do these things.

---

### Post by sdowney717 on 2012-12-30
> What’s special about DV non-linear editing?

DV is compressed just enough to be able to stream into and out of current-day PCs and Macs, and the availability of inexpensive 1394 I/O cards and fast SCSI-2 hard disks means that high quality video storage and manipulation on desktop computers is now possible for the first time without having to spend a king’s ransom on specialized RAID arrays and proprietary codecs.

**DV can be stored and manipulated in native form, without transcoding to JPEG, MPEG, Wavelets, or the like. The same high quality seen on DV tape is maintained in the computer.**

Ha, maybe for windows only!
[http://www.videouniversity.com/articles/dv-formats-everything-you-need-to-know/#linear](http://www.videouniversity.com/articles/dv-formats-everything-you-need-to-know/#linear)

Does anyone have thoughts on this? I can also boot windows7, what program would work there for dv video editing?

---

### Post by vanadium on 2012-12-30
[http://www.avidemux.org/admWiki/doku.php?id=general:faq](http://www.avidemux.org/admWiki/doku.php?id=general:faq)
>  ???? Avidemux won't open my DV or miniDV file ????

Avidemux can only open type-2 DV files at the moment. Two types of DV files exist: type 1 and type 2 (read the information at Microsoft.com about the differences between them). However, some cameras produce type-1 DV video. To convert them to type-2 DV, you can either use the Canopus DV File Converter or the Ulead DV Converter. 

That could be the problem with Avidemux, unfortunatelly.

Command line splitting with avconv or ffmpeg may be possible, but is far less convenient indeed.

The idea of non-linear video editors is that you throw the raw video at it, then compile your movie, and write it out in any format suitable for the specific task it is intended for. However, I imagine that it would be convenient, especially when you want to archive the raw video, to clean these files out a bit, quite fast and without loss in quality, i.e., without transcoding. That would typically be a job for avidemux, but unfortunatelly, it fails here, and I would not know of an alternative under linux.

---

### Post by evilsoup on 2012-12-30
It's very far from ideal, but until someone posts a GUI option, you can remove the end of a video with:

```
avconv -i input.avi -c copy -t 00:15:32 output.avi
```

That will copy everything in the file up until 15 minutes, 32 seconds. Obviously, figure out when you want the video to end. You can similarly use the -ss option to cut off the beginning of a video:

```
avconv -i input.avi -c copy -ss 00:03:30 -t 00:05:20 output.avi
```

This will begin copying at 3 minutes 30 seconds, for a length of 5 minutes 20 seconds.

The best NLE I used on Linux, back when I was trying out the options a few years ago, was Cinelerra. I don't know if it can do what you want, though, and it's not available in the repos - you can install it from [this PPA](https://launchpad.net/~cinelerra-ppa/+archive/ppa), and find out for yourself if it'll suit your needs.

---

### Post by sdowney717 on 2012-12-30
I am trying to grab the video editing concept.
What happens is I capture the video as dv video.

How about if I convert the dv video first using handbrake to h264.
Then edit it in openshot.
Will it then need to be rencoded again under export?
If I edit multiple times and it has to re-encode over and over, it is going to loose quality every time?

Seems like the video editing tools are not very good if you cant just re-save the original encoding with the modifications and have to re-encode. I am currently doing an export to h264 in openshot. I chose high quality. The file is half done and is currently at 3gb. start time 10am currently 1:18pm

Original dv video file is 13gb.
Handbrake would have already finished, typically was taking 40 minutes.

There is a lot of settings for openshot.
target MP4(h.264)
video profile HDV 1440x1080p 29.97 fps
Quality high

I have no idea if this is waste of time with these setting.

Likely waste of time as the original was not hdef 1080p.
Original was 480p from a digiatal8 camera.
So then what settings would you choose in openshot?

---

### Post by FakeOutdoorsman on 2012-12-30
> **sdowney717 said:**
> How about if I convert the dv video first using handbrake to h264.

That is an unnecessary step. H.264 is not a very editor-friendly format compared to DV although it doesn't mean that it can't be done.

> **sdowney717 said:**
> Will it then need to be rencoded again under export?
Yes.

> **sdowney717 said:**
> If I edit multiple times and it has to re-encode over and over, it is going to loose quality every time?

If depends on the formats involved. Yes, if you edit, export a lossy format, import, edit, export a lossy format, import... There is generational loss each time you re-encode to a lossy format over and over (using the resulting output as the next input for re-encoding); although if re-encoded properly you may not notice.

> **sdowney717 said:**
> So then what settings would you choose in openshot?
I would import the original DV files in Openshot, edit, and then export to the desired format depending on what I was planning on doing with the output (DVD, YouTube, web site, etc). You didn't mention anything in particular, so I can't give much of an exact suggestion.

When working with a format that is not supported by an editor, or something that is not very easy to edit you can re-encode to a lossless intermediary:

```
ffmpeg -i input -c:v huffyuv -c:a pcm_s16le output.mkv
```
Or possibly *output.avi* if your editor doesn't grok mkv. The lossless file will be huge, but that's ok; it is usually only temporary and will minimize, but possibly not eliminate, due to various factors, any potential loss due to re-encoding. It should also be fairly easy on the editor.

In reality, if I were simply trimming junk out of the DV files, I would probably do it like evilsoup showed (but using ffmpeg instead of course), and then concatenate the resulting DV files together using cat, or the various concat tools in ffmpeg as shown in [How can I join video files?](http://ffmpeg.org/faq.html#How-can-I-join-video-files_003f), but that doesn't mean that you should do it this way. Openshot might be easier and work just fine.

---

### Post by evilsoup on 2012-12-30
Video editing programs will create files of their own, these are essentially lists of every change made to the input videos. This is what is made when you hit 'save', rather than 'export' or 'render', generally speaking. If you're willing to keep your original video around, and you keep this 'edit list' file around, you will be able to go back and make changes to the video, and then export a brand-new copy without introducing generation loss.

---

### Post by sdowney717 on 2012-12-30
I am trying flowblade now.
[http://www.webupd8.org/2012/06/flowblade-cool-non-linear-video-editor.html](http://www.webupd8.org/2012/06/flowblade-cool-non-linear-video-editor.html)

I have the feeling your supposed to keep the dv file direct from the tape around for future mods and export a 'finished' video file for say youtube.  I was kinda hoping not to need to do that, but I can see it losing quality on x264 playback compared to the original dv file. Plus I am very new at this encoding and so many choices to make! SO I guess will have to keep originals and an encoded copy. Some of the tapes are +20 years old but still seem ok.

I was planning on taking a lot of digital8 tapes around 50 tapes and putting them on the computer hardrive. Then copy and give to my parents. He will not want large dv 13gb files so the idea was to edit then turn into x264 video files.

I did a few using windows movie maker on XP. This took the tape and realtime encoded in 720x480 vbr WMV file of about 1 to 1.5gb size. They actually look fairly decent. Using Windows Movie Maker, I saw no option to create any raw DV output file. WMM has a download for windows7. This new version of WMM can output straight to h264.

---

### Post by sdowney717 on 2012-12-30
part of my problem is in the re encoding understanding. I am going to kill this one. says has 45 hours left on the process!

It is why I liked handbrake, it was simple and fast about 40 minutes for the same video.

Another test I did was using openshot to re-encode. I has taken from 10:06 till now at 17:23 for the process.

---

### Post by andrew.46 on 2012-12-30
What sort of processor are you running? Video processing/conversion can use some serious horsepower and benefits from a very fast, multicore machine with buckets of ram....

---

### Post by sdowney717 on 2012-12-30
core2 duo e6550 
8gb ddr3 

yes it is totally wimpy or is it?
anyway I am trying windows7 and WMM.
it is pretty dumbed down.

I somehow managed to find a trim feature, pulls video off front and back. Get this, you need a calculator to figure out the ending seconds as when you move the slider, the ending trim seconds do not move. But the beginning trim ones will move.

Right now it is doing a conversion to a 'computer pc'
it is saying 40mb per second of video. And it is about 25% done after about 10 minutes.

I think the problem is I have to use these non linear editors to edit and that means dealing with them trying to export the final video file. and so far it is painfully slow. It is relatively speedy to use handbrake on Linux, about what WMM is doing. I may have to give up on using Linux for editing, unless I can figure out why it is so slow.

I see no mention of codecs or anything in the WMM software, just a bunch of preset devices to encode towards.

ALSO, Windows7 CAN NOT HANDLE DV Video, it does not think those DV files are video. I tried playing one with WMP and cant. And WMM cant load them.

---

### Post by andrew.46 on 2012-12-30
> **sdowney717 said:**
> core2 duo e6550 
8gb ddr3 

yes it is totally wimpy or is it?


Well it does have a 2.33GHz clock speed but in terms of video processing there would probably be a wimp factor involved :)

---

### Post by sdowney717 on 2012-12-30
I noticed something about kino.
We have 2 video cameras.
One is standard hi8
One is digital hi8
Both Sony.
Both types of tapes are being played back on the digital sony camera.
The tapes made on the non digital camera when ripped with kino show a video line mirror shiny what can I call it sort of like a tiny bit of the vertical frame out of place under the bottom edge of the recorded video.
That line does not show in the LCD view on the camera, but only on the video ripped from the camera. 

the tapes recorded in DigitalHi8 on this camera when ripped, do not show that line.

And the tapes recorded in standard when ripped with WMM in win7, do not show that line under the video.
So only Kino shows this when ripping non digitally recorded tapes.

Is there a way to get rid of that blanking line?

here is a screen shot, if you look along the lower edge you will see it. When watching the video it flashes around, and extends all along the lower edge. In this case by the wheel, you will see it. It is like the entire frame is pushed up too high.

---

### Post by sdowney717 on 2012-12-31
Cinelerra can render to DV codec.

[http://www.youtube.com/watch?v=jBs-biS8-y4](http://www.youtube.com/watch?v=jBs-biS8-y4)

Which is what I wanted.
As he says in the video, it is best to keep your changes in the original DV until your done doing what ever your done doing to the video. Plus your saving changes much quicker.


Can any others render to DV like this?

---

