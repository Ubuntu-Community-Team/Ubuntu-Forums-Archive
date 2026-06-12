---
title: "Import dvd to iso works, but no other way"
date: 2010-01-31
forum: Mythbuntu
---

### Post by Lido on 2010-01-31
I'm trying to import a dvd to a small avi file. When I run "import dvd" and select ISO as the quality, it works fine. If I select "excellent" quality instead, it seems to import the raw DVD ok, but then hang up at transcode and ultimately give up. The screen says "transcode is thinking..." for a minute or three and then finally, with the progress bar only about 1/3 of the way across the screen it gives the "1 of 0 jobs" and "You could import a dvd" messages. When I look in the videos directory there's a 2k file there that doesn't seem to contain anything useful, but at least it can write something so it doesn't appear to be a permissions problem. Here's what comes up in the mtd.log:
```
12:33:56: launching job: job dvd 1 2 6 1 -1 /MythTV/videos/RalphS
12:33:56: transcode command will be: 'transcode -i "/var/lib/mythdvd/temp/RalphS/vob/" -g 720x480 -M 2 -X 2,0 -y xvid,null -A -N 0x2000 -a 1 -o /dev/null --l
og_no_color -R 1,twopass.log'
12:33:56: job thread beginning to rip dvd title
12:37:18: job thread finished ripping dvd title
12:38:09: Error: 
12:38:09: transcode command will be: 'transcode -i "/var/lib/mythdvd/temp/RalphS/vob/" -g 720x480 -M 2 -X 2,0 -y xvid -A -N 0x2000 -a 1 -o "/MythTV/videos/RalphS.avi" --log_no_color -R 2,twopass.log'
12:38:53: Error: 
12:38:55: job finished successfully: job dvd 1 2 6 1 -1 /MythTV/videos/RalphS
12:39:51: a client socket has been closed

```

---

### Post by nickrout on 2010-01-31
try running the transcode command manually and see whether you get any useful error messages.

---

### Post by johnvan on 2010-02-01
I use acidrip if that helps. Works great for me.

---

### Post by Lido on 2010-02-02
Another weird thing is that MythVideo will play the .iso of the dvd, but only if the actual disc is mounted. Mounting the iso won't do it either, it has to be a disc or the player just exits after a few seconds of blank screen.

When I run transcode manually, I got thousands of lines of this:
```
[audio_trans.c] Sorry, only PCM audio is supported for processing

```
and then it ended with this:
```
[decoder.c] cancelling the import threads: 0:02:53,  (16| 0| 4) 

[transcode] encoded 4163 frames (1037 dropped, 0 cloned), clip length 173.63 s

```

---

### Post by nickfoti on 2010-07-29
I'm having the same issue, fresh install of mythbuntu 10.04 - I get this message (seems like every frame):

```
[audio_trans.c] Sorry, only PCM audio is supported for processing
```Transcode completes with this message:

```
[avilib.c] VID NrEntries 0/2 (ix00) |0x768D6A78|1100496|137558|7) 
[avilib.c] VID NrEntries 1/2 (ix00) |0xD5EFA3FC|802640|100326|
[decoder.c] cancelling the import threads

[transcode] encoded 237886 frames (-47545 dropped, 0 cloned), clip length 7937.46 s
```

The resulting file has no audio. This is the transcode command I used (identical to what the MTD log suggested, but I added an output filename):

```
transcode -i /var/lib/mythdvd/temp/DIEANOTHERDAY_D1_PS/vob/ -g 720x480 -M 2 -X 2,0 -y xvid,null -A -N 0x2000 -o die_another_day --progress_rate 20 --log_no_color -R 1,twopass.log
```How do I fix this? Thanks!

---

### Post by klc5555 on 2010-07-30
The mythtv importdvd is OK, but not perfect by a long shot. It is nearly as likely not to work on any particular DVD as work, depending on DRM considerations, and other issues.

For this reason, one needs to have a full array of backup tools ready to go in one's repertoire. One or another (and not always the same one) will get the job done when the myth importdvd fails. One poster already mentioned acidrip. Also very useful is Handbrake (though I prefer 0.9.3, which still has high-quality *.avi support, to 0.9.4, which has eliminated it). Handbrake handles just about everything. VLC is also useful for handling those obnoxious Sony/Disney disks with the 99 random tracks. (Though I find the Windows version of VLC next to useless). Thoggen has its moments as well, though I wish it could handle slightly higher quality limits. 

And I haven't come close to exhausting the list. Do a bit of research, and you'll find the tools that fit your needs.

---

