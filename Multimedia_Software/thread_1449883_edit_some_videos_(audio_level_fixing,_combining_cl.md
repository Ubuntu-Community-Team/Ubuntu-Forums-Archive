---
title: "edit some videos (audio level fixing, combining clips, encoding)"
date: 2010-04-08
forum: Multimedia Software
---

### Post by blueturtl on 2010-04-08
The family VHS collection is in my hands and it needs to be converted to digital (some recordings are worth the trouble because they are not available as DVDs).

I have for the task a Pioneer DVR-5100H (analog video & dvd recorder), a Sony VCR and a PC running nothing but Ubuntu.

I figured the easiest way to do this would be to...

1) Use the Pioneer recorder to first transfer the VHS tape content on to rewritable DVDs.
2) Rip and edit the DVDs on the system running Ubuntu
3) Either burn new "enhanced DVDs" or distribute files digitally

My questions are as follows:

How do I rip the DVDs on Ubuntu without re-encoding them (I want as little quality loss as possible before actual editing has happened)?

What tools are available for me that can edit these ripped files? I need simple cutting and pasting plus the ability to fix the audio track in cases where it's too quiet or "hissy". I know Pitivi comes bundled, but I have never used and don't know if it can do the things I want.

If I don't want to make a DVD, how do I re-encode the files for best size-to-quality ratio in an open format like XVid? What is the best format to encode in your opinion?

---

### Post by ron999 on 2010-04-08
> **blueturtl said:**
> 

How do I rip the DVDs on Ubuntu without re-encoding them (I want as little quality loss as possible before actual editing has happened)?


The program to use is **vobcopy** from Ubuntu's repository.

---

### Post by blueturtl on 2010-04-08
> **ron999 said:**
> The program to use is **vobcopy** from Ubuntu's repository.

Can Pitivi for example work with files produced from vobcopy?

---

### Post by blueturtl on 2010-04-09
A little documentation for others: some recorders do not produce standard DVDs. This is also the case with Pioneer DVR-5100H.

Instead the burned DVD contained files like this:

DVD_RTAV/
VR_MOVIE.IFO
VR_MOVIE.VRO

While I could play the video by double clicking VR_MOVIE.VRO, obviously vobcopy did not do it's job. Also if you have more than one entry on disc, they are all contained within that single file.

After searching for a while I found a utility called [dvd-vr]("http://www.pixelbeat.org/programs/dvd-vr/")

I downloaded and extracted it ('make' to build or 'sudo make install' to install globally).

I then did this:
```
dvd-vr --name="series name" /media/cdrom/DVD_RTAV/VR_MANGR.IFO /media/cdrom/DVD_RTAV/VR_MOVIE.VRO
```

It extracted the video files as standard vobs (separately I might add) in to the working directory. Brilliant!

So far I did not find any way to normalize the audio in Pitivi though. Keeping everyone posted and thanks for all the help so far! :)

---

### Post by blueturtl on 2010-04-09
I just noticed one 20 min clip of transferred VHS takes up 1.4 gigs of space! :shock: Seems a bit steep considering the video quality isn't that great to begin with.

I really need to re-encode from VOB to another format. I've attached a poll to this now.

If someone has sane ffmpeg command defaults they want to post, I'm all for that.

---

### Post by no2498 on 2010-04-09
you try, handbrake ?
or, tragtor
or, lives

if you install, smplayer it gives you the 264 codes
type it in a terminal it tell you how to install it

hope this helps

---

### Post by blueturtl on 2010-04-09
Wow! Handbrake seems like a very mature solution. Playing with it now...

Thanks!

---

### Post by blueturtl on 2010-04-10
Handbrake does an awesome job.

I've managed to compress the 1.4 gig original to a mere 120 megabytes after encoding (H264, Vorbis audio) without a very noticeable loss in quality.

That said there's no audio normalisation feature built-in.

What can I do to restore volume proper volume level? Since video containers like MKV and MP4 hold the audio separately is it possible to post-process it without affecting the encoded video?

It would of course be best if this could be handled simultaneously with the conversion.

---

### Post by blueturtl on 2010-04-12
Found a way to separate the audio and video before encoding.

To extract audio from the .vob:
```
mplayer -vc null -vo null -ao pcm:waveheader:fast:file=output.wav vobfilefromdvd.vob
```

I can then use what ever tools necessary to fix the audio track. In my case, Audacity does a nice job but I suspect one could very well build a batch job by writing a script to.

The problem is that I can't find a way to put the files back together again.

```
mplex -f8 -o vobwithnewaudio.vob extractedvid.mp2 edited_audio.wav
```

mplex simply complains that the files are of unknown type.

There has to be a way to make this work.. but how?!

Ref. [http://blogs.tech-recipes.com/abanks/2006/11/17/mythtv-dvd-rip-vob-remove-unused-audio-tracks/](http://blogs.tech-recipes.com/abanks/2006/11/17/mythtv-dvd-rip-vob-remove-unused-audio-tracks/)

---

### Post by ron999 on 2010-04-12
Hi
You're getting there.:)

To make an audio-only track I would use this command:-
```
ffmpeg -i vobfilefromdvd.vob -vn -ar 44100 audio.wav

```
To make a video-only track I would use this command:-
```
ffmpeg -i vobfilefromdvd.vob -an -vcodec copy video.vob

```
Then modify your audio file with Audacity or whatever.

Then combine them with this command:-
```
ffmpeg -i video.vob -i edited_audio.wav -vcodec copy -acodec copy combined.vob
```

This will give you a vob file containing your original video and modified audio.
Your audio will be in wav format. I'm not sure whether it's permitted to have wav in a vob file, **maybe I'm wrong**.

So you could put your finished file in an mkv container before you encode it to mp4/m4v with Handbrake.

To put it in mkv instead use this command:-
```
ffmpeg -i video.vob -i edited_audio.wav -vcodec copy -acodec copy combined.mkv
```

---

### Post by blueturtl on 2010-04-12
ron999, thank you for your advice! I am once again closer to having this thing wrapped.

What you said works, but I am worried because when dumping/extracting both audio and video ffmpeg says it's encoding the data. I want to avoid re-encoding the files until getting them to Handbrake as much as I can. Does ffmpeg re-encode the data, or is it just an expression?

I've had some interesting experience playing with all these tools.

ffmpeg, mplayer and mpegdemux all enable me to accomplish my goals as far as extracting the video goes:

```
mpegdemux -d -s 0xe0 vobfromdvd.vob video.m2v
```
Watchable video file, no audio, size 1179348
```
ffmpeg -i vbofromdvd.vob -an -vcodec copy video.vob
```
Watchable video file, no audio, size 1193760
```
mplayer -ao null vobfromdvd.vob -dumpvideo -dumpfile dump.mpg
```
Watchable video file, no audio, size 1179352

Why are all these files different sizes even though they're supposed to be exactly the same data?

The extracted audio is exactly the same size with ffmpeg as it's with mplayer.

Recombining a .vob file did not work with ffmpeg, but I managed to make an apparently working mkv. I'm encoding said mkv with Handbrake. Will post back how it all went.

---

### Post by ron999 on 2010-04-12
Hi
Using ffmpeg with my commands, there is no re-encoding. You are just copying an audio or a video track into a new container.
That's why the process is so quick.
Even though ffmpeg says it's encoding, it isn't, it's just copying.

I think that your mplayer command is the same, just 'dumping', not re-encoding.

I can't explain why they all are different sizes. Perhaps the different containers (m2v, vob and mpg) have different 'overheads'. I dunno.

Let's see how your re-encoded mkv file turns out.
:P :P

---

### Post by FakeOutdoorsman on 2010-04-12
You can try *normalize-audio* to normalize the volume of one or more audio files.  I've used it sucessfully for short audio clips.

---

### Post by blueturtl on 2010-04-13
Success!

I got high quality H264 video along with normalized and Vorbis-encoded audio neatly laid in MKV container.

Now if I knew anything about scripting in Linux, I could probably write a script to batch process all the files... That I can however research myself, I am sure there are plenty of sources to look up. If I ever get around to it, I will post the script here.

Doing this manually allows me to do greater work on the audio (Audacity allows me to do noise removal as well).

Thanks everyone for great help. :)

---

### Post by blueturtl on 2010-04-14
I have one more question...

I've been trying to shorten some clips with excess frames from overlapping recordings with ffmpeg:
```

ffmpeg -i input.vob -ss 00:00:00 -t 00:42:20 -acodec copy -vcodec copy output.vob
```

However the produced files don't play in Movie Player (totem) and on mplayer the audio is wildly distorted or filled with static.

Is this a bug with ffmpeg or is there something I don't know?

---

### Post by FakeOutdoorsman on 2010-04-14
> **blueturtl said:**
> I have one more question...

I've been trying to shorten some clips with excess frames from overlapping recordings with ffmpeg:
```

ffmpeg -i input.vob -ss 00:00:00 -t 00:42:20 -acodec copy -vcodec copy output.vob
```

However the produced files don't play in Movie Player (totem) and on mplayer the audio is wildly distorted or filled with static.

Is this a bug with ffmpeg or is there something I don't know?
Try placing *-ss* and *-t* before the input:
```
ffmpeg -t 00:42:20 -i input.vob -acodec copy -vcodec copy output.vob
```
I omitted *-ss* because you had it set to 0.

---

### Post by blueturtl on 2010-04-14
Thanks FakeOutdoorsman! (awesome nickname btw :D )

I've already tried rearranging the parameters in various ways (I think including the way you proposed) and it hasn't worked so far.

Either they're clearly wrong (cuts encoding way too early, file way too small) or it produces a file that seems exactly the right size but has garbled audio. :confused:

---

### Post by blueturtl on 2010-04-16
The answer is, don't waste your time trying to fix the .vob files, convert to mkv and do the editing with mkvtoolnix. :)

```
mkvmerge --split timecodes:00:00:xx,00:xx:xx video.mkv -o videocut.mkv
```

---

### Post by no2498 on 2010-04-16
am glad i pointed you the right way

---

