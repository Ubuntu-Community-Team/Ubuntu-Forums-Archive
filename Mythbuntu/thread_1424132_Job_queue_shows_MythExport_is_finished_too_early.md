---
title: "Job queue shows MythExport is finished too early"
date: 2010-03-07
forum: Mythbuntu
---

### Post by bcgrown on 2010-03-07
I'm using Mythbuntu 9.10.

When I start a MythExport job, it mostly works fine.

The problem is that MythTV thinks the job has finished as soon as the MythExport script exits, even though ffmpeg is still busy transcoding.

This wouldn't be a big deal except I use mythwelcome for auto-shutdown and since the ffmpeg job isn't recognized,  the system will interrupt the job and shut down.

I could write a script that runs in a cron job to check for ffmpeg processes and does "mythshutdown --lock" and "--unlock" as required, but that seems really messy.

It would also be nice if there were some way to run a script when MythExport is finished a job.

Anyone know a better way?

---

### Post by SiHa on 2010-03-07
Well, a slightly less dirty way than the cron job (but only painting over the cracks, really), would be to run a script that checks for an instance of ffmpeg as the 'Pre-Shutdown Check':```
#!/bin/bash
if (ps -A|grep $1 > /dev/null);
then
echo $1' is running, not safe to shutdown' 
exit 1
else
echo $1' is not running, it is safe to shutdown' 
exit 0
fi

```

You can copy the above script to something like 'shutdowncheck', put it in /usr/local/bin, or somewhere else in the command path, make it executable and enter ```
shutdowncheck ffmpeg
``` as the pre-shutdown-check in the backend setup.

If ffmpeg is running, it will return an exit status of '1' which will block the shutdown, else it will return a '0' and shutdown should continue.

---

### Post by bcgrown on 2010-03-07
That would work, but I've decided instead to ditch MythExport entirely.

I added the script [here]("http://www.mythtv.org/wiki/Transcoding_into_a_3gp_Video") as a user job after modifying the ffmpeg options to suit my device.

If you do it this way, MythTV recognizes that the transcoding is happening because that script doesn't exit until ffmpeg is finished.

Unfortunately the commercial-free option didn't work for me on the first go,  but the simple script works fine.

I'm not sure what advantage there is to using MythExport beyond the nice web interface and the RSS feed.

Edit: Here is the complete text of my script, in case the linked page changes in the future:

```
#!/bin/sh
# MythTV user job to transcode a video for a phone
FILE=$1
TITLE=$2
OUTDIR="/media/transcoded/"

# Settings for iPhone
/usr/bin/ffmpeg -i $FILE -y -acodec libfaac -ab 128kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 480x320 -aspect 16:9 -ac 2 -ar 48000 "$OUTDIR$TITLE".m4v

```

---

