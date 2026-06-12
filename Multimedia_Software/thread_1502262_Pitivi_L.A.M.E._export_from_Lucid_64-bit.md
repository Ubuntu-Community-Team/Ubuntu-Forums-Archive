---
title: "Pitivi L.A.M.E. export from Lucid 64-bit"
date: 2010-06-05
forum: Multimedia Software
---

### Post by arvana on 2010-06-05
Hi all, I am trying to export a video from Pitivi in a format that can be uploaded to YouTube. I found [this thread]("http://ubuntuforums.org/showthread.php?t=1483636") which suggests using an FLV muxer with the L.A.M.E. mp3 encoder. My problem is that my Pitivi doesn't list LAME as an option, and I haven't been able to get it in.

I have tried reinstalling lame from the repositories, and also building lame, ffmpeg, gstreamer, faac, x264 and pitivi from the latest source.  I simply can't get a video format to export that works in YouTube.  MP4 and other format exports don't seem to work at all, they get stuck on the first frame.

Pitivi can export OGG video perfectly, however if I try to upload that to YouTube it comes out with bad video. I've tried converting the OGG video to AVI with mencoder, but it drops a lot of frames and ends up with the audio badly out of sync.

I've run out of ideas to try -- anyone been through this before, or know of something I may be doing wrong?  I'm certainly no expert in building from source (or anything!), it just seemed like something to try...

---

### Post by dannyboy79 on 2010-06-12
looking for a solution also, i am captureing video with a dazzle hollywood dv bridge from my xbox 360 game play over firewire and first I am using Kino and not sure whether to capture into raw dv format or DV avi type 2 or even quicktime dv. I was previously using iMovie HD in a powerbook g4 that was loaned to me and it worked awesome exporting to H.264 in a mov container, you can check the videos out at my youtube channel:
[http://www.youtube.com/user/dansnewaddress](http://www.youtube.com/user/dansnewaddress)
anyway, I now need to use my lucid lynx desktop which has a texas instrument PCI firewire card. I am wondering what the best was to get my captured xbox 360 game play to youtube with decent vid. I am only capturing from standard definition using component cables into the dazzle then dazzle sends it to lucid firewire card. Can you help me out?

---

### Post by dario7 on 2010-07-03
> **arvana said:**
> Hi all, I am trying to export a video from Pitivi in a format that can be uploaded to YouTube. I found [this thread]("http://ubuntuforums.org/showthread.php?t=1483636") which suggests using an FLV muxer with the L.A.M.E. mp3 encoder. My problem is that my Pitivi doesn't list LAME as an option, and I haven't been able to get it in.

I have tried reinstalling lame from the repositories, and also building lame, ffmpeg, gstreamer, faac, x264 and pitivi from the latest source.  I simply can't get a video format to export that works in YouTube.  MP4 and other format exports don't seem to work at all, they get stuck on the first frame.

Pitivi can export OGG video perfectly, however if I try to upload that to YouTube it comes out with bad video. I've tried converting the OGG video to AVI with mencoder, but it drops a lot of frames and ends up with the audio badly out of sync.

I've run out of ideas to try -- anyone been through this before, or know of something I may be doing wrong?  I'm certainly no expert in building from source (or anything!), it just seemed like something to try...


hope this will help you out...
I followed these steps:
- Rendering
- Output file: test.avi
- Video output: 480p blablabla
- Container: ffmpeg avi format muxer (maybe someone other is better?
- audio codec: twolame mp2 (maybe mp3 is better?)
- video codec: xvid video encoder


my output file is an avi, and it works perfectly.. I didnt uploaded it on youtube yet, but I think there will be no problems ;)


edit: uploaded and it works :-) you can even select 240/360/480p quality..
enjoy the track! [http://www.youtube.com/watch?v=0vytutOwQjM](http://www.youtube.com/watch?v=0vytutOwQjM)

---

