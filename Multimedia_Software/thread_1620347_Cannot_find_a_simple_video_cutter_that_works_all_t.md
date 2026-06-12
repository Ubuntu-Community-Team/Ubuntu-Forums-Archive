---
title: "Cannot find a simple video cutter that works all the time"
date: 2010-11-12
forum: Multimedia Software
---

### Post by VideoRoy on 2010-11-12
I been struggling with this since Karmic and I know others have as well.  This is really the only thing making me keep a Windows install around for my personal stuff.

Problem: Convert .TS files to iPod or really any smaller format keeping A/V sync after edit.  I can covert my .TS file perfectly if I do not edit it but I want to just do a simple, quick  trim of 2 mins from beginning and end.

HandBrake with convert the file perfectly but cannot trim.  Avidemux does a great job on the video but I always have to play with the audio shift to get it in sync.  It is usually betwenn -250ms to -1000ms off but I cannot count on it.  If I run the video through DGIndex in Wine or view it with Mediainfo both programs detect the an offset problem but they are always wrong by almost 500ms and it is never constant.

Regular video editing I have pretty good luck with my normal DV files and I could even run the .TS files through other programs but it is too time consuming to be useful form this simple task.  Anytime I want to take my recorded TV .TS files I cannot edit them quickly without making a full project out of it in Openshot Cinelerra, etc.

Has anyone found a quick, reliable way to do some lite video trimming in Ubuntu and keep A/V sync without having to resort to any Windows programs?

EDIT: Also I really do not want to resort to have to demux separately either.  I know I am asking a lot but I got spoiled with a couple of Windows programs that will edit without reencode programs like VideoReDo can do the editing and converting all at once (for $100 !).

Thanks in advance.

---

### Post by bryanl on 2010-11-13
ditto!

I don't understand the audio sync problems when some, like avidemux, have severe problems with it and many others don't.

I haven't yet found a video editor good for simple cutting of large files like avidemux, either.

I haven't found solutions like ProjectX to be of much use, either. VLC or Handbrake to encode to another file type doesn't help much either.

And then there's the problem of trying to edit MP4 files.

then there's the Hauppage video capture card problem in Linux but that is another story. There is yet a long ways to go here.

---

### Post by VideoRoy on 2010-11-13
> **bryanl said:**
> ditto!

I don't understand the audio sync problems when some, like avidemux, have severe problems with it and many others don't.

I haven't yet found a video editor good for simple cutting of large files like avidemux, either.

I haven't found solutions like ProjectX to be of much use, either. VLC or Handbrake to encode to another file type doesn't help much either.

And then there's the problem of trying to edit MP4 files.

then there's the Hauppage video capture card problem in Linux but that is another story. There is yet a long ways to go here.
Thanks for the co-misery :P

I had minor success with tsmuxer today.  I ran my .TS file through and did nothing but strip out the secondary audio track (Spanish I think).  It only took about a minute or so and the audio was almost in synce in Avidemux after a quick edit.  It was off by just a maybe 100ms or so.  Still detectable but close enough that I will play with tsmuxer a little more and see what other settings might help.

I have read that the folks at Avidemux may be working on a fix in version 2.6 but I could not quite get all the steps right to compile and give it a shot.  I may have to wait for the official release whenever that is.

Unfortunately, I am getting ready to plunk down $50 for the cheap version of VideoReDo and do these in Windows if I cannot make it work.  I have about 75 .TS shows I want to edit / convert that I have been waiting to do since the beginning of the year.

---

### Post by cchhrriiss121212 on 2010-11-13
Have you tried handbrake for converting then openshot for trimming?

---

### Post by VideoRoy on 2010-11-13
> **cchhrriiss121212 said:**
> Have you tried handbrake for converting then openshot for trimming?
Thanks for the reply.

Yes, I actually did that as well.  The problem there was OpenShot does not have a profile that I could find that was just Copy or something similar so it has to reencode again.  More time and more loss.

To be fair I have not spent a great deal of time in OpenShot yet learning all the details but from the docs I could not find a quick way to do this so it would not reencode.  I also tried bringing the .TS file directly to OpenShot with mixed results.  Very slow to encode.

I have found a solution to my current situation.  Since I have 75 or so 30 min programs to edit  / convert, I know the where the beginning and end is pretty well due the padding I put into my recorder. So here is what I do:

1. Run .TS through TSmuxer and use the cut option.  I tell it to start at 2min end at 30 min.  I save the file back as .TS but I do take the time to remove the unwanted Audio tracks (this might be a waste of time but I will test that).

2. Take .TS file created with TSmuxer and run it through Handbrake.  Almost all the profiles in the current version work pretty good for me so no tweaking required.

--------------------------------------
Other thing I tried was to use TSMuxer to demux A/V then edit with Avidemux since I have read that works better.  It doesn't.  Followed a could of guides but still OOS A/V.

So, I did not use Avidemux at all and keep everything in Linux.  I really do like the Avidemux program as an idea but so far I have not found a media type I can use that will keep A/V sync once edited.  I really hope that team keeps working on it and makes Audio Sync work easier.  Nice application with great features and just one problem for me at least that is a show stopper.

So for quick trims I will use this process and now that I am getting back to camera work I will start playing with OpenShot and others for original footage.

---

### Post by VideoRoy on 2010-11-13
Turns out this is not exactly perfect either.

TSmuxer automatically reads in the audio delay that is in the file which by the way is what is shown in Mediainfo.  The problem is as I have discovered this number is always off by ~200ms or so.  At least now the number is already pre-populated and I can just add an arbitrary -200 ms and it gets pretty darn close and the whole process takes my about 10 minutes to run through TSmuxer and Handbrake.  Not bad at all.

A couple notes about Handbrake.  If I take the raw unedited file without going through TSMuxer the A/V sync is dead on every time.  I forget which encoder is used in Handbrake but either it is figuring out the real offset on or something else in the program is doing it.

Also another great thing about Handbrake is I am getting 100fps speed on my Ubuntu 64bit workstation compared to about 50fps I was getting in Avidemux for roughly the same settings.  Awesome!

If nothing else I have learned a lot about the tools available today for Ubuntu.

---

### Post by FakeOutdoorsman on 2010-11-13
Have you tried FFmpeg for cutting and trimming?
```
ffmpeg -ss 00:02:43.00 -i input -t 120 -vcodec copy -acodec copy output
```
The *-ss* option tells FFmpeg to skip the first 2 minutes and 43 seconds of the input. The *-t *option tells FFmpeg to create an output that is 120 seconds long.  My example shows two methods of declaring time: **hours:minutes:seconds:milliseconds** or just **seconds**, and *-ss* and *-t* can use either method.

Using *-ss* as in input option (before the *-i*) is usually faster than applying it as an output option (after *-i filename*) as it instructs FFmpeg to seek to that time and then decode, but it isn't always accurate (depending on your input format) so you may have to move *-ss* as an output option. As an output option this tells FFmpeg to decode everything until your desired time and then start encoding. This method can be much slower depending on how decoding intensive your input is, but is potentially frame accurate.

The *-vcodec copy* and *-acodec copy* options tell FFmpeg to simply copy the video and audio.  This preserves the quality and is fast because there is no re-encoding.

---

### Post by Devport on 2010-11-13
dvbcut ( [http://dvbcut.sourceforge.net/](http://dvbcut.sourceforge.net/) ppa @ [https://launchpad.net/~bojo42/+archive/dvbcut](https://launchpad.net/~bojo42/+archive/dvbcut) ) lets you cut ts frame accurate without demuxing and with smart encoding. It exports an mpeg which you can recode with handbrake.

Once you get used to it its fast and reliable. Use mouse wheel to scroll, for smaller steps press shift / control key.

---

### Post by VideoRoy on 2010-11-14
> **FakeOutdoorsman said:**
> Have you tried FFmpeg for cutting and trimming?
```
ffmpeg -ss 00:02:43.00 -i input -t 120 -vcodec copy -acodec copy output
```The *-ss* option tells FFmpeg to skip the first 2 minutes and 43 seconds of the input. The *-t *option tells FFmpeg to create an output that is 120 seconds long.  My example shows two methods of declaring time, and *-ss* and *-t* can use either method.

Using *-ss* as in input option (before the *-i*) is usually  faster than applying it as an output option as it instructs FFmpeg to  seek to that time and then decode, but it doesn't always work as  expected so you may have to move it past the input.

The* -vcodec copy* and *-acodec copy* tell FFmpeg to simply  copy the video and audio.  This preserves the quality and is fast  because there is no re-encoding.

> **Devport said:**
> dvbcut ( [http://dvbcut.sourceforge.net/](http://dvbcut.sourceforge.net/) ppa @ [https://launchpad.net/~bojo42/+archive/dvbcut]("https://launchpad.net/%7Ebojo42/+archive/dvbcut") ) lets you cut ts frame accurate without demuxing and with smart encoding. It exports an mpeg which you can recode with handbrake.

Once you get used to it its fast and reliable. Use mouse wheel to scroll, for smaller steps press shift / control key.

Thank you very much for both suggestions I will give them both a try.  I was headed towards the FFmpeg route already but it has be a couple of years since I have played with it.  I just saw there were a couple of front ends for it as well.

Also I think I actually used and early version of dvbcut but I will check it out again.

The help is much appreciated!

---

### Post by VideoRoy on 2010-11-14
@Devport,
I tried installed dvbcut and it seemed Ok until I loaded my video.  Once the video indexed and displayed on screen the entire application bled off the each of my screen and no matter what I did I could not resize the window.  Finally just had to terminate it.  I noticed it said it is QT application but I am not that familiar with that interface and thought it might have something to do with it.  I played around for about 30 minutes and gave up.

When I get some more time I will revisit it and do some more research.

@FakeOutdoorsman,
I ran the line you gave me almost exactly with my own parameters of course and it appeared to work the first time!  I ran the resulting .TS in VLC and no OOS all the way through.  Just got done running through Handbrake and the sync is dead on all the way through!

Running through ffmpeg took about 2 minutes and Handbrake takes 8 min so this might be a great process for these very simple cuts / encode.

Thanks very much for the help folks! :cool:

For more complex editing I will continue to search and may still have to resort to WinDoze.

---

### Post by VideoRoy on 2010-11-15
Ok, I think I can mark this one solved after trying a bunch of things.  Also maybe I will write up a little more detailed but I found a great process for editing the .TS Transport Stream files that I record from BeyondTV.

How to edit in Avidemux and keep A/V sync with the least amount steps.
Get these tools:
A) Avidemux I am using v2.5.4 from GetDeb.net
[http://www.getdeb.net/updates/Ubuntu/10.10/?category=Video%20Tools]("http://www.getdeb.net/updates/Ubuntu/10.10/?category=Video%20Tools")

B) MediaInfo I am using 7.36 from Sourceforge (great tool and must for video inspection)
 [http://mediainfo.sourceforge.net/en](http://mediainfo.sourceforge.net/en)

C) FFmpeg I am using the version 0.6-4 that was installed in Ubuntu 10.10.

Steps:
1. Run the .TS files through a stream copy in FFmpeg.  Thanks to the suggestion in this thread that was my "ah ha" moment.  My .TS files the audio offset was always wrong in my .TS files when viewed from MediaInfo.  Usually about 250ms (quarter second) but rather random.  Once I ran a stream copy of the video, FFmpeg stripped out the extra audio track and fixed my offset.

I ran my whole directory of 40 videos all a once with this bash script:

> for i in *.ts 
   do ffmpeg -ss 00:02:00.00 -i $i -t 1680 -vcodec copy -acodec copy ~/Videos/TempTS/trim-$i
doneBasically it says seek 2 min then copy 28 min to the directory specified.  It appends "trim" to beginning of the file name.  You could probably play with FFmpeg and not trim at all but for me this gets rid of the padding at the beginning scraps some junk at the end.  I did 40, 30min HD videos in about an hour (3gigs each).

2. Run MediaInfo and inspect the new file. I select HTML view then go to the Audio section in the output and look for:
> Video delay : -805ms Note my Video delay is -805ms for this particular video.

3. Run Avidemux and edit your video how ever you like but before you save or encode the video make sure to check the "Shift" box in the Audio section on the main page and put the offset you got from MediaInfo.  In my case for this one video it was -850.

4. Done.

Sounds a bit complex but it is not and goes pretty quick.  I have found that many .TS streams from recorded TV have issue so that many video tools have issues.  This is a quick and easy method to fix them.

Note: If you do not want to edit at all you could either just encode directly with FFmpeg or I have found Handbrake 0.9.4 (current as of this post) to always get the offset correct and A/V sync is perfect.

Thanks to those you helped me figure this one out.

---

### Post by arod0405 on 2010-12-05
I'm having the same problem with mpeg-ps files I get from my strong 5222 dvb-t tuner: vlc plays fine the raw mpeg file but I can't cut with avidemux without losing audio sync. 
ffmpeg does a great job cutting files without losing sync but I need a GUI for refined cuts (ads and all).

I've tried the steps recommended above: ffmpeg, mediainfo -> delay, avidemux, but the result nearly acceptable because a slight delay remains.

I got good results with dvbcut. It has an ugly super-old qt style GUI that doesn't even fit in gnome desktop (somehow I can't resize its window), but it works! Last dvbcut version is from 2007 and looks like code is unmaintained.

---

### Post by arod0405 on 2010-12-05
I've just tried using project-x, as suggested in avidemux's wiki:
[LIST]
[*]demux mpeg file (audio/video async) with project-x
[*]mux video and audio with mplex -f 8 (audio/video sync now)
[*]edit with avidemux
[/LIST]

And it works too! My file had some errors (don't know if due to trasmission or I/O with storage) and I got more frames skipped than with dvbcut, but the result is fine and almost pain-free.

So that's another viable solution for me.

---

### Post by VideoRoy on 2010-12-05
> **arod0405 said:**
> I've just tried using project-x, as suggested in avidemux's wiki:
[LIST]
[*]demux mpeg file (audio/video async) with project-x
[*]mux video and audio with mplex -f 8 (audio/video sync now)
[*]edit with avidemux
[/LIST]

And it works too! My file had some errors (don't know if due to trasmission or I/O with storage) and I got more frames skipped than with dvbcut, but the result is fine and almost pain-free.

So that's another viable solution for me.
Glad that work for you.  I tried Project-x as well but it too is unmaintained and I had a few problems.  Also I did not have good luck with demux / remux in Avidemux for some reason my sync was still off.

Any way nice to see you found a solution that works too.

---

### Post by arod0405 on 2010-12-06
> **VideoRoy said:**
> Glad that work for you.  I tried Project-x as well but it too is unmaintained and I had a few problems.  Also I did not have good luck with demux / remux in Avidemux for some reason my sync was still off.

Any way nice to see you found a solution that works too.

I don't know if it's relevant but I'm running debian sid (not ubuntu) and using project-x from the debian repository, not the one from doom.org.

---

### Post by arod0405 on 2010-12-06
Here reporting again.

Made some more experiments with mpeg-ps files from my dvb-t set-top-box.
I'm not satisfied with projectx+mplex results. Sync is ok but the process produces too many errors and I can hear hiccups on audio. Moreover, minutes later audio track dies. mplayer says "Too many video packets in the buffer: (4096 in 8247232 bytes)."

Dvbcut seems to do the job.

I'll try projectx again with an mpeg-ts stream.

---

### Post by arod0405 on 2010-12-06
I've got better results with a TS stream and project-x. Still got over 500 errors (dropped frames I guess) but no audio hiccups or audio track dying. I don't know if it's because of TS and .drv files or because the stream came from another channel that could have a better signal.

I even gave a try at kdenlive with some older mpeg-ps stream and it works too. Maybe overkill, ok.

---

### Post by VideoRoy on 2010-12-06
I like Avidemux for simple editing and exporting back out to TS files without much encoding.

If I am going to do a lot of editing then I covert the file to .AVI and us it in OpenShot or kdenlive.

Not too many editors will natively handle high bitrate HD streams in Linux yet.

---

### Post by michael37 on 2011-11-23
Just want to say +1 for ProjectX which has performed magnificently when using the latest version.

I use ffmpeg or mkvmerge to mux after projectx demux -- mplex fails too often.

Do use latest version of ProjectX though -- it's not available in repositories. More details (and vote for this bug) at [https://bugs.launchpad.net/ubuntu/+source/project-x/+bug/892671](https://bugs.launchpad.net/ubuntu/+source/project-x/+bug/892671)

---

