---
title: "Faulty avi's to mp4 help"
date: 2011-06-19
forum: Multimedia Software
---

### Post by pssturges on 2011-06-19
Hi,

Firstly, appologies for the length and detail in this post, but I thought best to provide as much detail as possible.

**Background**
I have several hundred video files that are mostly sourced from PAL dvd's. They have mostly been encoded as h264 and put into avi containers with the original ac3 soundtrack. I can't remember the precise command, but I used ffmpeg to acheive this. These have been mostly played on xbmc and in that capacity there have been no major issues. As myself and other family members have several iOS devices capable of playing this type of content, it would be good if I could transfer them to mp4 containers with aac audio for playback on those devices and still have them avaiable to play on xbmc.

**My Aim**
I'm trying to create a simple script to achieve this. Without going into the detail of the script, basic function is as follows:
1) mux avi into mkv using mkvmerge
2) demux mkv into elemental streams using mkvextract (steps 1&2 seem to be necessary because I can't get step 3 to work extracting the elemental streams any other way)
3) Hack the h264 stream so that it appears to be level 4.1
4) encode ac3 stream to aac using ffmpeg
5) mux h264, aac, and ac3 streams into mp4 using mp4 box.

**The Problems!**
All this works correctly and I get a working mp4 file at the end. The resulting file does, however have audio sync issues. Now interstingly if I do ffmpeg -i on the original avi, it shows the frame rate as 29.97, not 25 as it should be as it's sourced from a PAL dvd. XBMC plays the video at 25fps and audio pretty much stays in sync. 

Now, if I force mp4box to mux it at 25fps the audio starts in sync, but slowly drifts out and by the end of the movie, there is about a 1 sec diff.

Interestingly if I do MP4Box -info on my finished file, I get:
```
* Movie Info *
	Timescale 600 - Duration 01:51:49.086
	Fragmented File no - 3 track(s)
	File Brand M4V  - version 0
	Created: GMT Sun Jun 19 09:28:39 2011

File has root IOD
Scene PL 0xff - Graphics PL 0xff - OD PL 0xff
Visual PL: AVC/H264 Profile (0x15)
Audio PL: AAC Profile @ Level 2 (0x29)
No streams included in root OD

iTunes Info:
	Name: Me, Myself and Irene
	Genre: Adventure
	Created: 2000
	Cover Art: JPEG File

Track # 1 Info - TrackID 1 - TimeScale 25000 - Duration 01:51:48.000
Media Info: Language "Undetermined" - Type "vide:avc1" - 167700 samples
MPEG-4 Config: Visual Stream - ObjectTypeIndication 0x21
AVC/H264 Video - Visual Size 704 x 544 - Profile High @ Level 4.1
NAL Unit length bits: 32
Pixel Aspect Ratio 11133:34464 - Indicated track size 704 x 544
Self-synchronized

Track # 2 Info - TrackID 2 - TimeScale 48000 - Duration 01:51:49.034
Media Info: Language "Undetermined" - Type "soun:mp4a" - 314486 samples
MPEG-4 Config: Audio Stream - ObjectTypeIndication 0x40
MPEG-4 Audio AAC LC - 2 Channel(s) - SampleRate 48000
Synchronized on stream 1

Track # 3 Info - TrackID 3 - TimeScale 48000 - Duration 01:51:49.088
Media Info: Language "Undetermined" - Type "soun:ac-3" - 209659 samples
	AC3 stream - Sample Rate 48000 - 2 channel(s) 16 bits per samples

```

You'll notice that there is just over 1 second's difference between the duration of the audio and the video. It seems this is why the audio is getting out of sync. It seems that the duration of the video is calculated by using the total number of frames (which is given in mp4box -info) and dividing by fps.

One possible solution I have considered, is trying to determine the total number of frames before muxing to mp4, then calculate the fps based on that and the duration of the audio. In the case above the fps would be something like 24.99. I could then use this when muxing to mp4.

Does this seem a valid solution and would it work? If so, is there any way to determine the total number of frames at some earlier stage in the process(avi, mkv, or elemental) that can be used in a script?

Or, is there a better solution?

Thanks for any help,
Phil

---

### Post by handy on 2011-06-20
HandBrake should accept the .avi format as an input, it will very happily make .mp4 files for you & also gives you a great deal of control over the output.

I've been using HandBrakeCLI for sometime & find it to be an absolutely brilliant tool for ripping/transcoding.

I hope it can solve your problem.

[http://handbrake.fr/details.php](http://handbrake.fr/details.php)

---

### Post by pssturges on 2011-06-20
> **handy said:**
> HandBrake should accept the .avi format as an input, it will very happily make .mp4 files for you & also gives you a great deal of control over the output.

I've been using HandBrakeCLI for sometime & find it to be an absolutely brilliant tool for ripping/transcoding.

I hope it can solve your problem.

[http://handbrake.fr/details.php](http://handbrake.fr/details.php)

I whole heartedly agree. I encode any new videos with handbrake. I could feed my existing avi's into it, but it would re-encode the video stream which will take some time and result in some quality loss. 

As my video streams are already encoded how I need them, I simply want to transcode the audio and move them to an mp4 container. Shouldn't take more than about 15mins for each video and have no further loss in picture quality.

BTW, I've been looking at more videos from my collection and some of them have upto 6 secs differnce between the duration of the audio and the video, does that seems odd??!!

Cheers
Phil

---

### Post by handy on 2011-06-20
> **pssturges said:**
> 
I whole heartedly agree. I encode any new videos with handbrake. I could feed my existing avi's into it, but it would re-encode the video stream which will take some time and result in some quality loss. 


Sorry, I obviously didn't read your post as thoroughly as I should have. :)

> **pssturges said:**
> 
As my video streams are already encoded how I need them, I simply want to transcode the audio and move them to an mp4 container. Shouldn't take more than about 15mins for each video and have no further loss in picture quality. 

It is certainly worth doing it that way as far as the time saving is concerned, if nothing else.

> **pssturges said:**
> 
BTW, I've been looking at more videos from my collection and some of them have upto 6 secs differnce between the duration of the audio and the video, does that seems odd??!!

Cheers
Phil

Some vids have no sound at the start. I don't know if that is what the story is?

---

### Post by FakeOutdoorsman on 2011-06-20
> **pssturges said:**
> I have several hundred video files that are mostly sourced from PAL dvd's. They have mostly been encoded as h264 and put into avi containers with the original ac3 soundtrack.
Generally, AVI isn't a recommended container for H.264 *with b-frames*.

> **pssturges said:**
> 3) Hack the h264 stream so that it appears to be level 4.1
How are you doing this step? Maybe you should show your complete script.

> **pssturges said:**
> Or, is there a better solution?
If it wasn't for step 3 (I'm unsure what you're doing there), you could do all of this in one step:
```
ffmpeg -i input.avi -vcodec copy -acodec libfaac -aq 100 -ac 2 output.mp4
```

---

### Post by pssturges on 2011-07-03
> **FakeOutdoorsman said:**
> Generally, AVI isn't a recommended container for H.264 *with b-frames*.


How are you doing this step? Maybe you should show your complete script.


If it wasn't for step 3 (I'm unsure what you're doing there), you could do all of this in one step:
```
ffmpeg -i input.avi -vcodec copy -acodec libfaac -aq 100 -ac 2 output.mp4
```

This is a project I've had kicking around for a few months. When I first started playing around with it, I had tried something similar but kept getting errors so abandoned that and persued the the demuxing and remuxing route. Initially, i was demuxing using ffmpeg dumpaudio/dumpvideo. When I tried to remux using MP4Box, I was getting an error saying that the video stream was not compatible. So after a bit of googling if found a thread that was talking about converting mkv's to mp4 for psp's. In that, they were talking about the hack that I was using. So, I thought I'd try muxing my avi's to mkv's then follow the process they were using in the thread, including the hack. This is pretty much the point I was at when I made my original post.

Now, since then I've determined that the hack is entirely unnecessary and the problem was in the demuxing using ffmpeg dumpaudio. So I've spent many hours demuxing using MP4Box(I hadn't realised MP4Box could demux avi's), encoding the ac3 to aac with ffmpeg, then remuxing video, aac and ac3 to mp4 with mp4box. This always resulted in out of sync audio. I tied adjusting the framerate sightly and also adding delay. I could never get things to be in sync all the way through the movie.

So, today I thought I'd give ffmpeg another go. After, some research and testing I came up with the following command:
```
ffmpeg -i video.avi -vcodec copy -acodec libfaac -ac 2 -ab 160k video.m4v -acodec copy -newaudio
```

This works really well! Well,almost. The audio is perfectly in sync. The picture when played on xbmc is great. However, when I play it on an ios device, the picture shimmies and shakes. To me it 'feels' like an interlacing issue, but I'm really not sure. When I play videos created by the demuxing/remuxing method, this issue is not present. It's seems to be a problem introduced by ffmpeg. Is there, perhaps a some bit of the mp4 container that needs to specify that the video is interlaced for ios devices to handle it correctly?

Perhaps the problem is something completely different?

I think I'm getting very close to solving this. Any help to fix this last issue would be much appreciated.

Cheers
Phil

---

### Post by pssturges on 2011-08-03
It's amazing (and very frustrating) how when you are trying to solve a problem your very first attempt can be sooo close to the final solution. Yet it takes many different attempts, trying many varied things, only to go full circle and find the solution is a minor variation on your very first attempt. In this case, after several months working on and off on this, asking in several forums, the very simple solution is below:

```
mkvmerge -o video.mkv video.avi
ffmpeg -i video.mkv -vcodec copy -acodec libfaac -ac 2 -ab 160k video.mp4 -acodec copy -newaudio

```

I don't know why muxing the original avi to mkv allows ffmpeg to be able to handle it better, but it seems that it does. Perhaps there's a bug with how ffmpeg handles avi's?

Anyhow, this one is now (finally) solved. \\:D/
Thanks for all the help,
Phil

---

