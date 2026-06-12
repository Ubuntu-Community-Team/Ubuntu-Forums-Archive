---
title: "Can't watch recordings from 5* channel on front end: deinterlacing problem???"
date: 2013-04-01
forum: Mythbuntu
---

### Post by NautiusMaximus on 2013-04-01
This is a continuation of a [previous thread]("http://ubuntuforums.org/showthread.php?t=2128218") after I've done a bit more playing around with things.

The problem is that I am consistently unable to watch programmes recorded from one specific channel (5* via Freeview in the UK) on the MythTV frontend. The recordings have certainly not failed completely. I can watch them via VLC media player, and can also watch them via a media streamer.

I can also watch 5* as live TV without problems. I can watch recordings from any other channel without problems.

The only thing I can't do is watch recordings from 5* via the MythTV frontend.

If I look at the Mythfrontend log at the time I'm trying to watch the recording, I see the message "Failed to enable deinterlacing". So I had a play with the playback profiles to see if it would make any difference. My default playback profile was "CPU+". I changed it to "Slim" (which I gather is one of the least likely to fail), and that didn't help. I also, within the "Slim" profile, changed the deinterlacing method to "None". None of those things made any difference.

Any ideas what's gone wrong here and what I could try next?

Many thanks
NM

---

### Post by NautiusMaximus on 2013-04-03
Oh, sorry, should have mentioned that I'm using Mythbuntu 10.04.

---

### Post by klc5555 on 2013-04-03
10.04 is almost at EOL. Not sure which version of mythtv is being used at this point: 023.x, 0.24.x, or 0.25x 

But at any rate, as I wrote in the earlier thread, I still think the issue is related to the playback profile being used --more likely to the video decoder than to the deinterlacer. Three or four years ago I had a similar black-screen playback problem on one channel only, it turned out that the issue was this one channel's mpeg stream was the only one at the correct resolution to have the playback profile attempt to use hardware-assisted decoding (at the time still XvMC) rather than software decoding (libmpeg2 or ffmpeg). XvMC didn't work on my hardware; the result was playback black-screen on the main front end, but only for recordings from this one channel on this one frontend. A remote frontend elsewhere in the house could play the recordings without issue. 

But before I got the profile issue figured out and fixed, I had noticed that doing a lossless transcode of the recordings from that channel rendered them viewable (with no degradation of quality) from the main frontend. I even set up a user job to automatically transcode all recordings from this one channel, which script I continued to use until I figured out the profile issue.

You might want to test a recording file from your fatal freeview channel:```
mythtranscode --mpeg2 -c[myth 4-digit channel designation] -s[starttime]
``` Or you can use -i [filename] instead of -c -s

This produces a transcoded .mpg.tmp file with the same filename as your recording, and about the same size. Move (rename) the original recording from .mpg to .mpg.bak , then move (rename) the .mpg.tmp file you made earlier to .mpg

Then see if this newly made version of your original recording plays in the frontend.  If it does, then it's likely that the issue does pertain to some element of the playback profile.

---

### Post by NautiusMaximus on 2013-04-06
Many thanks for those suggestions. I think we're making progress.

I tried using mythtranscode as you suggested, but it didn't work. It created a .mpg.tmp file of size zero bytes. Here was the output from the terminal:

```
2013-04-06 10:06:28.270 New DB connection, total: 2
2013-04-06 10:06:28.272 ProgramInfo(): Updated pathname '':'' -> '1030_20130331230000.mpg'
2013-04-06 10:06:28.341 max_analyze_duration reached
2013-04-06 10:06:28.341 start time is not set in av_estimate_timings_from_pts
2013-04-06 10:06:38.978 Found end of file without finding  any frames
```

So then I tried using the transcode option from the MythTV front end. That also failed. Here is what the backend log looked like after I tried:

```
2013-04-06 10:18:01.993 JobQueue: Transcode Starting for Dallas "Ewings Unite!": High Quality (818.8 MB)
2013-04-06 10:18:02.041 ProgramInfo(): Updated pathname '':'' -> '1030_20130331230000.mpg'
2013-04-06 10:18:02.106 Using runtime prefix = /usr
2013-04-06 10:18:02.117 Using configuration directory = /home/mythtv/.mythtv
2013-04-06 10:18:02.129 Empty LocalHostName.
2013-04-06 10:18:02.140 Using localhost value of htpc
2013-04-06 10:18:02.163 New DB connection, total: 1
2013-04-06 10:18:02.178 Connected to database 'mythconverg' at host: localhost
2013-04-06 10:18:02.184 Closing DB connection named 'DBManager0'
2013-04-06 10:18:02.196 Connected to database 'mythconverg' at host: localhost
2013-04-06 10:18:02.208 Enabled verbose msgs: important
2013-04-06 10:18:02.219 ProgramInfo(): Updated pathname '':'' -> '1030_20130331230000.mpg'
2013-04-06 10:18:02.233 Transcoding from /var/lib/mythtv/recordings/1030_20130331230000.mpg to /var/lib/mythtv/recordings/1030_20130331230000.mpg.tmp
2013-04-06 10:18:02.370 NVP(0): Disabling Audio, params(-1,-1,-1)
2013-04-06 10:18:02.372 MythContext: Connecting to backend server: 172.16.100.20:6543 (try 1 of 1)
2013-04-06 10:18:02.441 Using protocol version 23056
2013-04-06 10:18:02.507 MainServer::ANN Monitor
2013-04-06 10:18:02.508 NVP(0): Disabling Audio, params(-1,-1,-1)
2013-04-06 10:18:02.518 adding: htpc as a client (events: 0)
2013-04-06 10:18:02.531 New DB connection, total: 2
2013-04-06 10:18:02.541 MainServer::ANN Monitor
2013-04-06 10:18:02.551 Connected to database 'mythconverg' at host: localhost
2013-04-06 10:18:02.562 adding: htpc as a client (events: 1)
2013-04-06 10:18:02.587 ProgramInfo(): Updated pathname '':'' -> '1030_20130331230000.mpg'
2013-04-06 10:18:02.597 No video information found!
2013-04-06 10:18:02.606 Please ensure that recording profiles for the transcoder are set
2013-04-06 10:18:02.620 Transcoding /var/lib/mythtv/recordings/1030_20130331230000.mpg failed
2013-04-06 10:18:02.630 Deleting /var/lib/mythtv/recordings/1030_20130331230000.mpg.tmp
2013-04-06 10:18:02.641 Requesting delete for file 'myth://Default@172.16.100.20:6543/1030_20130331230000.mpg.tmp'.
2013-04-06 10:18:02.652 MainServer::ANN Playback
2013-04-06 10:18:02.662 adding: htpc as a client (events: 0)
2013-04-06 10:18:02.672 ProgramInfo(): Updated pathname '':'' -> '1030_20130331230000.mpg'
2013-04-06 10:18:02.674 Unable to find 1030_20130331230000.mpg.tmp in HandleDeleteFile()
2013-04-06 10:18:02.696 Deleting file '/var/lib/mythtv/recordings/1030_20130331230000.mpg.tmp'.
2013-04-06 10:18:02.719 JobQueue: Transcode Errored: Dallas "Ewings Unite!": High Quality (exit status 255, job status was "Errored")
2013-04-06 10:18:02.770 ProgramInfo(): Updated pathname '':'' -> '1030_20130331230000.mpg'
```

OK, so if that isn't going to work, then I thought maybe I could transcode using ffmpeg instead. If anyone can see any obvious reasons why mythtranscode might have failed, then all suggestions are gratefully appreciated, but I don't think I want to spend too much time troubleshooting that one when I can just use ffmpeg instead. So here is the ffmpeg command I used:

```
ffmpeg -i oldfile.mpg newfile.mpg
```

Success! (Well, sort of). The resulting file could be played in the front end. 

The only problem was that the file size had shrunk to about a quarter of what it was, and the image quality was lousy. However, I expect that this is just a matter of using the right ffmpeg options, yes? Presumably the default shrinks the file considerably, and I need to figure out what the options are to make sure it doesn't do that. I expect I'll probably figure that out eventually, but if anyone happens to know the correct ffmpeg syntax, that would be appreciated.

So, I don't think this is really a solution to the problem, but it's approaching a pretty usable workaround. Once I've figured out the appropriate ffmpeg syntax, I can simply set that up as a user job and get it to run on any programs I record from that channel.

BTW, I know how to get specific recordings to automatically run a user job, but does anyone know if it's possible to automatically run a job on anything that's ever recorded on a particular channel?

So, what do we reckon? Should I just settle for the workaround, or is it going to be worth continuing to search for a proper solution to the problem?

Thanks again for your help
NM

---

### Post by klc5555 on 2013-04-06
I'm mildly surprised that mythtranscode bombed the way it did, unless your mythtv version on your 10.04 installation is 0.25-plus, where mythtranscode has begun increasingly to experience a variety of odd problems, particularly in the realm of lossless transcoding.

By all means continue to search for a proper solution to this issue. But if it's not your video decoder (depending on mythtv version) as applied to your channel 5, then I admit I don't know what it is.

But until the full solution turns up, you may wish to try to try workarounds if they allow the channel to be watched.

ffmpeg directly from the command line is nothing if not arcane. But the official ffmpeg faq does have recommendations for high-quality mpeg: [http://ffmpeg.org/faq.html#Which-are-good-parameters-for-encoding-high-quality-MPEG_002d1_002fMPEG_002d2_003f](http://ffmpeg.org/faq.html#Which-are-good-parameters-for-encoding-high-quality-MPEG_002d1_002fMPEG_002d2_003f)

Based on this you might wish to try something along the lines of```
ffmpeg -i oldfile.mpg -mbd rd -trellis 2 -cmp 2 -subcmp 2 -g 100 -pass 1/2  newfile.mpg
``` If this fails, the faq entry has additional recommendations. If this produces a satisfactory output, and viewable from the frontend, then I suppose it should be automated for recordings from this channel.

---

### Post by PhilWig on 2013-04-06
This is odd.  5* is not a channel I watch much but my stats suggest I made 26 recordings under 9.04 and it works now with 12.04.
Are ALL your 5* recordings faulty or are there some particular recordings which fail?
Can we pin it down by comparison of settings?    I'm using a mobo with on-board Nvidia 8300 graphics.  If you have similar and want to try comparisons then please suggest a recording to try.

Phil

---

### Post by PhilWig on 2013-04-06
A PS.  You do have good recordings from other channels on that multiplex eg ITV3 or E4 ?
Phil

---

### Post by NautiusMaximus on 2013-04-07
Good question, PhilWig. Yes, other channels on the same multiplex are fine. The problems only occur on 5*. They occur repeatedly, but not 100% consistently. Most recordings from that channel have the same problem, but I do have one recent good recording.

Anyway, back to my workaround. This is all getting rather frustrating. I'm afraid your suggested ffmpeg syntax didn't really help, klc5555, and gave rather poor quality. But I did figure it out in the end: the syntax that worked was as follows:

```
ffmpeg -i oldfile.mpg -sameq -ar 48000 -ac 2 newfile.mpg
```

That results in a modest increase in file size, which isn't ideal, but given that I don't have to do this to very many recordings isn't really a big problem. The main thing is there is no noticeable degradation in quality, and the recording is now viewable from the frontend.

So you might think it would be easy enough to set this up as a user job, right? Wrong. I tried that, and although I can run the script file manually, it doesn't want to run from the mythtv frontend. It says that it's queued, but it just stays in the queue without ever running. I don't think it's a permissions thing, as the script has 755 permissions. I shall do a little bit of playing around with that, but that's probably best introduced as a new thread if I can't figure it out.

---

### Post by klc5555 on 2013-04-07
> **NautiusMaximus said:**
> Good question, PhilWig. Yes, other channels on the same multiplex are fine. The problems only occur on 5*. They occur repeatedly, but not 100% consistently. Most recordings from that channel have the same problem, but I do have one recent good recording.

Anyway, back to my workaround. This is all getting rather frustrating. I'm afraid your suggested ffmpeg syntax didn't really help, klc5555, and gave rather poor quality. But I did figure it out in the end: the syntax that worked was as follows:

```
ffmpeg -i oldfile.mpg -sameq -ar 48000 -ac 2 newfile.mpg
```

That results in a modest increase in file size, which isn't ideal, but given that I don't have to do this to very many recordings isn't really a big problem. The main thing is there is no noticeable degradation in quality, and the recording is now viewable from the frontend.

So you might think it would be easy enough to set this up as a user job, right? Wrong. I tried that, and although I can run the script file manually, it doesn't want to run from the mythtv frontend. It says that it's queued, but it just stays in the queue without ever running. I don't think it's a permissions thing, as the script has 755 permissions. I shall do a little bit of playing around with that, but that's probably best introduced as a new thread if I can't figure it out.

Ah. I should have realized that you were still running an older version of ffmpeg --in versions from the last couple of years the -sameq option has been removed.

A script run as a user job needs to be in a directory where the mythtv account has execute access. Therefore /usr/bin or similar, but not in the main user's home directory.

Are you still running a version of mythtv less than 0.25? There's a script on the mythtv wiki intended to trim commercials while lossless transcoding with mythtranscode as a user job. [http://www.mythtv.org/wiki/Script_-_RemoveCommercials](http://www.mythtv.org/wiki/Script_-_RemoveCommercials)

With just a bit of hacking off of what is unnecessary for this task, and replacing the lossless mythtranscode with your ffmpeg command a version of this script may provide what you need:

```
#!/bin/sh

##### Originally Commercial Remover Script for MythTV, updated 5/14/12, edited to be
###   a transcoding script to solve a particular ffmpeg task, edited 4/7/13.
###
##       Version Changes to mythutil and mythcommflag tools under MythTV 0.25  
##        necessitate different commands within the script. (Under MythTV < 0.25 you could 
##        just point mythcommflag at the recordings in the file system and get the job done, now
##        under MythTV 0.25 you have to use mythutil to generate the cutlist and mythcommflag to
##        flag commercials, AND point both at recordings based on %CHANID% and %STARTTIME%.  Under 
##        MythTV 0.25 mythtranscode can also be pointed at %CHANID% and %STARTTIME% but since it
##        currently supports the older infile /outfile method as well (and I prefer how this
##        script creates old/new files, it is the method used.
##
##      Since this script requires the User Job to pass additional arguments under MythTV 0.25,
##       use following User Job syntax for userjobs under all versions:
##
##        'commercialremover.sh %DIR% %FILE% %CHANID% %STARTTIME%'
##
##      Credits: Zwhite, Ricks03, Waxrat @ www.mythtv.org/wiki

##  This quick hack based on the script by Zwhite, Ricks03, and Waxrat eliminates the automatic commercial 
##  detection and cutlist generation. It is intended to do a simple transcode with ffmpeg, back up the original
##  recording, replace it with the transcoded version and generate a frame index for it.

###
#####
VIDEODIR=$1 #MythTV-024 %DIR%
FILENAME=$2 #MythTV-024 %FILE%
CHAN=$3 #REQUIRED FOR MythTV-025 %CHANID%
START=$4 #REQUIRED FOR MythTV-025 %STARTTIME%

# Sanity checking, to make sure everything is in order. Modified to check $CHAN and $START for MythTV 0.25 Support
if [ -z "$VIDEODIR" -o -z "$FILENAME" -o -z "$CHAN" -o -z "$START"]; then
        echo "Usage: $0 <VideoDirectory> <FileName>"
        exit 5
fi
if [ ! -f "$VIDEODIR/$FILENAME" ]; then
        echo "File does not exist: $VIDEODIR/$FILENAME"
        exit 6
fi

# The part generating a cutlist has been removed.

echo "Transcoding..."
# mythtranscode --honorcutlist --showprogress -i $VIDEODIR/$FILENAME -o $VIDEODIR/$FILENAME.tmp

ffmpeg -i $VIDEODIR/$FILENAME  -sameq -ar 48000 -ac 2 $VIDEODIR/$FILENAME.tmp

ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Transcoding failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi
mv $VIDEODIR/$FILENAME $VIDEODIR/$FILENAME.old
mv $VIDEODIR/$FILENAME.tmp $VIDEODIR/$FILENAME


echo "Rebuilding..."
##### - UNCOMMENT FOLLOWING LINE IF RUNNING MythTV Version <= 0.24
#mythcommflag -f $VIDEODIR/${FILENAME} --rebuild

##### - UNCOMMENT FOLLOWING LINE IF RUNNING MythTV Version >= 0.25
mythcommflag --chanid $CHAN --starttime $START --rebuild
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Rebuilding seek list failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi


echo "Clearing cutlist..."
##### - UNCOMMENT FOLLOWING LINE IF RUNNING MythTV Version <= 0.24
#mythcommflag --clearcutlist -f $VIDEODIR/$FILENAME

##### - UNCOMMENT FOLLOWING LINE IF RUNNING MythTV Version >= 0.25
mythutil --clearcutlist --chanid $CHAN --starttime $START
ERROR=$?
if [ $ERROR -eq 0 ]; then
        # Fix the database entry for the file 
##### - Note: MAY need to add mysql mythconverg DB credentials '--user=<blah> --password=<blah>' 
##       to the 'mysql mythconverg' command below.)
        # Fix the database entry for the file 
        cat << EOF | mysql mythconverg
UPDATE 
        recorded
SET
        cutlist = 0,
        filesize = $(ls -l $VIDEODIR/$FILENAME | awk '{print $5}') 
WHERE
        basename = '$FILENAME';
EOF
        exit 0
else
        echo "Clearing cutlist failed for ${FILENAME} with error $ERROR"
        rm -f $VIDEODIR/$FILENAME.tmp
        exit $ERROR
fi

```


Depending on whether you are running 0.24 or 0.25, the mythcommflag sequence near the end of the script intended to build a new frame index may have to have an edit. 

If the script were called, say, channel-5, and placed in /usr/bin, the user-job command to invoke it would run something like:

```
/usr/bin/channel-5 %DIR% %FILE% %CHANID% %STARTTIME%
```

Anyway, this is just an initial idea of how to automate such an ffmpeg script. If it works at all.

---

### Post by NautiusMaximus on 2013-04-13
OK, I have finally succeeded.

The problem with getting the user job to run, as I eventually discovered, was that user jobs appear to be disabled by default. There is a setting in the backend setup that allows you to enable them. Once I'd figured that out, it was easy.

I would love to know who thought that disabling user jobs by default was a good idea, and why. I can't even imagine why you'd even want the option to disable a user job: if you don't want one, don't set one up in the first place. Having them disabled as an obscure option by default is just mind-blowingly baffling.

Anyway, thanks to all who contributed for your help. I knew we'd get there in the end!

---

