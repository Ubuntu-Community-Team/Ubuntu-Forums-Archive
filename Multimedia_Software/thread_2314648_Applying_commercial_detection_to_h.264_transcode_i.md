---
title: "Applying commercial detection to h.264 transcode in MythTV?"
date: 2016-02-22
forum: Multimedia Software
---

### Post by SagaciousKJB on 2016-02-22
Okay so I have mythtv 0.27.4-fixes self compiled, on Ubuntu 14.04 LTS. Not sure if any other information is relevant or needed...

I have a post-processing user script that transcodes using ffmpeg and x264.  I grabbed it off of the MythTV Wiki user scripts section and all credits are in the script but I modified it a little bit, to suit my own encoding desires. I don't really know Python well enough to make major modifications.

The reason I like this script is because it updates the database ( I think, from what I can tell ) and updates the filename of the recording entry with the .mp4 file, so everything is in place. Well, I don't want to apply commercial detection as a cutlist and use mythtranscode to cut them out permanently, because it really only works okay-ish at best for me.  I want to be able to use commercial detection on the H.264 file that the script produces to be able to skip commercials with the auto-skip feature, but be able to rewind and disable it if the commercial detection cuts part of the actual show. When I do apply commercial detection to the h.264 transcode it doesn't seem to actually line up to the detected commercials at all.

So, I think this is because there's no seek table? I tried using mythtranscode to rebuild the seektable instead of mythcommflag. I was able to enter the "edit" mode for the video and load the detected commercials as a cutlist ( and the times seemed to match up right), but then the cutlist didn't actually skip anything and seeking in the file wouldn't work at all.  With mythcommflag, I can seek with the cursors and rewind and everything just fine, but when trying to enter "edit" mode it says "No seektable", and any commercial list that's generated finds commercials but the times don't match up, so if I leave it on "notify" it will tell me it's a commercial in the middle of a program. Curiously it doesn't seem to skip at all even with the list if I enable auto-skip.

Is there actually a way to get the commercial list to work on a h.264 transcode like this?

```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-

# 2015 Michael Stucky
# This script is based on Raymond Wagner's transcode wrapper stub.
# Designed to be a USERJOB of the form </path to script/transcode-h264.py %JOBID%>

from MythTV import Job, Recorded, System, MythDB, findfile, MythError, MythLog, datetime

from optparse import OptionParser
from glob import glob
from shutil import copyfile
import sys
import os
import errno
import time

transcoder = '/usr/bin/ffmpeg'
flush_commskip = False
build_seektable = True

def runjob(jobid=None, chanid=None, starttime=None):
    db = MythDB()
    if jobid:
        job = Job(jobid, db=db)
        chanid = job.chanid
        starttime = job.starttime
    rec = Recorded((chanid, starttime), db=db)

    sg = findfile('/'+rec.basename, rec.storagegroup, db=db)
    if sg is None:
        print 'Local access to recording not found.'
        sys.exit(1)

    infile = os.path.join(sg.dirname, rec.basename)
    tmpfile = '%s.tmp' % infile.rsplit('.',1)[0]
    outfile = '%s.mp4' % infile.rsplit('.',1)[0]

    # reformat 'starttime' for use with mythtranscode/ffmpeg/mythcommflag
    starttime = str(starttime.utcisoformat().replace(u':', '').replace(u' ', '').replace(u'T', '').replace('-', ''))

    # Lossless transcode to strip cutlist
    if rec.cutlist == 1:
        if jobid:
            job.update({'status':4, 'comment':'Removing Cutlist'})

        task = System(path='mythtranscode', db=db)
        try:
            output = task('--chanid "%s"' % chanid,
                          '--starttime "%s"' % starttime,
                          '--mpeg2',
                          '--honorcutlist',
                          '--profile autodetect',
                          '--allkeys',
                          '-o "%s"' % tmpfile)
        except MythError, e:
            print 'Command failed with output:\n%s' % e.stderr
            if jobid:
                job.update({'status':304, 'comment':'Removing Cutlist failed'})
            sys.exit(e.retcode)
    else:
        copyfile('%s' % infile, '%s' % tmpfile)

    # Transcode to mp4
    if jobid:
        job.update({'status':4, 'comment':'Transcoding to mp4'})

    task = System(path=transcoder, db=db)
    try:
        output = task('-y -i "%s"' % tmpfile,
                      '-r 30',
                      '-map 0 -map -0:m:language:spa',
                      '-c:a libmp3lame -b:a 128k',
                      '-scodec mov_text',
                      '-vcodec libx264',
                      '-tune animation',
                      '-preset ultrafast',
                      '-crf 30',
                      '-threads 4',
                      '"%s"' % outfile)
    except MythError, e:
        print 'Command failed with output:\n%s' % e.stderr
        if jobid:
            job.update({'status':304, 'comment':'Transcoding to mp4 failed'})
        sys.exit(e.retcode)

    rec.basename = os.path.basename(outfile)
    os.remove(infile)
    # Cleanup the old *.png files
    for filename in glob('%s*.png' % infile):
        os.remove(filename)
    os.remove(tmpfile)
    try:
        os.remove('%s.map' % tmpfile)
    except OSError:
        pass
    rec.filesize = os.path.getsize(outfile)
    rec.transcoded = 1
    rec.seek.clean()

    if flush_commskip:
        for index,mark in reversed(list(enumerate(rec.markup))):
            if mark.type in (rec.markup.MARK_COMM_START, rec.markup.MARK_COMM_END):
                del rec.markup[index]
        rec.bookmark = 0
        rec.cutlist = 0
        rec.markup.commit()

    rec.update()

    if jobid:
        job.update({'status':4, 'comment':'Rebuilding seektable'})

    if build_seektable:
	task = System(path='mythcommflag')
        task.command('--chanid %s' % chanid,
                     '--starttime %s' % starttime,
                     '--rebuild')
    if jobid:
        job.update({'status':272, 'comment':'Transcode Completed'})

def main():
    parser = OptionParser(usage="usage: %prog [options] [jobid]")

    parser.add_option('--chanid', action='store', type='int', dest='chanid',
            help='Use chanid for manual operation')
    parser.add_option('--starttime', action='store', type='int', dest='starttime',
            help='Use starttime for manual operation')
    parser.add_option('-v', '--verbose', action='store', type='string', dest='verbose',
            help='Verbosity level')

    opts, args = parser.parse_args()

    if opts.verbose:
        if opts.verbose == 'help':
            print MythLog.helptext
            sys.exit(0)
        MythLog._setlevel(opts.verbose)

    if len(args) == 1:
        runjob(jobid=args[0])
    elif opts.chanid and opts.starttime:
        runjob(chanid=opts.chanid, starttime=opts.starttime)
    else:
        print 'Script must be provided jobid, or chanid and starttime.'
        sys.exit(1)

if __name__ == '__main__':
    main()
```

---

### Post by blm-ubunet on 2016-02-25
Do you really want to transcode H264? Why?
Are your recordings mpeg2 video?

That script is just using the built-in commercial detection ..
That script can only cut & transcode mpeg2 because fifo mode is not used.

Usually the detection scripts need to be tweaked to work well in different areas/countries.
Why don't you just enable commflag jobs on your recordings.
You can then view/check/tweak cut points in the editor. So commflag marks become cut marks.

My H264 recording cutter script rebuilds seektable & updates dB in a similar fashion & rewind/seeking is perfect.

You have to use mythcommflag to rebuild seektable on H264 (unless you using master/0.28).

H264 recordings may be smaller but editing them is much harder.
MythTV lossless transcode cutter can not work directly with H264 without using fifo passthru mode to external encoder like ffmpeg & x264.

---

### Post by SagaciousKJB on 2016-02-26
> **blm-ubunet said:**
> Do you really want to transcode H264? Why?
Are your recordings mpeg2 video?

That script is just using the built-in commercial detection ..
That script can only cut & transcode mpeg2 because fifo mode is not used.

Usually the detection scripts need to be tweaked to work well in different areas/countries.
[B]Why don't you just enable commflag jobs on your recordings.
You can then view/check/tweak cut points in the editor. So commflag marks become cut marks.[/B]

My H264 recording cutter script rebuilds seektable & updates dB in a similar fashion & rewind/seeking is perfect.

**You have to use mythcommflag to rebuild seektable on **H264 (unless you using master/0.28).

H264 recordings may be smaller but editing them is much harder.
MythTV lossless transcode cutter can not work directly with H264 without using fifo passthru mode to external encoder like ffmpeg & x264.

That is what I tried but the detected commercials don't line up with the right parts of the episode even when the detection times seemed right, and won't even skip anyway. Rewind and seeking work, just not skipping. If I try to go to Edit mode to apply the commercials ad a cultist it says there is no seek table, even after rebuilding it with mythcommflag. If I try using mythranscode instead I can load them as a cultist, but then it can't seek at all. 

I record to mpeg2 and the files are too large I need better compression.

Could you post your script or maybe show me what specifically you do to rebuild the seek table?

---

### Post by blm-ubunet on 2016-02-27
I don't understand how seeking can work & then the cut-list editor complains there is no seektable.
But MythTV can seek without a seektable but it is slow/imprecise/possible-macroblocked.

So how slow is normal seeking on your original mpeg2 recordings ?
Should be lightening fast..

Your recordings come from ATSC/DVB type tuner?
You can run mythcommflag with extra verbose logging to find the problem..

There is a suggestion that problem mpeg2 files could try:
mythtranscode --mpeg2 --buildindex --allkeys --showprogress --infile <filepath>
[https://www.mythtv.org/wiki/Repairing_the_Seektable](https://www.mythtv.org/wiki/Repairing_the_Seektable)

No secret sauce with mythcommflag (note that old mythtranscode can't rebuild H264 files)
Any cutting script should rebuild seektable after the cut.
```
mythcommflag  --rebuild --chanid $CHANID --starttime $STARTTIME
```
& clear the cutlist & skiplist after the cut:
```
mythutil --clearcutlist  --chanid $CHANID --starttime $STARTTIME
mythutil --clearskiplist --chanid $CHANID --starttime $STARTTIME
```
where STARTTIME has been massaged to remove spaces & ":" char.

mythcommflag & mythutil have both had bugs were they can not handle spaces in parameters etc or mythtv's own time format strings.

alt cmdline:
mythcommflag --rebuild --file filename
IIRC filename has to be found in storage groups, don't think it needs full path..
[https://www.mythtv.org/wiki/Mythcommflag#Rebuild_Seektable](https://www.mythtv.org/wiki/Mythcommflag#Rebuild_Seektable)

---

### Post by SagaciousKJB on 2016-02-27
> **blm-ubunet said:**
> I don't understand how seeking can work & then the cut-list editor complains there is no seektable.
But MythTV can seek without a seektable but it is slow/imprecise/possible-macroblocked.

So how slow is normal seeking on your original mpeg2 recordings ?
Should be lightening fast..

Your recordings come from ATSC/DVB type tuner?
You can run mythcommflag with extra verbose logging to find the problem..

There is a suggestion that problem mpeg2 files could try:
mythtranscode --mpeg2 --buildindex --allkeys --showprogress --infile <filepath>
[https://www.mythtv.org/wiki/Repairing_the_Seektable](https://www.mythtv.org/wiki/Repairing_the_Seektable)

No secret sauce with mythcommflag (note that old mythtranscode can't rebuild H264 files)
Any cutting script should rebuild seektable after the cut.
```
mythcommflag  --rebuild --chanid $CHANID --starttime $STARTTIME
```
& clear the cutlist & skiplist after the cut:
```
mythutil --clearcutlist  --chanid $CHANID --starttime $STARTTIME
mythutil --clearskiplist --chanid $CHANID --starttime $STARTTIME
```
where STARTTIME has been massaged to remove spaces & ":" char.

mythcommflag & mythutil have both had bugs were they can not handle spaces in parameters etc or mythtv's own time format strings.

alt cmdline:
mythcommflag --rebuild --file filename
IIRC filename has to be found in storage groups, don't think it needs full path..
[https://www.mythtv.org/wiki/Mythcommflag#Rebuild_Seektable](https://www.mythtv.org/wiki/Mythcommflag#Rebuild_Seektable)

Seeking works very smooth actually, I don't notice a difference between seeking in the h264 and the mpeg2 files. Im recording from ATSC

I tried that mythtranscode command. It made me able to load the editor with no warning about No seektable, but then I can't actually seek at all. I can load the skip list as a cut list but the cuts don't actually do anything.

Also just to clarify, I am not trying to cut the commercials out. I just want to preserve the cultist so I can use Auto skip.

I'll try running mythcomflag with verbose but I have noticed in the job queue after running it on a transcode, it says it found a number of commercials, usually 3 to 5. If I look in the database where the skip list markup is there's data there too, though I don't fully understand the format.

It's almost as if mythcomflag generates a skiplist but one where
-The times for the commercial breaks are out if sync
-The skip list doesn't actually skip

So for example say I run commercial detection on an h264 transcode, and play it with ability to seek forward and backward, but not able to skip between the skip points at all. However if I put "Auto Notify" on instead of Auto skip, it pops up the commercial notice the same amount of times to correspond to how many commercial breaks it claimed to find, but instead of showing the notice during the commercial it shows the notice in the middle of the show.

But, and this is important, if I run thst mythtranscode command to rebuild with all key frames, I can load the Editing mode and load the commercials as a cultist and it seems like they are in the right spots, based on past experience flagging commercials on the same network and show. Though like I said, then seeking won't work at all...

Sorry that was probably a little much to read but it's some pretty specific behavior. I think myth front-end can seek through h264 files without a seektable, but for some reason can't use the skip list. However whatever seektable mythtranscode builds doesn't seem to work, except to load the Editor and show the cultist markup.

---

### Post by blm-ubunet on 2016-02-27
Just to clarify (?):
- mythtranscode can not generate seektables for H264 (unless fixed recently)
- after transcode must regenerate seektable & any prob. any comm skip marks
- after cutting have to clear the old cutlist etc

The seektable the results from running mythtranscode on H264 files is probably blank.

I could try reproduce the problem here.. can you cut sample 100MB from start of recording with "dd"?

With MythTV 0.28, mythcommflag works very well out of the box!
The cut-list editor worked correctly, loaded comm skip points & allowed correction/addition & saving cutlist.
Didn't try skipping to the cut marks..
With one program it missed 2 breaks & one was short but the cut end points were right.
Another program it missed first ad break & one was short, cut ends were right.
With zero tuning this is very good performance considering how slick/seamless TV broadcasting is here..

Suspicion must fall on the transcoded file & the versions of ffmpeg & x264 installed.
MythTV master has internal copy ffmpeg 3.0, your packages might expose it as mythffmpeg.

---

### Post by SagaciousKJB on 2016-02-28
> **blm-ubunet said:**
> Just to clarify (?):
- mythtranscode can not generate seektables for H264 (unless fixed recently)
- after transcode must regenerate seektable & any prob. any comm skip marks
- after cutting have to clear the old cutlist etc

The seektable the results from running mythtranscode on H264 files is probably blank.

I could try reproduce the problem here.. can you cut sample 100MB from start of recording with "dd"?

With MythTV 0.28, mythcommflag works very well out of the box!
The cut-list editor worked correctly, loaded comm skip points & allowed correction/addition & saving cutlist.
Didn't try skipping to the cut marks..
With one program it missed 2 breaks & one was short but the cut end points were right.
Another program it missed first ad break & one was short, cut ends were right.
With zero tuning this is very good performance considering how slick/seamless TV broadcasting is here..

Suspicion must fall on the transcoded file & the versions of ffmpeg & x264 installed.
MythTV master has internal copy ffmpeg 3.0, your packages might expose it as mythffmpeg.
Hmm

[B]Just to clarify (?):
- mythtranscode can not generate seektables for H264 (unless fixed recently)
- after transcode must regenerate seektable & any prob. any comm skip marks
- after cutting have to clear the old cutlist etc[/B]
1. Seems correct, it just allows me to load the Editor, but no cuts or seeking work
2. The transcode script I'm using runs mythcommflag to rebuild the seektable and flushes commercial skips, I run a new commercial detection job on the transcode afterward
3. I don't think it does this since I don't load the commercials as a cutlist anyway, I just leave the skiplist

I am using myth 0.27.4-fixes, I had to compile myself to apply a patch for erroneous EIT data ([https://code.mythtv.org/trac/ticket/11739](https://code.mythtv.org/trac/ticket/11739)). Unfortunately the "fix" they committed doesn't actually work (despite them labeling it fixed) so I'm locked in with this version.  Did they make significant changes to mythcommflag between this version and 0.28?

My ffmpeg version I got from ffmpeg's own site and installed the .deb, so it's 3.0.0. I actually tried compiling myself last night too just to make sure there wasn't something funny with the binary but I had the same results.

Using mythtranscode is the only way I can get the editor to load on transcodes, but as you say the table itself seems to be blank. If the new mythcommflag allowed you to load skiplist in the editor, that's already one step ahead of what mine is doing.

Here's a 100 mb sample of an ATSC recording, this one is HD but I don't see any differing effects with SD content ( most of what I record ).

[https://www.dropbox.com/s/suru9phldgkxpmz/sample.mpg?dl=0](https://www.dropbox.com/s/suru9phldgkxpmz/sample.mpg?dl=0)

---

### Post by blm-ubunet on 2016-03-03
Your mpeg2video files seems normal but with bad AV sync (does not match value in file).
Your transcode command options (mp4 PS) does not allow mythcommflag to work.

Tried to find an H264 transcode that allows mythcommflag to work.. seems to need mpegts.
```
ffmpeg -i Videos/UF-SagaciousKJB-sample.mpg -map 0 -map -0:m:language:spa -c:a aac -b:a 128k -scodec mov_text -vcodec libx264 -preset slow -crf 30 -threads 4 -profile:v high -level:v 4.1 -f mpegts Videos/outfile3.mpg

ffmpeg -i Videos/UF-SagaciousKJB-sample.mpg -map 0 -map -0:m:language:spa -c:a aac -b:a 128k -scodec mov_text -vcodec libx264 -preset medium -crf 30 -threads 4 -profile:v high -level:v 4.1 -bsf:v h264_mp4toannexb Videos/outfile3.ts

```
Some of the other changes are not necessarily required.
The keyframe distance (the 1st ffmpeg option) is ~180 (v high c.f. broadcast) & is IDR.
Intraframe refresh with keyframes every 30-60 would be ideal..

Running mythcommflag with logging:-
```
mythcommflag --syslog local7 --rebuild --video Videos/outfile3.[mpg|ts] -v all --loglevel=debug
cat /var/log/mythtv/mythcommflag.log | grep ,9,
 
```
reveals that mythcommflag is finding keyframes (which seem reasonable) but it does not seem to be able to use them in playback (from "Videos" screen at least).
Checking the dB tables:-
```
echo "select * from filemarkup where filename='Videos/outfile3.mpg' order by offset;" | mysql -N  $upass 
```
where upass="-umythtv -pmythtv -h192.168.0.1 mythconverg"
And the filename offsets & mark values seem fine/same as other files with seektables.

I'm starting to think that building seektable for files in "Videos" is broken..
[Update] mythcommflag fails to insert seek data (into dB) for files in local FE Videos folder, works okay with both the above transcoded files in BE Video storage group.

---

### Post by SagaciousKJB on 2016-03-03
> **blm-ubunet said:**
> Your mpeg2video files seems normal but with bad AV sync (does not match value in file).

Tried to find an H264 transcode that allows mythcommflag to work.. seems to need mpegts.
Your transcode command options (mp4 PS) does not allow mythcommflag to work.
```
ffmpeg -i Videos/UF-SagaciousKJB-sample.mpg -map 0 -map -0:m:language:spa -c:a aac -b:a 128k -scodec mov_text -vcodec libx264 -preset slow -crf 30 -threads 4 -profile:v high -level:v 4.1 -f mpegts Videos/outfile3.mpg

ffmpeg -i Videos/UF-SagaciousKJB-sample.mpg -map 0 -map -0:m:language:spa -c:a aac -b:a 128k -scodec mov_text -vcodec libx264 -preset medium -crf 30 -threads 4 -profile:v high -level:v 4.1 -bsf:v h264_mp4toannexb Videos/outfile3.ts

```
Some of the other changes were not necessarily required.

Running mythcommflag with logging:-
```
mythcommflag --syslog local7 --rebuild --video Videos/outfile3.[mpg|ts] -v all --loglevel=debug
cat /var/log/mythtv/mythcommflag.log | grep ,9,
 
```
reveals that mythcommflag is finding keyframes (which seem reasonable) but it does not seem to be able to use them in playback (from "Videos" screen at least).
Checking the dB tables:-
```
echo "select * from filemarkup where filename='Videos/outfile3.mpg' order by offset;" | mysql -N  $upass 
```
And the filename offsets & mark values seem fine/same as other files with seektables.

I'm starting to think that building seektable for files in "Videos" is broken..
I have seektables for many existing samples but not all..

One of my stations kept putting Audio Description subtitles in the Spanish audio stream and ffmpeg was choosing it by default for some reason.

Hmmm is there a way to play the mpegts ts and mpg file from the "Watch Recordings" screen or would it make a difference? I don't know anything about mpegts. Do ts and mpg files just need to be in the same directory as each other, and if so would I have update the database to point at the ts file or the mpg?

Thanks for all the help so far!

---

### Post by blm-ubunet on 2016-03-04
I was using "Videos" because it was easiest solution.
It just caused problems using the FE's local video folder.

It is normally possible to record your mpeg2video file into recordings but I have hacked this to test H264.

The mpegts file will play just fine in "recordings"; all your mpeg2video recordings are already transport stream files. All OTA broadcast (DVB/ATSC) are TS.

The transcode script (you're using) converts transport stream to program stream container; there's lots of reasons to retain ts container.
Doesn't your transcode script rename the original & place the transcode in place of original ?? that's what a sensible transcoding script would do.

MythTV historically used mpg extension for TS & PS recording files. MythTV 0.28 is using .ts extension for mpegts & .mpg for PS. It has no effect except for DLNA clients (maybe).

Both of the ffmpeg cmd options (posted prev.) generate TS files & both should really be .ts but the script can just leave the file extension unchanged.
Rebuilding the seektable also fixes the duration etc.

---

### Post by SagaciousKJB on 2016-03-04
> **blm-ubunet said:**
> I was using "Videos" because it was easiest solution.
It just caused problems using the FE's local video folder.

It is normally possible to record your mpeg2video file into recordings but I have hacked this to test H264.

The mpegts file will play just fine in "recordings"; all your mpeg2video recordings are already transport stream files. All OTA broadcast (DVB/ATSC) are TS.

The transcode script (you're using) converts transport stream to program stream container; there's lots of reasons to retain ts container.
Doesn't your transcode script rename the original & place the transcode in place of original ?? that's what a sensible transcoding script would do.

MythTV historically used mpg extension for TS & PS recording files. MythTV 0.28 is using .ts extension for mpegts & .mpg for PS. It has no effect except for DLNA clients (maybe).

Both of the ffmpeg cmd options (posted prev.) generate TS files & both should really be .ts but the script can just leave the file extension unchanged.
Rebuilding the seektable also fixes the duration etc.

That makes a huge difference! I can load commercials as cultists and use the editor now. Interestingly though it wouldn't automatically skip commercials until I loaded them as a cultist though.

A weird thing about the ts file... It seems to work even if I delete it afterwards, is it supposed to be temporary?

---

### Post by blm-ubunet on 2016-03-05
I have no idea what you have done with the ffmpeg cmd options posted..so hard to comment..

The idea was to edit the script to add the "-f mpegts" & maybe "-forced-idr 1" & change the file extension from mp4 to mpg or ts..

The script (AIUI) renames the job recording file to <basename>.tmp & then transcodes it to <basename>.mp4 so it replaces the original recording.
The script updates the filename in dB for the recording via the recordedid or chanid&starttime fields.

If you're planning to transcode interlaced video you need to deinterlace with yadif filter (for example) & can then use interlaced H264 encoding with ffmpeg (libx264).

---

### Post by SagaciousKJB on 2016-03-05
```
ffmpeg -i Videos/UF-SagaciousKJB-sample.mpg -map 0 -map -0:m:language:spa -c:a aac -b:a 128k -scodec mov_text -vcodec libx264 -preset slow -crf 30 -threads 4 -profile:v high -level:v 4.1 -f mpegts Videos/outfile3.mpg

ffmpeg -i Videos/UF-SagaciousKJB-sample.mpg -map 0 -map -0:m:language:spa -c:a aac -b:a 128k -scodec mov_text -vcodec libx264 -preset medium -crf 30 -threads 4 -profile:v high -level:v 4.1 -bsf:v h264_mp4toannexb Videos/outfile3.ts
```

I used these ffmpeg commands you posted ( with different encoder options) one after the other in the script, and then as you said changing it to just leave the mpg, and then after I tried remove the ts file and it worked so I added the last line to do it automatically.

Are they both supposed to be run, or did I just need one of the ffmpeg commands and to change the extension to mpg or ts depending on which I choose?

```
infile = os.path.join(sg.dirname, rec.basename)
    tmpfile = '%s.tmp' % infile.rsplit('.',1)[0]
    outfile = '%s.mpg' % infile.rsplit('.',1)[0]
    tsfile = '%s.ts' % infile.rsplit('.',1)[0]


...

# Transcode to mp4
    if jobid:
        job.update({'status':4, 'comment':'Transcoding to h264'})

    task = System(path=transcoder, db=db)
    try:
        output = task('-y -i "%s"' % tmpfile,
                      '-map 0 -map -0:m:language:spa',
                      '-c:a libmp3lame -b:a 128k',
                      '-scodec copy',
                      '-vcodec libx264',
                      '-preset ultrafast',
                      '-crf 29',
                      '-threads 0',
                      '-profile:v high',
                      '-level:v 4.1',
                      '-f mpegts',
                      '"%s"' % outfile,
                      '> /tmp/ffmpeg_status 2>&1 < /dev/null')
    except MythError, e:
        print 'Command failed with output:\n%s' % e.stderr
        if jobid:
            job.update({'status':304, 'comment':'Transcoding to h264 failed'})
        sys.exit(e.retcode)
    if jobid:
        job.update({'status':4, 'comment':'Transcoding to ts'})

    task = System(path=transcoder, db=db)
    try:
        output = task('-y -i "%s"' % tmpfile,
                      '-map 0 -map -0:m:language:spa',
                      '-c:a libmp3lame -b:a 128k',
                      '-scodec copy',
                      '-vcodec libx264',
                      '-preset ultrafast',
                      '-crf 29',
                      '-threads 0',
                      '-profile:v high',
                      '-level:v 4.1',
                      '-bsf:v h264_mp4toannexb',
                      '"%s"' % tsfile,
                      '> /tmp/ffmpeg_status 2>&1 < /dev/null')
    except MythError, e:
        print 'Command failed with output:\n%s' % e.stderr
        if jobid:
            job.update({'status':304, 'comment':'Transcoding to ts failed'})
        sys.exit(e.retcode)

    rec.basename = os.path.basename(outfile)
    os.remove(tsfile)
```

---

### Post by blm-ubunet on 2016-03-05
Yeah, only need to use one of the ffmpeg cmd options.
Just wanted to show more than one example that worked..
Note mp4 (AFAIK) normally refers to mpeg4 ASP video in mpeg PS container.
 
I wouldn't use MP3 audio in mpeg TS container better to use AAC for wider compatibility. Also MP3 was never designed for quality audio (exact opposite in fact).

You could use .mpg extension for both ffmpeg command options, it likely matches name of your original mpeg2video file.
The latest mythtv is using .ts for all recordings from DVB/ATSC etc.

"mythutil --chanid blah --starttime blah --gencutlist" can be used to load the commflag marks into the cutlist.

---

### Post by SagaciousKJB on 2016-03-05
> **blm-ubunet said:**
> Yeah, only need to use one of the ffmpeg cmd options.
Just wanted to show more than one example that worked..
Note mp4 (AFAIK) normally refers to mpeg4 ASP video in mpeg PS container.
 
I wouldn't use MP3 audio in mpeg TS container better to use AAC for wider compatibility. Also MP3 was never designed for quality audio (exact opposite in fact).

You could use .mpg extension for both ffmpeg command options, it likely matches name of your original mpeg2video file.
The latest mythtv is using .ts for all recordings from DVB/ATSC etc.

"mythutil --chanid blah --starttime blah --gencutlist" can be used to load the commflag marks into the cutlist.
Nice! Thanks for all the help!

That's interesting they're switching, are they going to have backward compatibility to play mpg in old collections? I probably won't upgrade for quite a while since I need EIT patches... Maybe someday I'll get cable and just use schedules direct. 

I am a little out of date on audio codecs, I always liked mp3. I am half deaf so literally don't notice a difference between 128kB mp3 and flac. Kind of sucks, but so yeah I tend to go for highest compression.

Anyway thanks again for all the help, it's usually kind if tough for me to find mythtv support. Do you know of any other places with active myth users?

I am liking the mpegts so far, would there be any distinct advantages to using the second ffmpeg command you showed instead?

---

### Post by blm-ubunet on 2016-03-05
The file extension is just a nicety for user, in linux it does not really matter.
The first 4 bytes of a file are/can be used to determine the type.
MythTV will play your files with any or no extension if the database points to it.
Some DLNA clients need the right extension or at least the right file type descriptor supplied from somewhere.
Most of my old recordings are .mpg (H264 mpegts) & play fine in mythtv master.

MP3 was just a accident of history & timing, was intended for very low bitrate speech over radio telephones etc. Arguably the worst codec choice for HQ audio.

I believe that a compliant stream/file of H264 in mpeg container has to use annex B bitstream (00 00 00 01 hex start-code).
h264_mp4toannexb is used when converting mp4 to mpegts container.

So possibly the 2nd ffmpeg command option is the only correct one for "H264 in mpegts".

All the activity has been on MythTV mailing list or forums or IRC.

---

### Post by SagaciousKJB on 2016-03-06
Is it possible to use "mythtranscode --honorcutlist" to strip commercials out of already-transcoded recordings? I gave it a shot and got a weird result...

This is how I'm running mythtranscode

```
mythtranscode --chanid $1 --starttime $2 --honorcutlist --mpeg2 --allkeys
```

```
2016-03-06 13:11:55.214140 W  Warning: partial frame found!
2016-03-06 13:11:55.214167 W  Warning: partial frame found!
2016-03-06 13:11:55.214177 W  Warning: partial frame found!
*Contiues like that*
2016-03-06 13:11:55.229865 W  Warning: partial frame found!
2016-03-06 13:11:55.229873 W  Warning: partial frame found!
2016-03-06 13:11:55.229890 E  No more queue slots!
2016-03-06 13:11:55.246311 E  Transcoding /media/tb1/mythtv/1292_20160306043000.mpg failed

```

Edit:

I found a script to do it via filename but I get an error about no profiles found for H.264.  I'm gussing I just can't do lossless transcoding on h264 files to retroactively remove commercials from transcoded files?

```
2016-03-06 13:42:52.946010 C  mythtranscode version: fixes/0.27 [v0.27.4-38-ga2563e1-dirty] www.mythtv.org
2016-03-06 13:42:52.946046 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2016-03-06 13:42:53.213296 E  Transcode: Couldn't find profile for : H.264
2016-03-06 13:42:53.213304 E  Transcoding aborted, no profile found.
2016-03-06 13:42:53.215330 E  Transcoding /media/laptop/mythtv/1292_20160306050000.mpg failed

```

I wonder if there is a way to turn the cutlist information into start and duration points for ffmpeg to encode (via copy so it doesn't actually encode ) and then concatenate them together as one file?

I guess it'd just be simpler to remember to modify the cutlist before I transcode, but I have a bunch of old transcodes i never stripped commercials for I wanted to see if I could fix.

---

### Post by blm-ubunet on 2016-03-07
As mentioned previous.. mythtranscode does not grok H264 video except in fifo mode.
Fifo mode uses external encoder like (myth)ffmpeg & libx264.

You have to regenerate any cutlist after transcoding & especially with H264 as most (all) of the cutting scripts require keyframe cuts. The keyframe number & location could be totally different.
I would tweak the H264 encoding process to get 2 keyframes per second, the default is too sparse.

There are a couple of cutting scripts that use time cut list & ffmpeg, losslesscut uses mkvtoolnix & mkv output files. Sadly, mythtv will not generate seektables for mkv (AVCC mp4 format H264).
At one point ffmpeg was only accurate when decoding/encoding (& not muxing) so loss PQ & time but this might have changed with a new filter.
LossLessCut does not handle a very common audio bitstream in common use with DVB (outside US) because mkvtoolnix does not..

I have used this fast & dirty cutting script that works on any 188 byte transport stream.
[https://gist.github.com/BipedalTV/3174241](https://gist.github.com/BipedalTV/3174241)
You must consider the audio video packet offset (eff. time delay) in the file.
Your homebrew H264 files may not have any, broadcast typically has 0.5 to 2 seconds.

---

### Post by SagaciousKJB on 2016-03-08
> **blm-ubunet said:**
> As mentioned previous.. mythtranscode does not grok H264 video except in fifo mode.
Fifo mode uses external encoder like (myth)ffmpeg & libx264.

You have to regenerate any cutlist after transcoding & especially with H264 as most (all) of the cutting scripts require keyframe cuts. The keyframe number & location could be totally different.
I would tweak the H264 encoding process to get 2 keyframes per second, the default is too sparse.

There are a couple of cutting scripts that use time cut list & ffmpeg, losslesscut uses mkvtoolnix & mkv output files. Sadly, mythtv will not generate seektables for mkv (AVCC mp4 format H264).
At one point ffmpeg was only accurate when decoding/encoding (& not muxing) so loss PQ & time but this might have changed with a new filter.
LossLessCut does not handle a very common audio bitstream in common use with DVB (outside US) because mkvtoolnix does not..

I have used this fast & dirty cutting script that works on any 188 byte transport stream.
[https://gist.github.com/BipedalTV/3174241](https://gist.github.com/BipedalTV/3174241)
You must consider the audio video packet offset (eff. time delay) in the file.
Your homebrew H264 files may not have any, broadcast typically has 0.5 to 2 seconds.

Oh that's an interesting script, would not have thought of using dd. Unfortunately most of my old recordings are in the PS mp4 containers.

---

### Post by blm-ubunet on 2016-03-08
You could remux then into mpegts (without any transcoding) with maybe a 5% size increase..
Should run almost as fast as file copy.
Then mythtv can generate seektables & resulting playback seeking will be instant & accurate.

But be aware the transcoding script (you were using) has sparse keyframes so cutting accuracy (cut at the precise scene you want) could be poor.

---

### Post by SagaciousKJB on 2016-03-08
> **blm-ubunet said:**
> You could remux then into mpegts (without any transcoding) with maybe a 5% size increase..
Should run almost as fast as file copy.
Then mythtv can generate seektables & resulting playback seeking will be instant & accurate.

But be aware the transcoding script (you were using) has sparse keyframes so cutting accuracy (cut at the precise scene you want) could be poor.
How is that done? I was thinking of running ffmpeg with x264 set to crf 0 and copy the audio stream, but didn't know if that's the right way. Can't I tell x264 to add more key frames too?

I for some reason can't play the new mpegts files on Android (using Android VLC) , they start skipping and pausing. The mp4 containers worked fine so I wonder what the difference is. They sometimes get slowed down on 1080 video but not like this. Files alway seem to start playing back badly at the same point in the file too.

Seems like an audio sync option, playing the same files in the mythplayer, the av gets way off sync. I guess it just skips and pauses on Android at that point.

Is this a result of the encoding process or something I could tweak? I am still using mp3 too, aac just didn't sound very good to me, but could it be the mp3 format? Maybe I'll go take a peak at what ffmpeg has been saying and post it up here.

This is the ffmpeg options I'm using
```
output = task('-y -i "%s"' % tmpfile,
                      '-r 30',
                      '-map 0 -map -0:m:language:spa',
                      '-c:a libmp3lame -b:a 128k',
                      '-scodec copy',
                      '-vcodec libx264',
                      '-preset ultrafast',
                      '-crf 28',
                      '-threads 0',
                      '-f mpegts',
                      '"%s"' % outfile,
                      '> /tmp/ffmpeg_status 2>&1 < /dev/null')
```
(Still using mp3, aac didn't sound as good for some reason, have to tweak it later)

Maybe it's because I'm dropping the framerate down to 30? It saves more space than keeping it at 60 but I could see why it would make it harder for the A/V to match up.

I see a lot of these errors in the ffmpeg_status file I've logged to which seem like they could be indicating audio/video problems with the OTA recording but I don't know enough about this stuff.
```
[ac3 @ 0x2120140] error decoding the audio block
[ac3 @ 0x2120800] exponent -1 is out-of-range
[ac3 @ 0x2120800] error decoding the audio block
[ac3 @ 0x2120800] frame sync error
Error while decoding stream #0:2: Invalid data found when processing input
[ac3 @ 0x2120800] exponent 25 is out-of-range
[ac3 @ 0x2120800] error decoding the audio block
[ac3 @ 0x2120140] frame sync error
Error while decoding stream #0:1: Invalid data found when processing input
[ac3 @ 0x2120800] frame sync error
Error while decoding stream #0:2: Invalid data found when processing input
[ac3 @ 0x2120800] new bit allocation info must be present in block 0
[ac3 @ 0x2120800] error decoding the audio block
[ac3 @ 0x2120800] frame sync error
Error while decoding stream #0:2: Invalid data found when processing input
[ac3 @ 0x2120140] exponent 26 is out-of-range
[ac3 @ 0x2120140] error decoding the audio block
[ac3 @ 0x2120140] frame sync error
Error while decoding stream #0:1: Invalid data found when processing input
[ac3 @ 0x2120140] exponent -1 is out-of-range
[ac3 @ 0x2120140] error decoding the audio block
[ac3 @ 0x2120140] frame sync error
Error while decoding stream #0:1: Invalid data found when processing input
[mpeg2video @ 0x211fa80] ac-tex damaged at 19 6
[mpeg2video @ 0x211fa80] Warning MVs not available
[mpeg2video @ 0x211fa80] concealing 1120 DC, 1120 AC, 1120 MV errors in I frame
[mpeg2video @ 0x211fa80] Warning MVs not available
[mpeg2video @ 0x211fa80] concealing 674 DC, 674 AC, 674 MV errors in P frame
[mpeg2video @ 0x211fa80] ac-tex damaged at 38 1
[mpeg2video @ 0x211fa80] ac-tex damaged at 73 6
[mpeg2video @ 0x211fa80] ac-tex damaged at 51 29
[mpeg2video @ 0x211fa80] ac-tex damaged at 59 10
[mpeg2video @ 0x211fa80] Warning MVs not available
[mpeg2video @ 0x211fa80] concealing 1181 DC, 1181 AC, 1181 MV errors in P frame
[mpeg2video @ 0x211fa80] skipped MB in I frame at 62 36
[mpeg2video @ 0x211fa80] invalid mb type in I Frame at 24 37
[mpeg2video @ 0x211fa80] skipped MB in I frame at 45 24
[mpeg2video @ 0x211fa80] ac-tex damaged at 4 29
[mpeg2video @ 0x211fa80] Warning MVs not available
[mpeg2video @ 0x211fa80] concealing 387 DC, 387 AC, 387 MV errors in I frame
frame= 6509 fps= 92 q=25.0 size=   57988kB time=00:03:36.73 bitrate=2191.8kbits/s dup=0 drop=6496 speed=3.05x    ^M[ac3 @ 0x2120140] frame sync error
Error while decoding stream #0:1: Invalid data found when processing input
[ac3 @ 0x2120140] exponent -2 is out-of-range
[ac3 @ 0x2120140] error decoding the audio block

```

---

### Post by blm-ubunet on 2016-03-10
Your original mpeg2video file has odd/large AV offset. I have typically found that international samples of H264 ts (from OTA & HDPVR) to playback correctly using the reported AV offset.

Mpegts file audio & video packets are timestamped, changing AV error is **not possible** except if the timestamps are ignored or generated in error.
Forcing/changing framerates in ffmpeg seems problematic.

I'm fairly sure the only compliant stream/file for H264 in mpegts **must use**:
'-bsf:v h264_mp4toannexb'

AC3 & AAC audio are fine/allowed in mpegts container, mp3 (not standardised) might not be. AC3 on android device might be issue.

Sorry I can not believe AAC at 128K does not out perform MP3. Maybe the default AAC encoder settings in ffmpeg are poor; there has been a lot of recent work on the AAC encoder.

Also no broadcast OTA H264 uses I frames (HDPVR does).
Had no problems playing OTA H264 ts files on a tegra3 android device.

Some guesses:
Your original file is not 60fps but 60000/1001.
Maybe some of your files have variable framerate, this is common across US ad breaks.
Try not forcing the frame rate option in script / ffmpeg cmd.
And use the h264_mp4toannexb bitstream filter.

Halving the framerate does not halve the filesize because compression works on macro block tracking across multiple frames.

I don't know the required x264 options to generate a "broadcast grade" stream with B frame intra-refresh at 0.5 - 1 sec intervals.

---

### Post by SagaciousKJB on 2016-03-13
> **blm-ubunet said:**
> Your original mpeg2video file has odd/large AV offset. I have typically found that international samples of H264 ts (from OTA & HDPVR) to playback correctly using the reported AV offset.

Mpegts file audio & video packets are timestamped, changing AV error is **not possible** except if the timestamps are ignored or generated in error.
Forcing/changing framerates in ffmpeg seems problematic.

I'm fairly sure the only compliant stream/file for H264 in mpegts **must use**:
'-bsf:v h264_mp4toannexb'

AC3 & AAC audio are fine/allowed in mpegts container, mp3 (not standardised) might not be. AC3 on android device might be issue.

Sorry I can not believe AAC at 128K does not out perform MP3. Maybe the default AAC encoder settings in ffmpeg are poor; there has been a lot of recent work on the AAC encoder.

Also no broadcast OTA H264 uses I frames (HDPVR does).
Had no problems playing OTA H264 ts files on a tegra3 android device.

Some guesses:
Your original file is not 60fps but 60000/1001.
Maybe some of your files have variable framerate, this is common across US ad breaks.
Try not forcing the frame rate option in script / ffmpeg cmd.
And use the h264_mp4toannexb bitstream filter.

Halving the framerate does not halve the filesize because compression works on macro block tracking across multiple frames.

I don't know the required x264 options to generate a "broadcast grade" stream with B frame intra-refresh at 0.5 - 1 sec intervals.
Yeah everything I read said aac should be significantly better at the same bitrate, but it's more like the levels are off or something. I run the audio through the auxiliary on a nice stereo system I have, but with aac it sounds more as if it were using the TV speakers, just a really flat and tinny tone. I'll have to see if I can tweak the settings. 

I switched over to the hp4toannexb method and left the framerate alone and that seems to have helped a little, except only because now I can seek past the moment that doesn't playback right. Plus it seems to happen with only some recordings, so I am wondering if it's due to signal issues in the recordings, because I do get disruptions sometimes.

---

