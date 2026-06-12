---
title: "Some files won't transcode, others complete successfully but leave Job Queue errors"
date: 2010-03-30
forum: Mythbuntu
---

### Post by Lepy on 2010-03-30
I'm having trouble transcoding some particular files on my mythbox running 9.10 and .22. I have configured to my liking both nuvexport and mythnuv2mkv, and both run correctly on the master backend and a desktop acting as a slave backend when its running.

I was having some trouble with all jobs running on the slave backend erroring out, which I think I fixed by exporting the master backend nfs shares with write access. After this, commflagging is ok, but many of the slave "export to xvid" user jobs were giving a "ERROR: User job returned non-zero, check logs" in the Job Queue screen.

The affected files error out within about 30 seconds of the transcode starting. The files that output properly are complete, but still leave a "job returned non-zero" error in the queue. This seems to be related to mythtranscode dieing early, and while the job finishes, it is quite bothersome because the error stay in the queue.

Upon further inspection it seems the files may be culprit. The affected files play fine in mythtv and with vlc and are recorded using the analog side of an HVR-1600 in the exactly the same way other shows (on the same channel, even) that execute the user job correctly.

Running the same file through the cli of nuvexport and mythnuv2mkv.sh results in these errors:

```
xbmc@xbmc:~/scripts$ ./mythnuv2mkv.sh --quality=480 --chanid=1162 --starttime=20090929220000
29/03,22:54 [4130] INFO Changed to 480 quality.
29/03,22:54 [4130] INFO 1162 20090929220000 matches Good Eats   Peachy Keen (/video/media//1162_20090929220000.mpg)
29/03,22:54 [4130] INFO Unknown 480x480 NA 16:9 (Found in Channel) 29.970 FPS Audio Rate 0 Channels 0
29/03,22:54 [4130] ERROR Audio channels 0 invalid.
--------------------------------------------------------------------------------
29/03,22:54 [4130] INFO Exiting. Errored.

==========================


xbmc@xbmc:nuvexport-xvid
Now encoding:  Good Eats:  Peachy Keen
Encode started:  Mon Mar 29 22:58:59 2010
Use of uninitialized value in concatenation (.) or string at /usr/share/nuvexport/export/mencoder.pm line 104, <STDIN> line 14.
Use of uninitialized value in concatenation (.) or string at /usr/share/nuvexport/export/mencoder.pm line 104, <STDIN> line 14.
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Starting mencoder.
processed:  0 of 37547 frames (0.00%), 0 fps
mencoder finished.
processed:  0 of 37547 frames (0.00%), 0 fps

mencoder died early.Please use the --debug option to figure out what went wrong.
http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode


Cleaning up temp files.
Cleaning up child processes.

```

mythnuv2mkv.sh seems to give a better error: "ERROR Audio channels 0 invalid."

The user job is defined as: nuvexport-xvid --mencoder --nice 8 --input="%FILE%"

Any ideas? And while on the subject, a show should transcode to xvid quicker when the commercials are already losslessly transcoded out instead of transcoding with a cutlist, correct?

Relevant mythtvbackend.log:
```
2010-03-29 20:46:24.918 JobQueue Error: User Job 'nuvexport-xvid --mencoder --nice 8 --input="1162_20090929020000.mpg"' failed.
2010-03-29 21:47:38.944 JobQueue: Started Export to XVID for "Good Eats" recorded from channel 1162 at Tue Sep 29 02:30:00 2009
OSPEED was not set, defaulting to 9600 at /usr/share/nuvexport/nuv_export/shared_utils.pm line 61
^[[H^[[JLoading MythTV recording info.
^M0% ^M0% ^M1% ^M1% ^M2% ^M2% ^M3% ^M3% ^M4% ^M4% ^M5% ^M5% ^M5% ^M6% ^M6% ^M7% ^M7% ^M8% ^M8% ^M9% ^M9% ^M10% ^M10% ^M11% ^M11% ^M11% ^M12% ^M12% ^M13% ^M1$
^M23% ^M23% ^M24% ^M24% OSPEED was not set, defaulting to 9600 at /usr/share/nuvexport/nuv_export/shared_utils.pm line 61
^M25% ^M25% ^M26% ^M26% ^[[H^[[JLoading MythTV recording info.
^M26% ^M0% ^M27% ^M0% ^M27% ^M1% ^M28% ^M1% ^M28% ^M2% ^M29% ^M2% ^M29% ^M3% ^M30% ^M3% ^M30% ^M4% ^M31% ^M4% ^M31% ^M5% ^M32% ^M5% ^M32% ^M5% ^M32% ^M6% ^M$
^M82% ^M83% ^M83% ^M84% ^M84% ^M84% ^M85% ^M85% ^M86% ^M86% ^M87% ^M87% ^M88% ^M88% ^M89% . isn't writable.
^M89%
Cleaning up temp files.
^M89% 2010-03-29 21:47:57.028 JobQueue Error: User Job 'nuvexport-xvid --mencoder --nice 8 --input="1162_20090929023000.mpg"' failed.
^M90% ^M90% ^M91% ^M91% ^M92% ^M92% ^M93% ^M93% ^M94% ^M94% ^M95% ^M95% ^M95% ^M96% ^M96% ^M97% ^M97% ^M98% ^M98% ^M99% ^M99% ^M100%
. isn't writable.

Cleaning up temp files.
2010-03-29 21:47:58.072 JobQueue Error: User Job 'nuvexport-xvid --mencoder --nice 8 --input="1162_20090929020000.mpg"' failed.

```

---

### Post by Lepy on 2010-03-31
I updated to the .22-fixes to see if it would fix anything. The update deprecated nuvexport, so mythnuv2mkv is the only transcode script in use now...but it is still giving me a very odd problem.

On both master and slave, I have a script to take care of the analog-side recordings of the HVR-1600:

/home/mythtv/scripts/mythnuv2mkv43.sh

User job #2 is setup as follows:

/home/mythtv/scripts/mythnuv2mkv43.sh --jobid=%JOBID% --quality=480 --denoise=ON --deblock=ON --deinterlace=ON --copydir=/media/pool02/media/nuvexport --chanid=%CHANID% --starttime=%STARTTIME%

The slave handles commercial flaggings jobs with ease, but other jobs don't complete, with these same errors:

In the mythbackend.log

> 2010-03-31 01:49:15.073 JobQueue Error: User Job '/home/mythtv/scripts/mythnuv2mkv43.sh --jobid=1914 --quality=480 --denoise=ON --deblock=ON --deinterlace=ON --copydir=/media/pool02/media/nuvexport --chanid=1125 --starttime=20100329233000' failed.

Checking the /var/tmp/mythnuv2mkv####.log, 
```
31/03,01:48 [22289] INFO Changed to 480 quality.
31/03,01:48 [22289] INFO Denoise filter added.
31/03,01:48 [22289] INFO Deblock filter added.
31/03,01:48 [22289] INFO Deinterlace filter made available.
31/03,01:48 [22289] INFO Video will be located in /media/pool02/media/nuvexport.
31/03,01:48 [22289] INFO 1125 20100329233000 matches Good Eats	Tortilla Reform (/var/lib/mythtv/recordings//1125_20100329233000.mpg)
31/03,01:48 [22289] INFO Unknown 480x480 NA 4:3 (Found in Channel) 29.970 FPS Audio Rate 48000 Channels 2
31/03,01:48 [22289] INFO Output is a greater scale than input. This is not sensible.
31/03,01:48 [22289] INFO Crop to 480:480:0:0. Scale to 640x480.
31/03,01:48 [22289] INFO Deinterlace filter added.
31/03,01:48 [22289] INFO If progressive this is wrong use --deinterlace=NO.
31/03,01:48 [22289] INFO You may need Invtelecine rather than Deinterlace. (--deinterlace=NO --invtelecine=YES).
31/03,01:48 [22289] INFO Audio Encoder: oggenc --raw-chan=2 --raw-rate=48000 --quality=6 -o /var/lib/mythtv/recordings//1125_20100329233000_audio.ogg /var/tmp/mythnuv2mkv22289/audout.
31/03,01:48 [22289] START Starting ogg audio trans of /var/lib/mythtv/recordings//1125_20100329233000.mpg. quality 6.
31/03,01:48 [22859] INFO Starting monitoring process.
31/03,01:49 [22289] ERROR Skipping /var/lib/mythtv/recordings//1125_20100329233000.mpg. Problem with audio pass.
--------------------------------------------------------------------------------
31/03,01:49 [22289] INFO Exiting. Errored.
```

The job shows up in red on mythweb with the result: "job returned non-zero"

However, if the same command that was failed in the mythbackend.log is run from a terminal on the slave machine, the result is a successfully exported and transcoded files:

E.g. /home/mythtv/scripts/mythnuv2mkv43.sh --jobid=1914 --quality=480 --denoise=ON --deblock=ON --deinterlace=ON --copydir=/media/pool02/media/nuvexport --chanid=1125 --starttime=20100329233000

```
31/03,01:51 [31323] INFO Changed to 480 quality.
31/03,01:51 [31323] INFO Denoise filter added.
31/03,01:51 [31323] INFO Deblock filter added.
31/03,01:51 [31323] INFO Deinterlace filter made available.
31/03,01:51 [31323] INFO Video will be located in /media/pool02/media/nuvexport.
31/03,01:51 [31323] INFO 1125 20100329233000 matches Good Eats   Tort(illa) Reform (/var/lib/mythtv/recordings//1125_20100329233000.mpg)
31/03,01:51 [31323] INFO Unknown 480x480 NA 4:3 (Found in Channel) 29.970 FPS Audio Rate 48000 Channels 2
31/03,01:51 [31323] INFO Output is a greater scale than input. This is not sensible.
31/03,01:51 [31323] INFO Crop to 480:480:0:0. Scale to 640x480.
31/03,01:51 [31323] INFO Deinterlace filter added.
31/03,01:51 [31323] INFO If progressive this is wrong use --deinterlace=NO.
31/03,01:51 [31323] INFO You may need Invtelecine rather than Deinterlace. (--deinterlace=NO --invtelecine=YES).
31/03,01:51 [31323] INFO Audio Encoder: oggenc --raw-chan=2 --raw-rate=48000 --quality=6 -o /var/lib/mythtv/recordings//1125_20100329233000_audio.ogg /var/tmp/mythnuv2mkv31323/audout.
[1m31/03,01:51 [31323] START Starting ogg audio trans of /var/lib/mythtv/recordings//1125_20100329233000.mpg. quality 6.[m(B
31/03,01:51 [31923] INFO Starting monitoring process.
31/03,01:52 [31323] INFO Video Encoder: mencoder -idx -noskip 		/var/tmp/mythnuv2mkv31323/vidout -demuxer rawvideo -rawvideo w=480:h=480:fps=29.970 		-audiofile /var/tmp/mythnuv2mkv31323/audout -audio-demuxer rawaudio -rawaudio rate=48000:channels=2 		-ovc x264 -x264encopts level_idc=31:bframes=3:b_pyramid:weight_b:threads=auto:direct_pred=auto:subq=6:frameref=5:partitions=all:8x8dct:mixed_refs:me=umh:trellis=1:bitrate=1151 		-oac copy 		-vf hqdn3d,pp7,pp=fd,softskip,crop=480:480:0:0,scale=640:480,harddup -sws 7  		-of rawvideo -o /var/lib/mythtv/recordings//1125_20100329233000_video.h264.
[1m31/03,01:52 [31323] START Starting h264 Single video pass trans of /var/lib/mythtv/recordings//1125_20100329233000.mpg. vbr 1151 abr .[m(B
[1m31/03,02:06 [31323] START Joining /var/lib/mythtv/recordings//1125_20100329233000_video.h264 /var/lib/mythtv/recordings//1125_20100329233000_audio.ogg in mkv container.[m(B
[1m31/03,02:06 [31323] START Checking /var/lib/mythtv/recordings//1125_20100329233000.mkv.[m(B
[32m31/03,02:06 [31323] SUCCESS Successful trans. /var/lib/mythtv/recordings//1125_20100329233000.mpg trans to /media/pool02/media/nuvexport/Good_Eats.Tortilla_Reform. /var/lib/mythtv/recordings//1125_20100329233000.mpg kept[39;49m
31/03,02:06 [31323] INFO MythTV V0.22 or greater. Not creating MythVideo entry. Use MythVideo menu
31/03,02:06 [31323] INFO RUNTIME: 0 days 0 hours 15 minutes and 19 seconds. Original filesize: 557M New filesize: 512
--------------------------------------------------------------------------------
31/03,02:06 [31323] INFO Exiting. Successful.
```

On mythweb, I can refresh the page and watch the job queue entry (which is still red) progress through the stages until it turns white and says "Successfully Completed"

So, what exactly might be happening, if on the slave, the same command that fails with an audio error as a user job completes successfully from the command line?

This slave backend error is in addition to the "ERROR Audio channels 0 invalid." which appears on both the master and slave.

Can anyone shed some light on either error?

---

### Post by Lepy on 2010-03-31
I'll mark this thread as solved.

By installing mediainfo from the ppa and passing the USEMEDIAINFO="TRUE" option in the mythnuv2mkv.sh script, I overcame the "ERROR Audio channels 0 invalid." on those pesky recording, only to run into another error.

This error complained about dos2unix command not found. To fix this error, tofrodos needed to be installed, which was referenced nowhere in the mythnuv2mkv help or requirements.

After this, I chmod 777'd all my recording directories to be on the safe side, and so far the master and slave have been happily encoding all day long.

---

