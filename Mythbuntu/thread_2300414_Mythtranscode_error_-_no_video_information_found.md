---
title: "Mythtranscode error - no video information found"
date: 2015-10-25
forum: Mythbuntu
---

### Post by tristan-dawson on 2015-10-25
Hi, I've just reinstalled Mythbuntu 14.04 and I'm getting an error with Mythtranscode:

```
user@pc:/var/lib/mythtv/recordings$ sudo mythtranscode --honorcutlist --showprogress -i 1002_20151023080000.mpg -o test.mpg
2015-10-26 09:10:54.088054 C  mythtranscode version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2015-10-26 09:10:54.088069 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2015-10-26 09:10:54.243585 E  No video information found!
2015-10-26 09:10:54.243589 E  Please ensure that recording profiles for the transcoder are set
2015-10-26 09:10:54.246334 E  Transcoding 1002_20151023080000.mpg failed

```

Can someone help me out with this? I can't work out why mythtranscode is throwing this error..

I've looked in MythBackend Setup --> Recording Profiles and it all looks normal, with High, Medium and Low Profiles setup..

I'm not sure what to do.. Is there somewhere else I should be setting these recording profiles??

Help??

Thanks in advance.
-Tristan

---

### Post by blm-ubunet on 2015-10-25
Don't run this as sudo.
The (myth)program will try to find a config.xml in /root's home folder & likely fail.
Would be best to run as user "mythtv".
Could be the --infile option needs full path.

If you're using sudo to be able to write in the recording folder then find another way.
- permissions
- groups
- /home/Videos etc

Note: mythtranscode doesn't support mpeg4-layer10 AVC H264 except via fifo mode (frame server) using external x264 or ffmpeg encoder.

---

