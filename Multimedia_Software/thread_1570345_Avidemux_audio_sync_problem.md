---
title: "Avidemux audio sync problem"
date: 2010-09-08
forum: Multimedia Software
---

### Post by prabath_fun on 2010-09-08
Hi,
  I used avidemux to convert DVD/VOB file to MP4/MKV. But, final output is with audio out-of-sync with video. Video leads the audio.
I tried “shift” option in avidemux. This leads some other problem that, few places audio lead the video and few places video leads the audio.
Further, I want to convert the video with x264 codec and copy the second audio track (Basically DTS audio) from the VOB file. To do so, I selected Video (x264), Audio-> Main track -> DTS….. and format “AVI”. In this case, audio out-of-sync problem. If, I select Format as “MP4” or “MKV”, I am getting message that, “selected frame is not start off frame, move the marker A” even, I move the marker using double arrow button.
Also, let me know, what will be format to extract DTS audio bit on bit…. That is, without losing samples and bit rate using Avidemux…
Kindly help me to solve this problem.

---

### Post by prabath_fun on 2010-09-13
Help / guide me, please...

---

### Post by kevxh on 2010-12-28
Do you still have this problem? I've been struggling with this myself for so long.
I don't know enough about audio/video encoding delay and such (and really have no interest in learning as I don't do it that often) so I've been playing with alternatives.

I found a really good (and simple) solution with xvidenc. It's in the repositories, it's just a script that uses mencoder but it's very good and so far has been 100% accurate for everything I've used it for. It'll rip dvds too. I haven't tried cropping yet but I'll be looking at that over the holidays.

Anyway, after being frustrated for so long with avidemux this is the best solution I've found. If you found a solution yourself let me know.

Kev

---

### Post by prabath_fun on 2010-12-30
Hi,
  I have not found solution  for this yet. I will try xvidenc. I possible please post script you are using. Advanced thanks...

---

### Post by kevxh on 2010-12-30
xvidenc is the script. It just runs from the terminal. It will ask a few questions but the default is ok for almost all of them. I ripped a DVD with it last night and I'm really pleased, the end result is perfect.
I haven't tried the DTS track as I MP3 the audio anyway but I'll try one and see what happens.

Install the script with sudo apt-get install xvidenc mplayer mencoder lsdvd
Then run it with xvidenc and it will start asking questions
The only defaults I don't change are - 
the telecine if it's a NTSC DVD i'm ripping (essential)
the audio because I MP3 the AC3 stream
the bitrate which I up to 1280

Try it out and if you're still having problems post back here and I'll write a howto for you

Kev

---

### Post by prabath_fun on 2010-12-30
Thanks for your brief, Kev.
  I got the thread ([http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)) to convert DVD to mkv format with no change in audio (AC3), which I was looking for. 
  But, it crops the video. Instead I am looking for resizing the video. If you have any idea, please let me know. 
My understanding: Crop-cuts some portion of sides of the video frame. Resize - complete image will be available only pixel across line will get changed. Is it correct???

---

### Post by vanadium on 2010-12-30
"man mencoder" will tell you everything about mencoders options. "scale" is used for scaling the video.

Nowadays, you should not rescale the frame if good video quality is your first concern, and you are ripping to mkv. This will minimie quality loss. Similar as when you play a DVD, the aspect ratio by which the video is encoded, is corrected during playback.

Cropping out black bars will gain in filesize. Besides, black bars encoded in the video stream are of no use. Thus, cropping you should, resizing not.

A good reason to rescale is when you target low bandwith, e.g. for distribution over the internet, or when reencoding for a portable device, etc...

---

### Post by prabath_fun on 2010-12-30
Thanks vanadium

---

### Post by kevxh on 2010-12-30
You're welcome.

As vanadium has said, scale with mencoder but only if you want to really shrink the output. If you're storing the audio as AC3 then I expect you want the video in high quality too.

I'd be interested to know how you get on.

Kev

---

### Post by prabath_fun on 2010-12-31
Hi vanadium and kevxh,
   I have not tried DVD ripping and encoding.
   I tried cropping 1800 x 1280 resolution video to 1240 x 720 (I am not remembering exact pixels selected, but, it is very near to what I have tried)by picking command from ([http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)). The final outcome is right side major portion and bottom major portion of video went missing after cropping using mencoder and x264 format.
  I have not tried resizing yet. Because, I don't know commands on mencoder. I started go-through commands. If, I get good result, will post here.

  Please through some idea to achieve it easily. Advanced thanks.

---

### Post by kevxh on 2011-01-01
That's very large format, I didn't realize you were dealing with video that big. I assumed it was a movie with black borders that you wanted to remove so yes of course cropping isn't any good for you (sorry!).

The ratio for 1800x1280 is 1.40625 so use mencoder with -vop scale=1012:720
the default bilinear filter will be used which produces good results.

Kev

---

### Post by prabath_fun on 2011-01-03
Hi Kevxh,
   Thanks. I will try and update you.
  If DVD conversion, I am not looking only to remove black border. I am looking for encoding the video with x264 codec with resolution as is along with DTS or / and Ac3 audio basically to reduce the size of full length movie and to share / save it in my external harddisk.
  Will try both sometime and update the result.

---

### Post by BicyclerBoy on 2011-01-04
HandBrake can rip DVD to H264 using x264 encoder...

Very nice GUI & up to date with DVDs navigation issues.

---

### Post by prabath_fun on 2011-01-05
Hi BicyclerBoy,
   I have tried Handbrake, Avidemux, etc., for DVD to x264 encoding. I am getting audio sync problem with most of the DVD's....

---

### Post by BicyclerBoy on 2011-01-05
I have used/tried all of these programs mentioned except the script..

No A/V sync problems found so far, none with DVD material.

Maybe the A/V sync problem is a playback problem not transcoding..

What do you use to playback mpeg-4/10 H264 material ?

The playback would be much better using nvidia hardware (vdpau video decode).

note: inverse telecining should only be used to fix film material that has been badly transferred to DVD. Should not be needed very often. A similar method to telecining is sometimes used to convert between PAL-NTSC.

---

### Post by prabath_fun on 2011-01-05
Hi BicyclerBoy,
   I use on-board hardware which is ATI radeon xpress-200 based. I have played so high resolution videos also, No problem. So, hope, there is some problem with decoding only. I have tried even windows version of avidemux, Handbrake, etc., same problem.

---

### Post by kevxh on 2011-01-05
Bicyclerboy, I've had exactly the same problems. Handbrake, DVD::Rip, OGMRip, everything produces a choppy video, the audio out of sync, or more often both. I've tried everything and so far nothing has worked.

The only thing I've found to work so far is xvidenc script, yet I still have problems but they're reduced. No offence intended but it's really frustrating when people say "this works fine for me".

I've found that if I use mencoder with copy on both audio and video streams to produce an mpeg2 and then encode that to xvid/mp3 the results are far better.

Kev

---

### Post by BicyclerBoy on 2011-01-05
I understand your frustration..

I was just making you aware that it can work okay & there must be a solution.

With a lot of the video transcoding programs you need to build a recent release.

Are you using the latest HandBrake from stebbins-handbrake-snapshots ppa ?

The ffmpeg libraries in the standard ubuntu repos are stripped/cut-down.
(libavcodec, libswscale etc)
Make sure you have the (7) -extra packages from medibuntu.
I think "ubuntu-restricted-extras" package pulls in some of these.

The good bad & ugly gstreamer codec packages are not installed by default.

Build ffmpeg with x264 from source & use it on unencrypted source.

I doubt that 8 year old radeon IGP GPU is able to decode any H264 video or MPEG-2..
Playback of HD video is 2 things : decode & presentation.

---

### Post by kevxh on 2011-01-05
I've just switched to Xubuntu (the performance boost is amazing) so I used the restricted extras package for codecs. I'll rip something as a test tonight and post my findings.

I agree that there *must* be something amiss somewhere for this issue to exist, it's just really bizarre ...

Thanks for your thoughts ... I'll let you know what happens.

---

### Post by prabath_fun on 2011-01-06
Hi Bicyclerboy,
 If you provide the steps how you have installded complete package required for Handbrake, I will give a try. Moreover, I am using Ubuntu9.10 as 10.04/10.04.1 freezes on my desktop....

---

### Post by kevxh on 2011-01-06
Well ... I ripped a DVD with Handbrake and the end result is perfect.

I've had this issue for a long time, back as far as 8.04 at least. Now I'm using Xfce instead of Gnome I have no problems. Encoding isn't noticeably faster but the end results are what matters. So is this a Gnome issue? Is there something going on with streams? Xubuntu is still using gvfs, maybe the buffering is different.

It's a drastic step I know. After trying Xfce for a few days I was so impressed I cleaned my machine and have a fresh install of Xubuntu. So who knows what exactly is going on there.

I might have a look at how the vfs is flushing buffers.

---

### Post by JohnAStebbins on 2011-01-06
> **prabath_fun said:**
> Hi Bicyclerboy,
 If you provide the steps how you have installded complete package required for Handbrake, I will give a try. Moreover, I am using Ubuntu9.10 as 10.04/10.04.1 freezes on my desktop....

```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk

```
Ubuntu 9.10 is supported by this PPA

---

### Post by prabath_fun on 2011-01-06
Hi All,
   I tried DVD encoding to x264 with mencoder in command lines with help of webpage ([http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)). Here also, I end up with audio sync problem again. Moreover, I have to tell audio delay problem.
   As per DVD, audio should start after few seconds (That is, during film certification video and displaying thanks for contributers, DVD playback gives no audio stream selection option and later it is. With help of VLC I found), but, after encoding, audio starts along with video. Anybody have thought on this?

Hi JohnAStebbins,
   Thanks. I will try this night...

I tried xvidenc, suggested by kevxh, I could not able to trace where the encoded file is. I gave path for output file while prompted and during encoding, no file addition on that folder. So, I stopped and thought of going through xvidenc help pages...

---

### Post by kevxh on 2011-01-08
The third question asked by the script is the filename for the output, it will suggest a default of Xvid-XXXXX where XXXXX is a random number ie Xvid-16898

Kev

---

### Post by Happy Frog on 2011-03-13
As this isn't marked as solved I have a further comment:

I found that pulse audio was to blame for a variety of audio sync issues. After spending an unfortunate amount of time playing with various parameters I happened to read an article about pulse audio and its architecture which got me thinking, so I went off and learned how it works. Whilst the architecture makes sense it really isn't the best way to do it, essentially you're at the mercy of scheduling which is a bad idea if your machine isn't very fast.

Selecting ALSA in the avidemux options won't help because it's routed through pulse anyway. So the only real option is to remove pulse audio altogether.

A short while ago I changed from gnome to xfce and found the audio problem to be lessened which is what started me thinking in this direction. Then after learning how pulse works it made sense that scheduling was to blame. I don't know if the 2.6.38 kernel with its desktop oriented scheduling will make any difference here but it's a possibility. Sadly, I'd already remove pulse (and therefore solved the problem) before I installed the 2.6.38 kernel so I couldn't say if there would be an improvement.

Anyway, I hope that helps.

---

