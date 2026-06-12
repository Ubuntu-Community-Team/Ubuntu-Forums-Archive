---
title: "mytharchive dvd burning, audio out of sync or silence"
date: 2009-01-26
forum: Mythbuntu
---

### Post by faginbagin on 2009-01-26
Has anyone experienced a problem with audio on DVDs burned using mytharchive?

I recently upgraded to mythbuntu 8.04.1 which, after the latest updates, is running mythtv 0.21+fixes18207-0ubuntu4-hardy1. The first DVD I burned had audio problems, out of sync and 20 minutes into one recording, no sound at all. This was with the "Don't re-encode" encoder profile. The recordings were made with a PVR-150 on mythtv 0.20.2 (ubuntu 7.10). The recordings play back fine in 0.21 mythfrontend.

Since my system is partitioned with more than one O/S, I booted back into the old 7.10/0.20.2 system and burned a DVD with the exact same recordings and options. It was fine, audio in sync the whole way through each recording.

FWIW, I had trouble installing mythbuntu 8.10, but 8.04.1 went smoothly. The 8.10 installer had problems reading the desktop CD from both my CD burner and my DVD burner, even though I could verify the checksums on the CD using my old ubuntu environment. The only problem I've found with 8.04.1/0.21 so far is this one.

I'm hoping the audio issue is a known problem that's been fixed in a more recent version of 0.21 or in a library mytharchive depends on. I'd be willing to try to upgrade to mythbuntu 8.10 via synaptic or with the alternate installation CD if I could have some reassurance that DVDs burned from PVR-150 recordings on 8.10/021 have good audio. But I'm hesitant because of the problems I had trying to install 8.10.

Troubleshooting suggestions welcome, too.

TIA,
Helen

P.S. If this post looks familiar to some of you, that's because it's similar to one I posted on mythtv-users. So far, no one there has responded, so I thought I'd try here.

---

### Post by klc5555 on 2009-01-27
> **faginbagin said:**
> Has anyone experienced a problem with audio on DVDs burned using mytharchive?

I recently upgraded to mythbuntu 8.04.1 which, after the latest updates, is running mythtv 0.21+fixes18207-0ubuntu4-hardy1. The first DVD I burned had audio problems, out of sync and 20 minutes into one recording, no sound at all. This was with the "Don't re-encode" encoder profile. The recordings were made with a PVR-150 on mythtv 0.20.2 (ubuntu 7.10). The recordings play back fine in 0.21 mythfrontend.

Since my system is partitioned with more than one O/S, I booted back into the old 7.10/0.20.2 system and burned a DVD with the exact same recordings and options. It was fine, audio in sync the whole way through each recording.

FWIW, I had trouble installing mythbuntu 8.10, but 8.04.1 went smoothly. The 8.10 installer had problems reading the desktop CD from both my CD burner and my DVD burner, even though I could verify the checksums on the CD using my old ubuntu environment. The only problem I've found with 8.04.1/0.21 so far is this one.

I'm hoping the audio issue is a known problem that's been fixed in a more recent version of 0.21 or in a library mytharchive depends on. I'd be willing to try to upgrade to mythbuntu 8.10 via synaptic or with the alternate installation CD if I could have some reassurance that DVDs burned from PVR-150 recordings on 8.10/021 have good audio. But I'm hesitant because of the problems I had trying to install 8.10.

Troubleshooting suggestions welcome, too.

TIA,
Helen

P.S. If this post looks familiar to some of you, that's because it's similar to one I posted on mythtv-users. So far, no one there has responded, so I thought I'd try here.

The issue is mytharchive 0.21, not so much Ubuntu, so an 8.04 to 8.10 upgrade is unlikely to have any effect. It's still mytharchive 0.21. 

Audio sync is a perpetual problem with dvb recordings and mytharchive; this is the first time I've heard of it popping up with analog recordings  from a PVR 150.

I don't know of any current solution for mytharchive's audio sync problems. I suspect the problem has to do with the version of ffmpeg used in 0.21 and how it's configured. At any rate when audio sync becomes a deal-breaker on particular recordings, I use one or more workarounds.

The first is that I will try to archive the problem recordings using DeVeDe and mencoder (with k3b for the burn itself) which almost never suffer from audio sync problems, rather than using mytharchive. A version of DeVeDe later than 3.06 is recommended, since these versions will do simple menus. The recording(s) will have to have their commercials cut out by hand (from your cutlist) prior to feeding the recording to DeVeDe. This can be done with mythtranscode from the command prompt:

mythtranscode --mpeg2 --honorcutlist -c<channel> -s<starttime> 

where the file <your_recording>.mpg will produce a new temp file <your_recording>.mpg.tmp, which will have the commercials cut out and can in turn be fed directly to DeVeDe. Your original recording will be left untouched.

Sometimes, for no apparent reason, DeVeDe and mencoder will simply choke on a problem recording. In these cases, I'll use the command-line utility nuvexport to reencode the recording from mp3 to some other format (usually *.avi XVid), and in turn feed the *.avi to DeVeDe, where the archiving will now be successful.

Sometimes, when the audio sync problem is very minor on the mytharchived DVD, the problem can be solved by first cutting the recording manually, as described above, then making the temp file the recording to be archived, by moving the original recording to a backup: mv <recording>.mpg <recording>.mpg.old

and then make the temp file the recording: 
mv <recording>.mpg.tmp <recording>.mpg 

and now run mytharchive on the new <recording>.mpg The cutlist no longer applies to the new version of the recording, of course.

At any rate, don't expect mytharchive to get any better before 0.22 (and sadly probably not then), so if all you wish to upgrade for now is a possibly improved mytharchive, I think you may be better served by waiting.

Cheers!:)

---

### Post by faginbagin on 2009-01-27
Thanks for the suggestions. Your mention of ffmpeg gives me some ideas. I think I'll take a closer look at ffmpeg and also the codecs I've installed on both systems. Maybe there's a subtle difference there that I can fix by installing, uninstalling some codec packages and/or compiling source. The ffmpeg versions are nearly identical:
3:0.cvs20070307-5ubuntu4.1+medibuntu1 on 7.10/0.20.2
3:0.cvs20070307-5ubuntu7.1+medibuntu1 on 8.04.1/0.21
So maybe it's an audio codec.

I like using mytharchive for a couple of reasons:
1) DVD menus have recording title, date, time, description based on myth's database.
2) On 0.20.2, I did a fair amount of tinkering to add CCs in the form of subtitles, plus my own theme, and chapters based on myth's commercial flags. I was planning on porting this work to 0.21, but not until I can sort out the audio issue.
3) I burn DVDs in batch mode after I edit the config file passed from mytharchive to mythburn.pl. This allows me to continue to watch recordings while burning a DVD, which takes a really long time, especially with the processing done to add subtitles.

I wanted to try 0.21 on my existing system because I'm planning on building a new system in the near future, with an ATSC/QAM/NTSC tuner. I'm assuming CCs shouldn't be an issue in ATSC/QAM recordings because the VBI data should be embedded in the video stream and shouldn't be lost when prepping recordings for DVD, as long as there's no video transcoding. But first I wanted to make sure I could get all the functionality I'm used to on my current system. My workaround for now is to back up the 0.21 database, boot into the 0.20.2 system, backport the recorded* db tables into 0.20.2 (I've added table columns new in 0.21 and written a shell script to automate the back porting), then burn the recordings I want. This works, but it's inconvenient. I need to be careful which system gets to record new programs, otherwise, I'll lose track of them going back & forth.

Again, thanks for giving me some ideas to explore, and for pointing out that upgrading to mythbuntu 8.10 is probably a waste of time.

Helen

---

### Post by klc5555 on 2009-01-27
> **faginbagin said:**
> Thanks for the suggestions. Your mention of ffmpeg gives me some ideas. I think I'll take a closer look at ffmpeg and also the codecs I've installed on both systems. Maybe there's a subtle difference there that I can fix by installing, uninstalling some codec packages and/or compiling source. The ffmpeg versions are nearly identical:
3:0.cvs20070307-5ubuntu4.1+medibuntu1 on 7.10/0.20.2
3:0.cvs20070307-5ubuntu7.1+medibuntu1 on 8.04.1/0.21
So maybe it's an audio codec.

I like using mytharchive for a couple of reasons:
1) DVD menus have recording title, date, time, description based on myth's database.
2) On 0.20.2, I did a fair amount of tinkering to add CCs in the form of subtitles, plus my own theme, and chapters based on myth's commercial flags. I was planning on porting this work to 0.21, but not until I can sort out the audio issue.
3) I burn DVDs in batch mode after I edit the config file passed from mytharchive to mythburn.pl. This allows me to continue to watch recordings while burning a DVD, which takes a really long time, especially with the processing done to add subtitles.

I wanted to try 0.21 on my existing system because I'm planning on building a new system in the near future, with an ATSC/QAM/NTSC tuner. I'm assuming CCs shouldn't be an issue in ATSC/QAM recordings because the VBI data should be embedded in the video stream and shouldn't be lost when prepping recordings for DVD, as long as there's no video transcoding. But first I wanted to make sure I could get all the functionality I'm used to on my current system. My workaround for now is to back up the 0.21 database, boot into the 0.20.2 system, backport the recorded* db tables into 0.20.2 (I've added table columns new in 0.21 and written a shell script to automate the back porting), then burn the recordings I want. This works, but it's inconvenient. I need to be careful which system gets to record new programs, otherwise, I'll lose track of them going back & forth.

Again, thanks for giving me some ideas to explore, and for pointing out that upgrading to mythbuntu 8.10 is probably a waste of time.

Helen

Well, good luck on finding the ffmpeg/audio codec issue! It would certainly make mytharchive life easier for us all of us who use it if someone could correct this problem.

On the other hand, for you, why run 0.21 at all? The feature that finally got me to upgrade my machines from 0.20.2 was support for storage groups. If it weren't for that, I would still be happily running the  older and less buggy version.

As an aside, when you begin recording ATSC/QAM, I believe you'll have to begin reencoding, as the video stream will not be coming in at a resolution supported on analog DVD. But one problem at a time.

All the best!

---

### Post by faginbagin on 2009-01-27
If I find a solution, I promise to post it.

The reason for upgrading is to prepare for a new system. It will have a new mobo, so I'm assuming I'll need a new kernel, too. I've had trouble using older kernels with newer mobos before. It would be easiest to use a distro with a kernel that works for both the new system and my current system. My current system will become a slave backend/frontend.

You're probably right about reencoding ATSC/QAM streams. Argh! hadn't thought about that. If I find that vbi data is lost thru reencoding, it might just be time for me to really dig in and understand the MPEG specs and try to provide fixes to the open s/w community that can reencode while preserving vbi data. So far, I've only learned enough to decode the data stream that the ivtv driver adds to PVR-150 recordings, but I haven't learned how to decode the video stream. My impression is that CC/teletext isn't a priority to most of the developers involved in mythtv and the libraries it depends on. Maybe when they get a little older and their hearing starts to fade, they'll appreciate the value. For me, it's not that I'm hard of hearing, it's just that I like to watch a lot of British stuff and I don't always understand some of the accents.

Thanks,
Helen

---

### Post by klc5555 on 2009-01-28
> **faginbagin said:**
> If I find a solution, I promise to post it.

The reason for upgrading is to prepare for a new system. It will have a new mobo, so I'm assuming I'll need a new kernel, too. I've had trouble using older kernels with newer mobos before. It would be easiest to use a distro with a kernel that works for both the new system and my current system. My current system will become a slave backend/frontend. ... 

Well, one consideration is that mythtv is just an application, after all, and not particularly dependent on kernel level. On your new machine you could install a cutting edge full distro of your choice, and then install Myth 0.20.2, either from archive packages or compiling from source. Alternatively, you could first try the installation of an 0.20.2 Myth-centric distro, like Mythbuntu 7.10 (without 0.21 backports) or the equivalent Knoppmyth or Mythdora variants, whose kernels are all in the 2.6.22 range and are only a year-and-a-half old, and see how it goes. If it turns  out a newer kernel needs compiling, or, worst case, that cutting-edge distro really needs to be installed, then nothing much in time and effort will have been invested and it's got to be easier than trying to debug that mess of a ffmpeg/mythburn.py combination. 

All the best! :)

---

### Post by faginbagin on 2009-01-28
Yes, you're quite right that mythtv is an app and it isn't tied to a particular kernel. I guess it's the developer in me that just hates to be defeated. Plus, if I do need a new kernel/distro to support a new mobo, it would help to know the root cause of my problem, i.e. which package. If it's not in the mythtv source, then I'll have to start compiling older libraries it depends on, until I figure out which one is the culprit.

FWIW, I thought I had found the cause. I had installed some Windows codecs on the new system without thinking, which my old system didn't have. And the old system had the mencoder package, unlike the new system. So I uninstalled w32codec and installed mencoder, then burned a DVD. The first couple of recordings were fine, audio in sync, but the fourth one went silent after 12 minutes. At least the audio was in sync until that point.

Anyway, I'm going to forge ahead with debugging. I know I can go back if I need to.

---

### Post by faginbagin on 2009-01-31
I think I know what my problem was. The mytharchive script that does the real work for mytharchive, mythburn.py, executes mythtranscode using the python function os.system. For some reason, os.system was returning with an EPIPE error (errno=32), even though mythtranscode was successful. As a result, mythburn.py did not use the newfile.mpg file created by mythtranscode. Instead it used the original recording file for subsequent processing. I think that was the root cause of my problems.

Now the weird thing, I'm no longer getting the EPIPE error. I don't know why, maybe because I have since installed some more development packages. Anyway, it's working and I'm now working on porting my CCs to subtitles stuff.

---

### Post by bb_145 on 2009-03-20
Hi,

Did the problem come back?  I seem to be having a similar issue with MythArchive, but it is very intermittent.  

For some recordings, the sound cuts out at the point where I've cut the commercial.  For one recording I was able to fix the issue by clearing the cut list, and redoing it.  Another one though, redoing the cut list didn't work.  I even tried leaving in the block of commercials where the sound cut out, but then the sound stopped after the next cut point...  A real pain. :(

---

### Post by faginbagin on 2009-03-20
I finally figured out that the EPIPE error only occured when I ran mythburn.py from an X terminal window. When I ran it when logged in via ssh, no problem. But in a X terminal window, I would see this error message:
```
ICE default IO error handler doing an exit(), pid = <pid>, errno = 32
```
The error is caused by ICE, the X11 Inter-Client Exchange library, which Qt uses, which mythreplex uses. I was able to work around the problem by adding the following command to the shell script I use to burn DVDs, before executing mythburn.py:
```
unset SESSION_MANAGER
```

If you're using the mytharchive plug-in in mythfrontend, it might be the same issue. If so, you should see the above error message in the mythburn.log file, which should be in your mytharchive tmp directory in a sub directory called logs. If that's the problem, you can run mythburn.py from the command line, e.g.:
```
unset SESSION_MANAGER
MYTHARCHIVEDIR=/usr/share/mythtv/mytharchive *(or wherever mytharchive is installed)*
MYTHARCHIVETMP=*<your mytharchive tmp directory>*
python $MYTHARCHIVEDIR/scripts/mythburn.py -j $MYTHARCHIVETMP/config/mydata.xml -l $MYTHARCHIVETMP/logs/progress.log
```

HTH

---

### Post by bb_145 on 2009-03-26
Thanks, 

However, I now think I have a different problem.  I don't get the error message in your post.

I've been looking in the mytharchive.log, and what seems to be happening is that when I transcode, I get the following message:

"fixing audio PTS inconsistency - diff:  0:00:00.0426  - need to add 1 frame(s)
encoding an MP2 audio frame"

I think it is at one of the commercial cut points.

Then, when DVDauthor runs, I get the error:

"WARN: audio sector out of range: -8310 (vobu #4401, pts 2197.272)."

and it is repeated hundreds of times.

I think both errors occur at the same point in the recording.

It is somehow related to the cut points- if I remove the the cut points, there is not a problem. I was even able to fix the problem once by removing the cut points and redoing them.  However, that doesn't always seem to work. The problem is also intermittent.  ~80% of the recordings seem to go OK.

If anyone has any suggestions, it would be appreciated.  Thanks.

---

### Post by klc5555 on 2009-03-26
> **bb_145 said:**
> Thanks, 

However, I now think I have a different problem.  I don't get the error message in your post.

I've been looking in the mytharchive.log, and what seems to be happening is that when I transcode, I get the following message:

"fixing audio PTS inconsistency - diff:  0:00:00.0426  - need to add 1 frame(s)
encoding an MP2 audio frame"

I think it is at one of the commercial cut points.

Then, when DVDauthor runs, I get the error:

"WARN: audio sector out of range: -8310 (vobu #4401, pts 2197.272)."

and it is repeated hundreds of times.

I think both errors occur at the same point in the recording.

It is somehow related to the cut points- if I remove the the cut points, there is not a problem. I was even able to fix the problem once by removing the cut points and redoing them.  However, that doesn't always seem to work. The problem is also intermittent.  ~80% of the recordings seem to go OK.

If anyone has any suggestions, it would be appreciated.  Thanks.

I've had a handful of files for which this has happened, where even if I cut the commercials manually with mythtranscode, neither mytharchive nor Devede would archive them. However, when it was something I really wanted to archive, and could not re-record, I discovered I could run the time-consuming nuvexport (which also understands the myth cutlist) on them (either the default with ffmpeg or with the --transcode switch), and export them to "files for DVDs" (that is, .mpg files). These .mpg's could, in turn, easily be archived with Devede. I've not had nuvexport ever fail completely on me.

---

### Post by bb_145 on 2009-04-04
> **klc5555 said:**
> I've had a handful of files for which this has happened, where even if I cut the commercials manually with mythtranscode, neither mytharchive nor Devede would archive them. However, when it was something I really wanted to archive, and could not re-record, I discovered I could run the time-consuming nuvexport (which also understands the myth cutlist) on them (either the default with ffmpeg or with the --transcode switch), and export them to "files for DVDs" (that is, .mpg files). These .mpg's could, in turn, easily be archived with Devede. I've not had nuvexport ever fail completely on me.


Thanks for the hint.  I think I now partially understand what is going wrong, and I have a work-around.  It looks like I'm getting small errors in the stream (with the video and audio slightly out of sync) that Mythtranscode needs to fix, or DVDauthor chokes.  Normally they are fixed fine but, sometimes, after the commercials are cut, there are still errors at the cut points that Mythtranscode hasn't fixed properly and the audio drops out at that point.

The work-around appears to be to select "re-encode" when setting up the mytharchive session.  In that case, FFMPEG re-encodes the stream and fixes the errors.  It is slow, but it consistently seems to work.:)

I just wish I knew why Mythtranscode doesn't fix the errors properly.

---

### Post by bb_145 on 2009-04-24
Well, my previously posted solution was working well for a couple of weeks, but I've run into another problem.  I have one recording that has the above mentioned sound dropping out issue.  However, this time if I use FFMPEG to re-encode before running DVDauthor, DVDauthor crashes.  There appears to be something wrong with the audio stream that is causing the problem.  Haven't figured out what yet.

Fortunately, I was able to find a solution: ProjectX.  ProjectX can be used to remove the commercials instead of Mythtranscode.  Mythachive is mostly set up to use it, though ProjectX needs to be installed (can be done from add/remove programs) and "Use ProjectX" needs to be selected.  

I've burned the troubled recording without the sound dropping out, and without needing to run FFMPEG to re-encode. :)  Hopefully that is the last of it.  As a side benefit, not having to run FFMPEG and reencoding the whole recording speeds up the whole process.

---

