---
title: "[SOLVED] Transcoding woes."
date: 2008-11-12
forum: Mythbuntu
---

### Post by kelliott on 2008-11-12
I am running Mythbuntu 8.10 on an AMD64 platform and have no trouble recording SD and HD shows via firewire on my SA 4250HD box.  For the most part, I can even stream these via the built-in UPnP server to my PS3 via wireless without any issues.  However, if I want to copy a file to my PS3, it almost always shows up as Unsupported or corrupt.  So, I have tried to transcode these recordings using either mythtranscode or ffmpeg.

I have found many articles on removing commercials ([http://www.mythtv.org/wiki/index.php/Script_-_RemoveCommercials]("http://www.mythtv.org/wiki/index.php/Script_-_RemoveCommercials")), cleaning up recordings for PS3 ([http://www.mythtv.org/wiki/index.php/PS3_GameOS]("http://www.mythtv.org/wiki/index.php/PS3_GameOS")), auto-transcoding recordings ([http://ubuntuforums.org/showthread.php?t=346778&page=1]("http://ubuntuforums.org/showthread.php?t=346778&page=1")) as well as many others.  However, the problems I still face are:

1) The remove commercials script, while it runs successfully, doesn't actually remove the commercials from the .mpg recording.
2) When I try to use ffmpeg -vcodec copy -acodec copy to "clean up" a recording, the first part of a recording (such as the transition from a channel change or the commercials that were playing when the recording kicked off) is the only thing that gets copied into the new file.  The rest of the recording (such as the whole show or movie) is ignored, resulting in a tiny file of about 3-5 seconds.
3) I have never been able to use nuvexport or ffmpeg to copy my files to Xvid, DivX or any other format, due to incorrect versions of x264, ffmpeg, mencoder, etc.  I've removed everything, recompiled each (via [http://ubuntuforums.org/archive/index.php/t-786095.html]("http://ubuntuforums.org/archive/index.php/t-786095.html")) and am still unsuccessful so far.

I would love to be able to clean up the issues in my recordings and lossless mpeg2 transcode the files so I can watch via my PS3 without having to FF over commercials (which is flaky on a PS3 so far).  Additionally, if I could transcode the recordings (movies, mostly) to DivX, Xvid or H264 in order to copy them to my PS3 for later viewing, that would be great.  If I could automate that transcode to even transcode all recordings to save disk space, even better!

Is anyone else having similar issues?  I've searched everywhere and have yet to come upon anyone else mentioning the commercial transition issue in the beginning of a recording when trying to do the lossless transcode.  Are there other documents out there I can reference to help myself?  I'm not looking for a handout here and am perfectly willing to fix the issues myself, but I've been trying on these 3 problems for months without success and they are the only thing keeping my system from being perfect.  It is completely stable and never missed a recording.

Thank you in advance to anyone that can point me in the right direction.

---

### Post by kelliott on 2008-11-13
I guess that means no one has seen my issues before.  I really am trying to do everything possible to fix my own issues before reaching out for help.  I was just hoping someone has seen and dealt with similar problems before.

Thanks anyway.

---

### Post by anonymousdog on 2008-11-13
Are you looking to auto-remove commercials from your originals, or create a separate collection of commercial-removed recordings just for the PSP3, or something else?  I think we can manage the first two pretty easily ;-)

---

### Post by kelliott on 2008-11-13
Yes, I'm looking to do both of the first two in an automated fashion.  I've got the removecommercials.sh script which runs and flags commercials and is supposed to losslessly transcode mpeg to mpeg, but even when that completes I've still got commercials in the recording.

Additionally, and as for the PS3 file creation, I would like to auto-transcode to divx/xvid or some other PS3-capable format and leave the files in my Videos folder or later copy them to the PS3.  For movies, this would be a pretty good way to save space and still be able to watch them on the PS3, which is my only frontend device (using UPNP/DLNA) until MVix gets their act together and makes my 760HD DLNA-capable.  I don't run Mythfrontend on any machines, but do occasionally watch a recording from VLC on my Vista PC.
 
Every time I run ffmpeg or mencoder against a file to go from mpeg to xvid or divx it will only create a small file that is the beginning of the recording before the show actually begins.  I think if the remove commercials job worked and I could run ffmpeg against a commercial-stripped recording I'd be all set, but I haven't been able to get that to work on my own.

I recently upgraded from Mythbuntu 8.04 to 8.10 and since then ffmpeg and mythtranscode have been doing weird things, like complaining that the recordings are at 59.94 vs. 29.97 fps.  I have removed x264, ffmpeg, nuvexport and re-downloaded and recompiled them to try and get them working, but have not been successful.  I am willing to wipe and rebuild my machine from a clean 8.10 build if that will help, though I don't think it would.

Thanks for your reply, and hopefully I'm just missing something simple in my configuration.

---

### Post by anonymousdog on 2008-11-13
If this was a problem introduced by 8.10, I probably can't help you.

---

### Post by kelliott on 2008-11-14
Actually the problems existed in 8.04 as well.  I mentioned the upgrade only to stress that it didn't fix anything and to emphasize that I removed and recompiled ffmpeg, x264, etc. and still can't get it working.  

The best information I could find on each of my issues were in the links in the original post.  Maybe there is better information available or maybe I'm just doing something wrong with those documents, but I've followed them pretty closely without success.

I'm not looking to waste anyone's time with my issues, so if you can point me in the right direction I'm happy to research more and try to resolve things on my own.

---

### Post by kelliott on 2008-11-14
Ugh...double post.

---

### Post by anonymousdog on 2008-11-14
Ok, so, I'll back up and address your various problems.

What's in the /var/log/mythtv/mythbackend.log during a remove commercials job run?  Most or all of the script output is there.  I have some remove commercial scripts that work in 8.04 on mpeg2 recordings.  I haven't ever done the stuff on the PS3 page, but, I would think that a mythtranscode to mpeg2 would clean up the videos just fine.  You can set up (by default anyway IIRC) the backend to run a lossless transcode job on recordings before commercial flagging; so, if you're going to autoremove commercials, the videos will come out pretty clean anyway.

Overall, are you looking to maintain your original, pristine recordings and just create a separate store of commercial-removed videos (that won't be in the myth db unless you reimport them as videos)?  Or do you want to just replace your originals with commercial-removed versions?  The only issue with the latter is that auto-removing commercials isn't perfect; you are particularly likely to either not remove commercials in the last few minutes of a show or remove the last series of commercials as well as "closing credit" scenes typical of US sitcoms.  Works most awesome on sporting events.

If you are interested in getting perfect commercial removal, there is no substitute for watching a recording on a proper MythTV frontend and touching up the cut list.  With the built-in diskless client support (and usb flash drive config for netboot); you can use most any network connected PC to run the frontend.  If you just can't run a full frontend somehow, you're probably left with accepting the less-than-perfect results you get from auto-removal; it still better than watching the 80% of commercials it successfully removes.

What does 'ffmpeg -version' report?  Your xvid/divx problem might be a lack of compliled support for xvid.

---

### Post by kelliott on 2008-11-14
My /var/log/mythtv/mythbackend.log file is completely empty, oddly enough.

When you say I can run the lossless transcode before commercial flagging, do you mean using the integrated transcode job or the scripts that are all over the forums?

I agree with the assessment that commercial flagging isn't perfect.  I used to run a frontend on a Dell laptop and watch shows that way and I always missed the very beginning and very end of The Office (the American one).  

I would say that ideally I would like the TV shows I record to be cleaned up and the movies to be commercial removed and transcoded to Xvid/Divx in the Videos section to save space.  The TV shows get watched and deleted, but movies may stay on the system a bit longer.  Pretty much everything I record is in HD and I'd like to maintain as much quality as is feasible without wasting all the space on my drive by leaving them as Mpeg.  I've heard that WMV does a good job of making small and high-quality transcodes.

Lastly, my ffmpeg -version output is:FFmpeg version SVN-r15802, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 3. 0 / 52. 3. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov 11 2008 22:45:39, gcc: 4.3.2
FFmpeg SVN-r15802
libavutil     49.12. 0 / 49.12. 0
libavcodec    52. 3. 0 / 52. 3. 0
libavformat   52.23. 1 / 52.23. 1
libavdevice   52. 1. 0 / 52. 1. 0
libpostproc   51. 2. 0 / 51. 2. 0

I specifically left out the --enable-xvid option due to reading somewhere that xvid and divx were natively supported.  I am trying to find the post now and will update this thread when I find it.  I can try to recompile with --enable-xvid and see if that helps.

Thanks again.

---

### Post by anonymousdog on 2008-11-14
I thought there was no way to commflag a video, but I do see the database table there for it, filemarkup, and mythcommflag has an option "--video filename" that appears to be for creating a seeklist for non-recordings (i.e., videos).  It looks like mythtranscode would take an --infile and a cutlist (as a file) as an --honorcutlist argument.  The only missing piece is that mythcommflag currently won't run a flagging (and maybe getcutlist and getcutlist) job on file not in the recorded table (or, at least, files without start time and end time like a recording).  We would need at least those functions working to commflag videos without a proper frontend.

If you have a frontend, it appears you can generate a seek table (I just did that), create a cutlist in the frontend (I did that too), and you're stuck again.  If mythcommflag would getcutlist on a video file, we could use mythtranscode -infile <path>/<file> --honorcutlist <that cutlist>.  You could figure out the sql query to get the cutlist, something like 'SELECT `mark` FROM "filemarkup` WHERE `filename` = '<path>/<file>' AND type IN (0,1) ORDER BY `mark` ASC", and piece it together to make a cutlist string suitable to pass to mythtranscode --honorcutlist.

Either way, a bit of work to get it working for videos.

For the recordings, it's a matter of modifying my scripts to do what you want: auto-commercial removal and lossless transcode to a separate folder.  Fix xvid support in ffmpeg so transcoding to xvid would be possible.  Then you'll have a folder full of recordings with strange names.  That's still not ideal.

---

### Post by kelliott on 2008-11-14
BTW, post #176 at this link ([http://ubuntuforums.org/showthread.php?t=786095&page=18]("http://ubuntuforums.org/showthread.php?t=786095&page=18")) is where I found reference to the native xvid encoder.  Not sure if he's right or wrong.

As for your scripts, where do I find them to modify them?  I would think it should be possible to rename the xvids in the user job to the real show name.

Do you recommend I rebuild ffmpeg with --enable-xvid?

---

### Post by kelliott on 2008-11-17
I rebuilt using --enable-xvid and now my nuvexport works as expected.

Additionally, when I run mythtranscode --mpeg --honorcutlist on a recording from the command line (as opposed to a user job) that too seems to now work.  After I've removed the commercials via mythtranscode I have been able to successfully nuvexport-xvid to shrink the file size down a bit.  Then I manually move those files to /var/lib/mythtv/videos and delete my recordings via Mythweb.

So, the process seems to work now.  I'm assuming that recompiling ffmpeg from trunk helped a bit, though my remove commercials user job only flags commercials and generates a cutlist, even though it is then supposed to lossless transcode and honorcutlist.  I'll have to work that out separately.

As for my issues with nuvexport and only getting the beginning seconds of a recording, now that I can remove commercials that really isn't an issue anymore.  I did run into files that won't mythtranscode and complained about the bitrate being 59.94 instead of 29.97, but I've opted to re-record those shows to see if I was just dealing with bad recording files.  If it persists, I'll research that issue separately and start a new thread if necessary.

Now it seems I just need to play with the nuvexport settings.  I'm using mencoder as per GC's recommendation in the Auto Transcode HOWTO thread - I haven't tried ffmpeg yet.  I used quantization 1 and a vbr of 5000 and even HDTV recordings still look pretty good.

In all, I think I'm set for now and I appreciate your help.  Thanks again!

---

