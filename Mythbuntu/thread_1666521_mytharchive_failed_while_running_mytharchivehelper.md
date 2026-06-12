---
title: "mytharchive failed while running mytharchivehelper"
date: 2011-01-13
forum: Mythbuntu
---

### Post by kaare jensen on 2011-01-13
I am running a combined frontend/backend Mythtv-box with Mythbunto 10.10 and MythTv 0.24 upgraded from 9.10/0.22.

When I run mytharchive to write a DVD everything seems to work fine until ffmpeg has written newfile2.mpg then mytharchivehelper fails apparently while getting stream informaion from newfile2.mpg. I have pasted the progress log below.

I saw some other posts hinting that this could be due to missing privileges so I removed everything from mytharchive/temp and chmod 777 on temp but this does not change anything - same error.

I have a regular user and a mythtv user on my Myth-box and the regular user is automatically logged in at boot. The backend is running as the mythtv user but the frontend is running as the regular user. Is that as intended or should the frontend also be running as the mythtv user? Could that be the issue if my problem is related to file permissions?

Any help is highly appreciated !

Kind regards,
Kaare


===============================
Progress log:
2011-01-11 23:36:59 mythburn.py (0.1.20101206-1) starting up...
2011-01-11 23:37:01 Found 4 CPUs
2011-01-11 23:37:01 Obtaining MythTV settings from MySQL database for hostname htpc
2011-01-11 23:37:01 temppath: /home/mythtv/mytharchive/temp/work
2011-01-11 23:37:01 logpath:  /home/mythtv/mytharchive/temp/logs
2011-01-11 23:37:01 Setting process priority to 17
2011-01-11 23:37:01 Processing Mythburn job number 1.
2011-01-11 23:37:01 Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 1
2011-01-11 23:37:01           savefilename = ''
2011-01-11 23:37:01 Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter/theme.xml
2011-01-11 23:37:01 Loading font 0, /usr/share/mythtv/fonts/FreeSans.ttf size 22
2011-01-11 23:37:01 Loading font 1, /usr/share/mythtv/fonts/FreeSans.ttf size 18
2011-01-11 23:37:01 Loading font 2, /usr/share/mythtv/fonts/FreeSans.ttf size 16
2011-01-11 23:37:01 wantIntro: 1, wantMainMenu: 1, wantChapterMenu:1, wantDetailsPage: 0
2011-01-11 23:37:01 Final DVD Video format will be pal
2011-01-11 23:37:01 There are 1 files to process
2011-01-11 23:37:01 Pre-processing video 1: '/home/mythtv/video/ruth/dvd/1002_20100416101000_part1.mpg'
2011-01-11 23:37:02           1002 20100416101000 part1
2011-01-11 23:37:02 Video resolution is 704 by 576
2011-01-11 23:37:02 *************************************************************
2011-01-11 23:37:02 Processing video 1: '/home/mythtv/video/ruth/dvd/1002_20100416101000_part1.mpg'
2011-01-11 23:37:02 *************************************************************
2011-01-11 23:37:02 File type is 'mpeg'
2011-01-11 23:37:02 Video codec is 'mpeg2video'
2011-01-11 23:37:02 File will be re-encoded using profile LP
2011-01-11 23:37:02 File will be re-encoded using profile LP
2011-01-11 23:37:03 Preferred audio languages dan and eng
2011-01-11 23:37:03 Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2011-01-11 23:37:03 Aspect ratio is 16:9
2011-01-11 23:37:03 Re-encoding audio and video
2011-01-11 23:37:03 Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_pal.xml
2011-01-11 23:37:03 Encoding profile (LP) found
2011-01-11 23:37:03 ffmpeg -threads 4 -v 1 -i "/home/mythtv/video/ruth/dvd/1002_20100416101000_part1.mpg" -r pal -target dvd -b 2344k -s 352x576 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 16:9 "/home/mythtv/mytharchive/temp/work/1/newfile2.mpg" -map 0:0 -map 0:1 
2011-01-12 02:00:53 ************************************************************
2011-01-12 02:00:53 ERROR: Failed while running mytharchivehelper to get stream information from "/home/mythtv/mytharchive/temp/work/1/newfile2.mpg"
2011-01-12 02:00:53 ************************************************************
2011-01-12 02:00:53 
2011-01-12 02:00:54 Terminated

---

### Post by ian dobson on 2011-01-14
Hi,

Maybe this thread might help [http://ubuntuforums.org/showthread.php?t=610856](http://ubuntuforums.org/showthread.php?t=610856)

Regards
Ian Dobson

---

### Post by kaare jensen on 2011-01-14
Thanks a lot for the pointer!

I did come across that thread in my search which is why I tried to set world permissions (777) on the mytharchive/temp folder. I could of course try to change ownership to the user that runs the frontend as suggested in the thread but I'd be surprised if that would make a difference.

Any comments as to who should run the mythfrontend? The user that is logged into the box or the mythtv user?

---

### Post by BicyclerBoy on 2011-01-14
The error could be because the ffmpeg file creation failed.
What's in the other log file in mytharchive logs folder ?
My mytharchive uses folders mytharchive/work/  ./logs/ ./config/

Try cutting & pasting the ffmpeg cmd out of the log file & executing it in terminal. This can be very revealing.

The command line options in mytharchive .xml files (IMHO) do not match up very well with the recent ffmpeg cmd line options.

Be aware that mytharchive calls external ffmpeg & this is practically unusable in stock std Ubuntu repos.

Myth0.24 builds mythffmpeg which should at least support most containers/codecs etc.

I understand MythTV runs as user mythtv (could be wrong) & permissions/group membership has to allow this.

---

### Post by kaare jensen on 2011-01-15
Thanks again for the reply!

It seems to me that ffmpeg writes the mytharchive/temp/work/1/newfile2.mpg file as it is supposed to. It takes a few hours to re-encode the file to LP and I can view the file fine in VLC (apart from the audio gradually getting out of sync).

The subsequent call to mytharchivehelper, however, is the command that fails. This could of course be due to some problem in the file that ffmpeg created but somehow I doubt it.

I order to get some debug info from mytharchivehelper I dumped the command string from mythburn.py and got the following:
```

mytharchivehelper -i "/home/mythtv/mytharchive/temp/work/1/newfile2.mpg" /home/mythtv/mytharchive/temp/work/1/streaminfo.xml 1

```When I run this from the terminal I get this on stdout:
```

Input #0, mpeg, from '/home/mythtv/mytharchive/temp/work/1/newfile2.mpg':
  Duration: 03:00:01.16, start: 0.500000, bitrate: 2609 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 352x576 [PAR 32:11 DAR 16:9], 9000 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
ICE default IO error handler doing an exit(), pid = 3283, errno = 32

```I wonder why this "ICE default IO error handler" is doing an exit. Could that be my problem?

The return value from mytharchivehelper is:
```

 2011-01-15 18:52:49.287 getFileInfo(): Opening '/home/mythtv/mytharchive/temp/work/1/newfile2.mpg'
2011-01-15 18:52:49.359 Calculating frame count
2011-01-15 18:54:23.810 frames = 270030
2011-01-15 18:54:23.810 duration = 10801
2011-01-15 18:54:23.810 Extracting details from: newfile2.mpg
2011-01-15 18:54:23.812 Cannot find details for newfile2.mpg
2011-01-15 18:54:23.814 File is not a MythTV recording.
2011-01-15 18:54:23.814 cutframes = 0
2011-01-15 18:54:23.814 cutduration = 0

```It is the return value that mythburn.py expects to be empty so it fails.

As mytharchivehelper says, it is not a MythTV recording so some details are obviously not found. And to some degree that is true, the recording is copied from the livetv folder and, I guess, by that detached from the data base. So am I missing something here: can mytharchive only use MythTV recordings??


If BicyclerBoy is correct that the mythtv user should be running the frontend I have some problem in the frontend startup scripts (whereever that is, haven't figured that out yet).

Can I persuade people to remotely login to their myth-box and check the user that runs the frontend? E.g. like:
```

ps auxww | grep mythfrontend.real | grep -v grep

```and check if it is the mythtv user or the your own user name at the beginning of the line.

Thanks!

---

### Post by kaare jensen on 2011-01-15
.

---

### Post by BicyclerBoy on 2011-01-15
Too clarify, I'm fairly sure the frontend GUI process runs as the logged in user but all the backend & script processes are mythtv.

I think it is a permissions problem.
Your MythTV users should be part of the mythtv group.

Things like mythfilldatabase run as user if invoked from terminal but  normally run as mythtv user; this confuses some peoples debugging.


Check the file ownership & permissions of the recordings & the mytharchive work area etc.
All my recordings & folders belong to mythtv (& RW) .
My mytharchive working folders & files belong to the main user, RW to all.

I use a modified ffmpeg_dvd_pal.xml for debugging my transcoding woes...
(mytharchive/mythburn.py searches for this xml file in the user home area first)

[HTML]   <profile>
        <name>SP</name>
        <description>A standard play profile giving approx. 2 hour of video on a single layer DVD</description>
        <bitrate>2096.63</bitrate>
        <passes>1</passes>
        <parameter name="-v"        value="1"/>
        <parameter name="-i"        value="%inputfile"/>
        <parameter name="-f"        value="dvd"/>
        <parameter name="-target"   value="pal-dvd"/>
        <parameter name="-b"        value="4771k"/>
        <parameter name="-s"        value="720x576"/>
        <parameter name="-flags"    value="ildct"/>
        <parameter name="-aspect"   value="%aspect"/>
        <parameter name="-mbd"      value="rd"/>
        <parameter name="-trellis"  value=""/>
        <parameter name="-mv0"      value=""/>
        <parameter name="-cmp"      value="0"/>
        <parameter name="-subcmp"   value="2"/>
        <parameter name="-acodec"   value="ac3"/>
        <parameter name="-ab"       value="192k"/>
        <parameter name="-ac"       value="2"/>
        <parameter name="-copyts"   value=""/>
        <parameter name="-ss"       value="00:01:00"/>
        <parameter name="-t"        value="00:00:30"/>
        <parameter name=""          value="%outputfile"/>
    </profile>[/HTML]

I have added the -ss & -t but I changed a lot of other stuff because it does not match up with later ffmpeg.

---

### Post by ian dobson on 2011-01-15
Hi,

Maybe try deleting the ~/.ICEauthority file, or atleast renaming it so something else.

I had an ICE default IO error some time back and deleteing the above file fixed it for me.

Regards
Ian Dobson

---

### Post by kaare jensen on 2011-01-16
Ok, my frontend startup is probably ok then, and it means that all processes started from the frontend (such as mythburn.py) is run by the frontend user and not the mythtv user. So I guess you are right that it could be a permission issue after all.

I tried to run the mytharchivehelper command above as mythtv user and it gave me the same output except from the ICE error. So I tried to remove the ~/.ICEauthority as ian suggested (had done that once before in my quest for a solution) and that removed the ICE error when I run mytharchivehelper from the terminal. However, when I run mytharchive from from MythTV I still get the same error that mytharchivehelper fails to get stream info.

I have checked the permissions on mytharchive:
drwxrwxrwx 3 mythtv mythtv     8 2011-01-16 14:12 mytharchive

Inside mytharchive all subfolders belong to the frontend user and all with 777 permission except mytharchive/temp/work/1 containing the newfile2.mpg. That folder has 755 and newfile2.mpg has 644. So could that be the issue? I mean, if some process owned by mythtv tries to modify newfile2.mpg that would definitely fail.

The mythburn.py process is at least owned by the frontend user so I don't really see how it could spawn a mythtv owned process?

My frontend user is a member of the mythtv group so that is not the problem either.

My livetv and video folders belong to mythtv and has 775 permissions. The recordings also melong to mythtv and some has 664 and some 644 permissions.

The file that I am trying create a DVD of has 444 but the temporary file mytharchive/temp/work/1/newfile2.mpg is written fine so I don't suppose that is the problem.

I tried to use the xml code BicyclerBoy posted and saved it as  ~/ffmpeg_dvd_pal.xml but mythburn.py did not seem to pick it up. Are  there other tricks needed?

Any suggestions are still very welcome :)

---

### Post by BicyclerBoy on 2011-01-16
The mythburn.py scripts (about line 520) checks 2  paths for xml profile.

1.   ~/.mythtv/MythArchive/
2.  default path where it is now..

This allows you to have custom profiles that do not get trashed with updates.

Note: my .xml profile is an attempt to get this working better with the latest ffmpeg.
And to reduce the cycle time for debugging.

---

### Post by kaare jensen on 2011-01-16
Great, thanks !

I had to copy the default file and add yours to the profile list. Unfortunately that did not reproduce the error, rather it gave me a nicely working 30 sec long (as expected) DVD.

So I copied the default LP profile and added only the -ss and -t options from your profile. Again a successful burned 30 sec long DVD.

I put in a log dump in mythburn.py in the function that gets the stream info (line 1929) and it turns out that the stream info is retrieved twice from the original mpg file and then once from the temporary file mytharchive/temp/work/1/newfile2.mpg created by ffmpeg. It is this latter one that fails. But apparently it only fails on the original length file, not the short one created with the -ss and -t ffmpeg options. Strange...

---

### Post by BicyclerBoy on 2011-01-16
My posted dvd ffmpeg profile was just a piece snipped out of the .xml.

Try increasing the length of transcoded file & monitor system memory..

Beware:
I'm finding recent ffmpeg is eating RAM at about 3MB/sec so it crashes after 40min.
Haven't got round to finding root cause..It may be my profile options.

Note: there are 2 bugs with the mythburn script in that it only works if the video stream is stream 0 , & it gets the audio stream indexes wrong.
The audio indexes is fixes itself because of iterative loops for preferred audio track.

---

### Post by kaare jensen on 2011-01-23
I tried to watch the memory consumption by ffmpeg but during the more than two hours of transcoding it stayed constantly at 158 MB so that does not seem to be the problem.

So in am attempt to get more info out of mytharchivehelper I hacked mythburn.py to use the subprocess class (instead of the older os.system) to spawn mytharchivehelper. This allows for capturing both the return code, stdout, and stderr.

The troubling call to mytharchivehelper is (I have added the -v all option in an attempt to get more info about the error but the extra info is minimal and not helpful):
```

mytharchivehelper -v all -i /home/mythtv/mytharchive/temp/work/1/newfile2.mpg /home/mythtv/mytharchive/temp/work/1/streaminfo.xml 1

```
that is, the input file is newly transcoded file by ffmpeg and the method (last parameter) is 1 meaning "read all frames (most accurate but slow)".

The return code from this call is 1 which is what makes mythburn.py terminate.

The stdout is:
```

2011-01-22 14:42:15.606 getFileInfo(): Opening '/home/mythtv/mytharchive/temp/work/1/newfile2.mpg'
2011-01-22 14:42:15.675 Calculating frame count
2011-01-22 14:43:55.851 frames = 270030
2011-01-22 14:43:55.851 duration = 10801
2011-01-22 14:43:55.851 Extracting details from: newfile2.mpg
2011-01-22 14:43:55.853 MSqlQuery::exec(DBManager0) SELECT chanid, starttime FROM recorded WHERE basename = 'newfile2.mpg
' <<<< Returns 0 row(s)
2011-01-22 14:43:55.853 Cannot find details for newfile2.mpg
2011-01-22 14:43:55.854 MSqlQuery::exec(DBManager0) SELECT chanid, starttime FROM recorded WHERE basename = 'newfile2.mpg' <<<< Returns 0 row(s)
2011-01-22 14:43:55.855 File is not a MythTV recording.
2011-01-22 14:43:55.855 cutframes = 0
2011-01-22 14:43:55.855 cutduration = 0

```

and the stderr is:
```

Input #0, mpeg, from '/home/mythtv/mytharchive/temp/work/1/newfile2.mpg':
  Duration: 03:00:01.16, start: 0.500000, bitrate: 2609 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 352x576 [PAR 32:11 DAR 16:9], 9000 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
ICE default IO error handler doing an exit(), pid = 2896, errno = 32

```

Everything here basically looks fine (and both video and audio is stream #0 as required like BicyclerBoy mentioned) except from the ICE error. And if I launch the same command outside mythburn.py everything is the same except from the ICE error.

I have tried to remove the ~/.ICEauthority (which get re-written at reboot) and changing permissions to 666 but that doesn't help. 

A mutual launch of "ps auxww" shows that "pid = 2896" really is the mytharchivehelper process that ICE is complaining about.

The ICE "errno = 32" is supposedly a broken pipe.

This ticket [http://code.mythtv.org/trac/ticket/6236](http://code.mythtv.org/trac/ticket/6236) talks about dropped frames from ffmepg making the video and audio streams of different lengths. Could that possibly be my problem?

On the other hand it seems strange that this does not happen outsidde mythburn.py??

Does anybody know how to get more info out of mytharchivehelper (other than the -v all option)?

---

### Post by BicyclerBoy on 2011-01-24
Still looks like permissions problems ..

Can you run any other database scripts okay ?
Do you use EPG scrapping scripts from web xml EPG listings ? 
Maybe try mythfilldatabase from terminal.

---

### Post by kaare jensen on 2011-01-24
I can run mythfilldatabase fine with no errors. The mythbackend is set up to use EIT which have worked fine out-of-the-box so I do no manual EPG stuff.

Are there other database scripts I can try?

---

### Post by BicyclerBoy on 2011-01-24
I meant run mythfilldatabase manually from a terminal.
This was a common problem for people with a user <>mythtv.

I think there are other frontend job scripts. Best to see mythtv wiki.

AFAIK all mythtv apps can be called with -v n  where n is the verbose level.
Try -v help.
Look in mythverbose.cpp & .h to see if this makes sense.

Can browse the code on-line with full hyperlinked navigation etc.

---

### Post by kaare jensen on 2011-01-24
Yes, I did run mythfilldatabase from the terminal. I am sorry I wasn't clear on that.

I tried to run mythavtest with no apparent problems but I am not sure if that tells me anything.

mytharchivehelper has a "-v all" option for verbose output but that did not reveal anything.

It would be nice to figure out what exactly makes mytharchivehelper fail but unfortunately it is a binary so I need to figure out how to obtain the sources and compile it. Any help in that is highly appreciated.

Other than that I am running out of ideas...

---

### Post by BicyclerBoy on 2011-01-25
You check out the source code using git for Mythtv 0.24 onwards.

The old SVN maybe still available for 0.23+fixes (completely halted).

See mythtv website for details & compiling how to.
It is not that hard..

Key points I recall relate to MythTV 0.23 ./configure options:
set the install path to match Ubuntu.
  ./configure --prefix=/usr --enable-gpl --enable-version3 --enable-nonfree --enable-libfaad --disable-backend

This config example is for 0.23 frontend only. libfaad used for latm_aac decode.

---

### Post by kaare jensen on 2011-01-25
Great, thanks!

I will try my luck and write back if I find anything useful.

---

### Post by baekgaard on 2011-04-23
> **kaare jensen said:**
> I will try my luck and write back if I find anything useful.

Kaare, did you ever get this solved? 

I'm running into a similar problem here with 0.24. However, I can run mytharchivehelper in a ssh window and from there I do not get the ICE error, and instead gets the expected 0 return status... so maybe it has indeed something to do with the .ICEauthority file after all?


-- Per.

---

### Post by baekgaard on 2011-04-25
> **baekgaard said:**
> 
I'm running into a similar problem here with 0.24. However, I can run mytharchivehelper in a ssh window and from there I do not get the ICE error, and instead gets the expected 0 return status... so maybe it has indeed something to do with the .ICEauthority file after all?

Just for the record: I implemented the work-around suggested in the threads linked above ([http://ubuntuforums.org/showpost.php?p=9211587&postcount=30](http://ubuntuforums.org/showpost.php?p=9211587&postcount=30)), so that mytharchivehelper in reality moves the .ICEauthority file out of the way first, calls the mytharchivehelper.real (copy of original binary) and then puts the .ICEauthority file back in place again.

Seems to work so far, and was only required for the mytharchivehelper program in my case.


-- Per.

---

