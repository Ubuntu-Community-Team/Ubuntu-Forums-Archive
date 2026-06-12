---
title: "[SOLVED] mytharchive/mythtranscode failing - mythbuntu weekly builds"
date: 2007-11-12
forum: Mythbuntu
---

### Post by bigtdp on 2007-11-12
I'm having problems with Mytharchive when trying to archive a recording I have made from DVB-T (Freeview)

The recording is less than 4.3GB, so I just use the edit function to create a cutlist to remove the parts before and after the prog I wish to archive, then choose "Don't Re-encode"... 

the log viewer (and logfile) show:

```
2007-11-12 17:08:22 mythburn.py (0.1.20070826-5) starting up...
2007-11-12 17:08:22 Found 2 CPUs
2007-11-12 17:08:22 Obtaining MythTV settings from MySQL database for hostname msu-mythtv2a
2007-11-12 17:08:22 temppath: /var/lib/mythtv/mytharchive/work
2007-11-12 17:08:22 logpath:  /var/lib/mythtv/mytharchive/logs
2007-11-12 17:08:22 Setting process priority to 17
2007-11-12 17:08:22 Processing Mythburn job number 1.
2007-11-12 17:08:22 Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 0
2007-11-12 17:08:22           savefilename = ''
2007-11-12 17:08:22 Looking for: /usr/share/mythtv/mytharchive/themes/Simple - Autoplay/theme.xml
2007-11-12 17:08:22 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2007-11-12 17:08:22 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2007-11-12 17:08:22 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2007-11-12 17:08:22 wantIntro: 0, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 0
2007-11-12 17:08:22 Final DVD Video format will be pal
2007-11-12 17:08:22 There are 1 files to process
2007-11-12 17:08:24 Pre-processing file '/var/lib/mythtv/recordings/1001_20071108000300.mpg' of type 'recording'
2007-11-12 17:08:25 streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="1101" duration="1820" filename="/var/lib/mythtv/recordings/1001_20071108000300.mpg" type="mpegts">
        <streams count="10">
                <video aspectratio="1.77778" bitrate="15000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="600" start_time="6631.500520" streamindex="0" width="720"/>
                <audio bitrate="256000" channels="2" codec="mp2" ffmpegindex="1" id="601" language="eng" samplerate="48000" start_time="6631.468527" streamindex="1"/>
                <audio bitrate="0" channels="0" codec="mp3" ffmpegindex="2" id="602" language="eng" samplerate="0" start_time="6631.468527" streamindex="2"/> 
                <subtitle codec="dvbsub" ffmpegindex="3" streamindex="3"/>
                <data codec="Data: 0x0000" streamindex="4"/>
                <data codec="Data: 0x0000" streamindex="5"/>
                <data codec="Data: 0x0000" streamindex="6"/>
                <data codec="Data: 0x0000" streamindex="7"/>
                <data codec="Data: 0x0000" streamindex="8"/>
                <data codec="Data: 0x0000" streamindex="9"/>
        </streams>
</file>
2007-11-12 17:08:25           Talk of Angels
2007-11-12 17:08:25 Video resolution is 720 by 576
2007-11-12 17:08:25 *************************************************************
2007-11-12 17:08:25 Processing file /var/lib/mythtv/recordings/1001_20071108000300.mpg of type recording
2007-11-12 17:08:25 *************************************************************
2007-11-12 17:08:25 File type is 'mpegts'
2007-11-12 17:08:25 Video codec is 'mpeg2video'
2007-11-12 17:08:25 File has a cut list - running mythtrancode to remove unwanted segments
2007-11-12 17:13:14 Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 1, Command was mythtranscode --mpeg2 --honorcutlist -c 1001 -s 2007-11-08T00:03:00 -o /var/lib/mythtv/mytharchive/work/1/tmp
2008-11-12 17:13:14 Failed to run mythtranscode to remove unwanted segments
2007-11-12 17:14:18 ************************************************************
2007-11-12 17:14:18 ERROR: Failed while running mytharchivehelper to get stream information from "/var/lib/mythtv/recordings/1001_20071108000300.mpg"
2007-11-12 17:14:18 ************************************************************
2007-11-12 17:14:18
2007-11-12 17:14:18 Terminated

```

any ideas? sometimes I've seen it go further, but mythtranscode fails pretty much every time... I've just done another test with 2x kids cartoons to be burnt onto one disc - the first one went through fine, using the cutlist, but the 2nd prog didn't!!

help!

does anyone know when the weekly builds are released? is it worth me waiting to see if the problem is fixed in the next build? in the mythbuntu trunk weekly builds is mytharchive/mythtranscode working correctly for anyone else? is the mythbuntu 0.20-fixes build working, so would i be better off with that? I really need the ability to save mythtv recordings in more than one location, and this doesn't appear in older versions.......

once again - help! - thanks in advance if you can :)

xTx

---

### Post by bigtdp on 2007-11-13
I've just done a clean install of Mythbuntu 7.10, and this time used the weekly fixes... I imported the recording that I want to burn, and get pretty much exactly the same error... 

is anyone actually successfully burning their recordings to DVD?

xTx

---

### Post by Meph1st0 on 2007-11-13
I've been having this problem myself.  I had thought that it had something to do with folder permissions to the mytharchive temp folder but I've tried creating the temp folder in /home/username/mytharchive/temp or /var/lib/mythtv/temp or even /var/lib/mythtv/recordings/temp and none of them worked.

Strangely, when I set the folder to /var/lib/mythtv/recordings/temp it actually successfully burned a recording once but none of my attempts worked thereafter.  I'm getting the exact same error message you are.

My next idea was to uninstall mytharchive from the MCC and then reinstall it.  I'm all out of ideas otherwise.

Here's the post I made a while back.  I put the project on hold since my last post.  [http://ubuntuforums.org/showthread.php?t=598792](http://ubuntuforums.org/showthread.php?t=598792)

---

### Post by bigtdp on 2007-11-14
yeah, mythtv definitely has write access to the temp folder... 

I can successfully burn recordings, but the cut list is the problem for me... I've just successfully run the command manually on the same file it fails on through mytharchive, and it works fine... the command was: ```
 mythtranscode --mpeg2 --honorcutlist -c 1029 -s 2007-11-13T21:00:00 -v all,nodatabase -o /mnt/store/work//work/1/tmp
```

I added in -v all,nodatabase so I could see detailed logs of what fails, but of course it didn't fail :(

I haven't managed to find anyone that this works for yet :(

xTx

---

### Post by Meph1st0 on 2007-11-14
Oh, well it looks like you know more about this than I do.  Where did you end up putting your temp folder?

Do you know what this error message means?

2007-11-12 17:14:18 ERROR: Failed while running mytharchivehelper to get stream information from "/var/lib/mythtv/recordings/1001_20071108000300.mpg"

It's the same one I'm getting that appears in your code snipet.

---

### Post by bigtdp on 2007-11-14
> **Meph1st0 said:**
> Oh, well it looks like you know more about this than I do.  Where did you end up putting your temp folder?

Do you know what this error message means?

2007-11-12 17:14:18 ERROR: Failed while running mytharchivehelper to get stream information from "/var/lib/mythtv/recordings/1001_20071108000300.mpg"

It's the same one I'm getting that appears in your code snipet.

that error is apparently something to do with permissions - I don't seem to get that one now, as I've created a new directory for all my mythtv stuff, /mnt/store/ - I changed the ownership to the user that runs mythfrontend and gave the user read, write and delete properties...

```
chown -hR <user:group> /mnt/store/ 
``` 

changes who owns the directory and anything in that directory, then:

```
 chmod -R 777 /mnt/store/ 
```

changes the properties of the directory, and anything in that directory to full read/write/delete...

I dunno if that'll help you...

the errors I'm NOW getting are relating to just the cutlist:

```
2007-11-14 10:05:48 mythburn.py (0.1.20070428-1.fixes) starting up...
2007-11-14 10:05:48 Found 2 CPUs
2007-11-14 10:05:48 Obtaining MythTV settings from MySQL database for hostname msu-mythtv2
2007-11-14 10:05:48 temppath: /mnt/store/work//work
2007-11-14 10:05:48 logpath:  /mnt/store/work//logs
2007-11-14 10:05:48 Processing Mythburn job number 1.
2007-11-14 10:05:48 Options - mediatype = 0, doburn = 0, createiso = 1, erasedvdrw = 0
2007-11-14 10:05:48           savefilename = ''
2007-11-14 10:05:48 Looking for: /usr/share/mythtv/mytharchive/themes/Compact/theme.xml
2007-11-14 10:05:48 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2007-11-14 10:05:48 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2007-11-14 10:05:48 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2007-11-14 10:05:48 wantIntro: 1, wantMainMenu: 1, wantChapterMenu:0, wantDetailsPage: 0
2007-11-14 10:05:48 Final DVD Video format will be pal
2007-11-14 10:05:54 There are 1 files to process
2007-11-14 10:06:12 Pre-processing file '1029_20071113210000.mpg' of type 'recording'
2007-11-14 10:06:13 streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file duration="2899" filename="/var/lib/mythtv/recordings/1029_20071113210000.mpg" type="mpegts">
        <streams count="8">
                <video aspectratio="1.77778" bitrate="10000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="570" start_time="298.33304" streamindex="0" width="544"/>
                <audio bitrate="192000" channels="2" codec="mp2" ffmpegindex="1" id="571" language="eng" samplerate="48000" start_time="297.984117" streamindex="1"/>
                <audio bitrate="64000" channels="1" codec="mp2" ffmpegindex="2" id="572" language="eng" samplerate="48000" start_time="297.984991" streamindex="2"/>
                <subtitle codec="dvbsub" ffmpegindex="3" streamindex="3"/>
                <data codec="Data: 0x0000" streamindex="4"/>
                <data codec="Data: 0x0000" streamindex="5"/>
                <data codec="Data: 0x0000" streamindex="6"/>
                <data codec="Data: 0x0000" streamindex="7"/>
        </streams>
</file>
2007-11-14 10:06:13           Sleepy Hollow
2007-11-14 10:06:13 Video resolution is 544 by 576
2007-11-14 10:06:13 *************************************************************
2007-11-14 10:06:13 Processing file 1029_20071113210000.mpg of type recording
2007-11-14 10:06:13 *************************************************************
2007-11-14 10:06:13 File type is 'mpegts'
2007-11-14 10:06:13 Video codec is 'mpeg2video'
2007-11-14 10:06:13 File has a cut list - running mythtrancode to remove unwanted segments
2007-11-14 10:07:57 Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 256, Command was mythtranscode --mpeg2 --honorcutlist -c 1029 -s 2007-11-13T21:00:00 -o /mnt/store/work//work/1/tmp
2007-11-14 10:07:57 Failed to run mythtranscode to remove unwanted segments
2007-11-14 10:07:57 WARNING: File does not have a DVD compliant resolution but you have selected not to re-encode the file
2007-11-14 10:08:41 streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file duration="7194" filename="/var/lib/mythtv/recordings/1029_20071113210000.mpg" type="mpegts">
        <streams count="8">
                <video aspectratio="1.77778" bitrate="10000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="570" start_time="298.33304" streamindex="0" width="544"/>
                <audio bitrate="192000" channels="2" codec="mp2" ffmpegindex="1" id="571" language="eng" samplerate="48000" start_time="297.984117" streamindex="1"/>
                <audio bitrate="64000" channels="1" codec="mp2" ffmpegindex="2" id="572" language="eng" samplerate="48000" start_time="297.984991" streamindex="2"/>
                <subtitle codec="dvbsub" ffmpegindex="3" streamindex="3"/>
                <data codec="Data: 0x0000" streamindex="4"/>
                <data codec="Data: 0x0000" streamindex="5"/>
                <data codec="Data: 0x0000" streamindex="6"/>
                <data codec="Data: 0x0000" streamindex="7"/>
        </streams>
</file>
2007-11-14 10:08:41 Preferred audio languages eng and eng
2007-11-14 10:08:41 Video id: 0x23a, Audio1: [1] 0x23b (MP2, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
2007-11-14 10:08:41 Splitting MPEG stream into audio and video parts
2007-11-14 10:08:41 Running: mythreplex --demux --fix_sync -t TS -o /mnt/store/work//work/1/stream -v 570 -a 571 "/var/lib/mythtv/recordings/1029_20071113210000.mpg"
2007-11-14 10:10:43 Audio track 1 is in mp2 format - NOT re-encoding to ac3
2007-11-14 10:10:43 *************************************************************
2007-11-14 10:10:43 Finished processing file 1029_20071113210000.mpg
2007-11-14 10:10:43 *************************************************************
2007-11-14 10:10:43 Menu items per page 6
2007-11-14 10:10:43 Background image file is /usr/share/mythtv/mytharchive/themes/Compact/Compact-Background.png
2007-11-14 10:10:43 Music is menumusic.ac3, length is 15 seconds
2007-11-14 10:10:43 Creating DVD menus
2007-11-14 10:10:43 Menu page 1
2007-11-14 10:10:46 Encoding Menu Page 1 using aspect ratio '16:9'
2007-11-14 10:11:00 Menu items per page 6
2007-11-14 10:11:00 Creating DVD XML file for dvd author
2007-11-14 10:11:00 Menu page 1
2007-11-14 10:11:00 aspect ratio is: 1.77778
2007-11-14 10:11:00 aspect ratio is: 1.77778
2007-11-14 10:11:00 Total size of video files, before multiplexing, is 1559 Mbytes, audio is 164 MBytes, menus are 1 MBytes.
2007-11-14 10:11:00 Video will fit onto DVD. 2680.05 MBytes of space remaining on recordable DVD.
2007-11-14 10:11:00 Multiplexing MPEG stream to /mnt/store/work//work/1/final.mpg
2007-11-14 10:11:00 Adding sync offset of 348ms
2007-11-14 10:11:00 Available streams - video and one audio stream
2007-11-14 10:11:00 Multiplex started PID=8748
2007-11-14 10:11:00 Starting dvdauthor
2007-11-14 10:13:05 Finished  dvdauthor
2007-11-14 10:13:05 Creating ISO image
2007-11-14 10:14:30 Finished creating ISO image
2007-11-14 10:14:30 Finished processing jobs!!!

```

so now I've got mytharchive to create an image, but this section shows the error when mythtranscode fails to use the cutlist to remove the ads etc:

```
2007-11-14 10:06:13 File has a cut list - running mythtrancode to remove unwanted segments
2007-11-14 10:07:57 Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 256, Command was mythtranscode --mpeg2 --honorcutlist -c 1029 -s 2007-11-13T21:00:00 -o /mnt/store/work//work/1/tmp
2007-11-14 10:07:57 Failed to run mythtranscode to remove unwanted segments

```

surely there must be someone out there using Mythtv that has resolved these problems?!?! :confused:

xTx

---

### Post by bigtdp on 2007-11-14
ok, now I've changed mythburn.py so whilst mythtranscode is running it outputs verbose messages into a logfile... I was expecting to get some sort of error message around the time that progress.log said mythtranscode has failed - but all I get is a message telling me that mythtranscode has completed! no errors or anything...

from progress.log:

```
2007-11-14 17:11:49 Processing file 1029_20071113210000.mpg of type recording
2007-11-14 17:11:49 *************************************************************
2007-11-14 17:11:49 File type is 'mpegts'
2007-11-14 17:11:49 Video codec is 'mpeg2video'
2007-11-14 17:11:49 File has a cut list - running mythtrancode to remove unwanted segments
2007-11-14 17:14:31 Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 256, Command was mythtranscode --mpeg2 --honorcutlist -c 1029 -s 2007-11-13T21:00:00 -o /mnt/store/work//work/1/tmp -v all >> /home/msu/transcode.log
2007-11-14 17:14:31 Failed to run mythtranscode to remove unwanted segments

```

from the verbose output of mythtranscode:
```
2007-11-14 17:14:19.914 VID: P #:5 nb: 2 pts: 01:37:00.038 dts: 01:36:59.958 pos: 3076145864
2007-11-14 17:14:19.914 Id:0 01:37:00.038 V:145 EXT: 82 91
2007-11-14 17:14:19.914 VID: B #:3 nb: 2 pts: 01:36:59.998 dts: 01:36:59.998 pos: 3076161844
2007-11-14 17:14:19.914 Id:0 01:36:59.998 V:144 EXT: 82 91
2007-11-14 17:14:19.914 VID: I #:6 nb: 2 pts: 01:37:00.078 dts: 01:37:00.038 pos: 3076145864
2007-11-14 17:14:19.915 Id:0 01:37:00.078 V:143 EXT: 82 91
2007-11-14 17:14:19.934 Generating Keyframe Index
2007-11-14 17:14:19.934 Opening /mnt/store/work//work/1/tmp
2007-11-14 17:14:19.981 Input #0, mpeg, from '/mnt/store/work//work/1/tmp':
2007-11-14 17:14:19.981   Duration: N/A, bitrate: N/A
2007-11-14 17:14:19.981   Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 544x576, 10000 kb/s, 25.00 fps(r)
2007-11-14 17:14:19.982   Stream #0.1[0x1c1]: Audio: mp2, 48000 Hz, mono, 64 kb/s
2007-11-14 17:14:31.208 Transcode Completed
2007-11-14 17:14:31.234 Transcoding /var/lib/mythtv/recordings/1029_20071113210000.mpg done
2007-11-14 17:14:31.235 SSDPCache - Destructor
2007-11-14 17:14:31.235 UPnpDeviceDesc - Destructor

```

I have the full logs, if anyone's out there?!? :-k

xTx

---

### Post by Meph1st0 on 2007-11-14
Thanks for explaining to me how to take care of permissions, I really appreciate it.  Your problem with the cutlist is clearly beyond my skill level.  I hope someone will be able to help you out.

---

### Post by bigtdp on 2007-11-15
> **Meph1st0 said:**
> Thanks for explaining to me how to take care of permissions, I really appreciate it.  Your problem with the cutlist is clearly beyond my skill level.  I hope someone will be able to help you out.

no worries - I'm still only an ubuntu/linux n00b and find it really annoying when someone says: "change permissions" without them saying how! I dunno if the way I've said to do it is the "right" way, but it definitely did the job for me :)

xTx

---

### Post by bigtdp on 2007-11-15
I have solved the mythtranscode problem!!! \\:D/

[http://www.mythtvtalk.com/forum/viewtopic.php?p=19018#19018](http://www.mythtvtalk.com/forum/viewtopic.php?p=19018#19018)

basically, you just need to remove the ".ICEauthority" file that is in the mythtv users' home directory:

```
rm /home/<username>/.ICEauthority
```

I'm hoping that this hasn't killed anything else ;-) but I'm now able to burn dvds using mytharchive that has ads cut out - YAY! :-D

xTx

---

### Post by bigtdp on 2007-11-15
ok, the .ICEauthority file is definitely the problem - when you reboot, the file is created again in the users' home directory, and mythtranscode fails... deleted the file again and mythtranscode works fine...

right, so now I just need to find out what the file is, what creates it, and how to stop it from being created! 

easy.......

;-)

xTx

---

### Post by bigtdp on 2007-11-15
from google searches, it appears the file ".ICEauthority" causes lots of problems... it's created during bootup, probably by something running a KDE app as root or sudo... anyways, I think I'm ok to delete it, so I've added a line to my Mythbuntu's mythfrontend startup script to remove it everytime the PC is booted... 

NB: you don't have to use 'vi', you can replace that with 'nano' or 'gedit' or your own fave text editor:

```
sudo vi /usr/share/mythtv/mythfrontend.sh
```
then add the following lines (I've put them near the top of the file and it works):

```
# deletes .ICEauthority which makes mytharchive NOT honour cutlist
rm /home/<user>/.ICEauthority

```
now, I'm not sure if this is the right way to go about things (I'm fairly sure it isn't!!) but it does the job for me... if anyone has any better ideas, please let me know!

I hope this is of some use to others that have this issue, as there seems to be a few peeps out there with the problem, and virtually nothing on how to fix it...

xTx

---

### Post by Meph1st0 on 2007-11-20
bigtdp,

I hadn't noticed before but I too was having the same .ICEauthority error message in my logs.  I wasn't even trying to use cut lists, I just wanted to burn a recording but it was failing.  I deleted the .ICEauthority like you recommended and it worked!!!

I've now followed your instructions on adding it to the mythfrontend.sh file.  I've burned several recordings now.  I'm a happy camper.  Thanks again for this thread.

---

### Post by bigtdp on 2007-11-21
> **Meph1st0 said:**
> bigtdp,

I hadn't noticed before but I too was having the same .ICEauthority error message in my logs.  I wasn't even trying to use cut lists, I just wanted to burn a recording but it was failing.  I deleted the .ICEauthority like you recommended and it worked!!!

I've now followed your instructions on adding it to the mythfrontend.sh file.  I've burned several recordings now.  I'm a happy camper.  Thanks again for this thread.

no probs - glad it works for you too :)

If you upgrade packages, you will probably need to re-enter the "rm /home/<user>/.ICEauthority" bit in the /usr/share/mythtv/mythfrontend.sh script, as I found out earlier this week ;-)

xTx

---

### Post by ahood on 2007-12-10
Thank you. This suggestion removes the .ICEauthority file.

[I]Note: System would not boot if the rm statement was added below the  main part of the script. I added the rm statement immediately below the scripts author name.
[/I]

---

### Post by wyliecoyoteuk on 2008-07-13
The .ICE authority file is something to do with remote logins. and yes it cures the transcode failure, not sure why...

---

### Post by agamotto on 2008-07-17
> **wyliecoyoteuk said:**
> The .ICE authority file is something to do with remote logins. and yes it cures the transcode failure, not sure why...

I just upgraded frfom 7.10 to 8.04.1, and have not been able to burn DVDs, just as I couldn't with the first 8.04 releases.  I am going to try the .ICEauthority removal tip and see if that clears things up.

---

### Post by entourage on 2008-12-06
FYI, I upgraded from 8.04.1 to 8.10 and got this message when trying to burn a DVD.  These directions fixed my problem!!  Thanks!

---

### Post by bigtdp on 2008-12-06
> **entourage said:**
> FYI, I upgraded from 8.04.1 to 8.10 and got this message when trying to burn a DVD.  These directions fixed my problem!!  Thanks!

glad this is still helping peeps! :D

xTx

---

### Post by matthewgeier on 2009-01-04
> **bigtdp said:**
> glad this is still helping peeps! :D

xTx

 Actually what ticks me off, is this IS STILL NEEDED two years later. I've gone through 3 upgrade cycles on my Ubuntu/MythTV box - and I STILL have to log in on an alternate console and remove the .ICEauthority file if I want to make a DVD of a recording.
 Why hasn't the bug been fixed ?
 Why does mythtrancode even care what's in about the ICEauth file ?. It doesn't have a GUI!.

---

### Post by agamotto on 2009-01-05
I personally gave up on burning DVDs some time ago due to these issues, but now that I have 'upgraded' to 8.10, I might try your ICEauthority trick and see if anything happens.

---

### Post by bazzawill on 2009-04-22
I have been using this hack for some time I just now released how ever this is causing an issue when I try to quit xfce it seems the xfce-session-logout (called by xfce quit) requires .ICEauthority otherwise it does nothing.

---

### Post by racmar on 2009-06-16
Thanks for the FIX!  In the spirit of helping out, I hacked a quick solution to this problem.  However, any Ubuntu updates to mythtv will probably break this; thus YMMV.

```
sudo mv /usr/bin/mythtranscode /usr/bin/mythtranscode.real
sudo nano /usr/bin/mythtranscode

```

and paste the following code:
```
#! /bin/bash

# renames .ICEauthority to .ICEauthority.mythtranscode
mv /home/`whoami`/.ICEauthority /home/`whoami`/.ICEauthority.mythtranscode

# run the original mythtranscode + args
echo "Running: /usr/bin/mythtranscode.real $@"
/usr/bin/mythtranscode.real $@

# renames .ICEauthority back to the original
mv /home/`whoami`/.ICEauthority.mythtranscode /home/`whoami`/.ICEauthority

```

Save the file ( CTL+X ), then make it executable:
```
sudo chmod +x /usr/bin/mythtranscode
```


This will temporarily rename the .ICEauthority file before starting mythtranscode and then rename it back after mythtranscode finishes.  I changed the old <<your mythtv username>> to the `whoami` command.  If this does not work for you, use your actual mythtv user account above.

---

### Post by bcg30506 on 2009-07-27
I'm still getting this error and the ICEauthority trick did not work for me, nor did a reboot.  It seems to be just some files.  I've tried re-transcoding them losslessly which used to get around this but not now.  I used to be able to burn DVDs with no problem.  Anyone have ideas?
```

...
2009-07-27 18:40:26 Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2009-07-27 18:40:26 Audio track 1 is in mp2 format - re-encoding to ac3
2009-07-27 18:40:26 Encoding audio to ac3
2009-07-27 18:40:56 *************************************************************
2009-07-27 18:40:56 Finished processing file '/monolith/tv/3147_20090612182900.mpg'
2009-07-27 18:40:56 *************************************************************
2009-07-27 18:40:56 *************************************************************
2009-07-27 18:40:56 Processing recording 2: '/monolith/tv/3147_20090620205900.mpg'
2009-07-27 18:40:56 *************************************************************
2009-07-27 18:42:21 ************************************************************
2009-07-27 18:42:21 ERROR: Failed while running mytharchivehelper to get stream information from "/monolith/tv/3147_20090620205900.mpg"
2009-07-27 18:42:21 ************************************************************
2009-07-27 18:42:21 
2009-07-27 18:42:22 Terminated

```

```

size=   39963kB time=1705.09 bitrate= 192.0kbits/s    
video:0kB audio:39963kB global headers:0kB muxing overhead 0.000000%
*************************************************************
Finished processing file '/monolith/tv/3147_20090612182900.mpg'
*************************************************************
*************************************************************
Processing recording 2: '/monolith/tv/3147_20090620205900.mpg'
*************************************************************
2009-07-27 18:40:57.630 Opening /monolith/tv/3147_20090620205900.mpg
Input #0, mpeg, from '/monolith/tv/3147_20090620205900.mpg':
  Duration: 01:29:58.6, start: 0.312411, bitrate: 4960 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
2009-07-27 18:40:57.651 Calculating frame count
2009-07-27 18:42:21.488 frames = 161797
2009-07-27 18:42:21.527 duration = 5398
2009-07-27 18:42:21.546 Extracting details from: 3147_20090620205900.mpg
2009-07-27 18:42:21.564 chanid: 3147 starttime:2009-06-20T20:59:00 
2009-07-27 18:42:21.628 File is a Myth recording.
2009-07-27 18:42:21.638 cutframes = 0
2009-07-27 18:42:21.638 cutduration = 0
ICE default IO error handler doing an exit(), pid = 4430, errno = 32
************************************************************
ERROR: Failed while running mytharchivehelper to get stream information from "/monolith/tv/3147_20090620205900.mpg"
************************************************************

chmod: changing permissions of `/monolith/tmp/mythexport': Operation not permitted
Terminated

```

---

### Post by bcg30506 on 2009-07-29
I think I got my issue fixed.  It only happened on some runs with certain recordings, but was related to the same issue with the ~/.ICEauthority file.

I had to do the same "fix" from above for mytharchivehelper.

---

### Post by bewsher on 2009-09-02
Hi!
 
I've used racmar's fix on mythtranscode (and mythwelcome and mytharchivehelper) and it's fixed the problems with mythtranscode failing. THANKS :D
 
I've added some extra lines to the code so that if mythtranscode fails it will pass on the error code. The code I used is below.
 
> **racmar said:**
> ... However, any Ubuntu updates to mythtv will probably break this; thus YMMV.
 
Because of this, I also put the wrapper scripts in /usr/share/mythtv/ and ended them with .sh
For example /usr/share/mythtv/mythtranscode.sh
 
I then made a symbolic link to this script in the original location.
 
This way, when Ubuntu updates mythtv, it will only break the symlinks. It will still break, but it will be easier to fix.
 
So the process I used is: 
```
sudo nano /usr/share/mythtv/mythtranscode.sh

```
 
and paste the following code:
```
#! /bin/bash
 
# renames .ICEauthority to .ICEauthority.mythtranscode
mv /home/`whoami`/.ICEauthority /home/`whoami`/.ICEauthority.mythtranscode
 
# run the original mythtranscode + args
echo "Running: /usr/bin/mythtranscode.real $@"
/usr/bin/mythtranscode.real $@
errorval=$?
 
# renames .ICEauthority back to the original
mv /home/`whoami`/.ICEauthority.mythtranscode /home/`whoami`/.ICEauthority
 
exit $errorval

```
 
Save the file ( CTL+X ), then make it executable:
```
sudo chmod +x /usr/share/mythtv/mythtranscode.sh
```
 
Then:
```
sudo mv /usr/bin/mythtranscode /usr/bin/mythtranscode.real
sudo ln -s /usr/share/mythtv/mythtranscode.sh /usr/bin/mythtranscode

```
 
As racmar said:
> **racmar said:**
> 
This will temporarily rename the .ICEauthority file before starting mythtranscode and then rename it back after mythtranscode finishes. I changed the old <<your mythtv username>> to the `whoami` command. If this does not work for you, use your actual mythtv user account above.
 
For mythwelcome and mytharchivehelper, just follow the above but replace transcode with welcome (or archivehelper).  Change it in the names of the files and in the contents of the files too.
 
Have fun!

---

### Post by bigtdp on 2009-11-24
Looks like this problem has been resolved in the latest version of Mythbuntu - 9.10

Finally!! :D

xTx

---

### Post by rlongfield on 2010-03-26
Nope not solved :(

I'm running 9.10 and I am still getting the same error. I can't remove the .ICE file as I require remote access to my myth box.

---

### Post by bigtdp on 2010-03-26
> **rlongfield said:**
> Nope not solved :(

I'm running 9.10 and I am still getting the same error. I can't remove the .ICE file as I require remote access to my myth box.

I also use remote access (SSH and web) to my myth box, which works fine without the .ICE file for me... 

If this isn't working for you, or you need to access the box by another method that relies on the .ICE file, then I would suggest creating another fault report for MythTV in the normal way... this has been a problem for years, maybe if someone else reports it too then it will eventually be fixed!

:D

xTx

---

### Post by steve@physics.queensu.ca on 2010-05-01
This solved my problem.  Thanks to everyone! 
Here's my contribution to make it just barely more elegant.
It's the same solution but uses a single sh file for all of the executables by detecting the name of the called command and acting appropriately.
First, use your favourite editor to create  "/usr/share/mythtv/mythICEfix.sh"
```
#! /bin/bash
FNAME=`basename $0`
 
# renames .ICEauthority to .ICEauthority.$FNAME
mv /home/`whoami`/.ICEauthority /home/`whoami`/.ICEauthority.$FNAME
 
# run the original filename + args
echo "Running: /usr/bin/$FNAME.real $@"
/usr/bin/$FNAME.real $@
errorval=$?
 
# renames .ICEauthority back to the original
mv /home/`whoami`/.ICEauthority.$FNAME /home/`whoami`/.ICEauthority
 
exit $errorval
```Make it executable with:  (I run a different flavour so use "sudo" as appropriate.)
```
chmod +x /usr/share/mythtv/mythICEfix.sh
```Now rename your troublesome executables with the .real suffix
```
mv /usr/bin/mytharchivehelper /usr/bin/mytarchivehelper.real
mv /usr/bin/mythtranscode /usr/bin/mythtranscode.real
mv /usr/bin/mythwelcome /usr/bin/mythwelcome.real
```Now create links to mythICEfix.sh with the appropriate names
```
ln -s /usr/share/mythtv/mythICEfix.sh /usr/bin/mytharchivehelper
ln -s /usr/share/mythtv/mythICEfix.sh /usr/bin/mythtranscode
ln -s /usr/share/mythtv/mythICEfix.sh /usr/bin/mythwelcome
```

---

### Post by steve@physics.queensu.ca on 2010-05-01
BTW, here's another useful script that I've used to help me debug issues.
Occasionally, it's handy to know the EXACT command that was run.
This uses the same trick as above to shim a script between your executable so that it can log the full command.
Use your favourite editor to create "/usr/share/mythtv/MythLogCommand.sh"
```
#! /bin/bash
FNAME=`basename $0`
 
# run the original filename + args
echo "MythLogCommand.sh Running: /usr/bin/$FNAME.real $@"
/usr/bin/$FNAME.real $@
errorval=$?
 
exit $errorval
```Make it executable... ```
chmod +x  /usr/share/mythtv/MythLogCommand.sh
```Rename a command with the .real suffix and soft link the original name to the script. ```
mv /usr/bin/mplex /usr/bin/mplex.real
ln -s /usr/share/mythtv/MythLogCommand.sh /usr/bin/mplex
```This will parrot the full command with arguments to your mythburn.log file.  Just search on "MythLog" in the file to find the command.
Example: ```
grep MythLog logs/mythburn.log
``` > MythLogCommand.sh Running: /usr/bin/mplex.real -f 8 -v 0 -o /video/dsk1/temp/work/temp.mpg /video/dsk1/temp/work/temp.m2v /usr/share/mythtv/mytharchive/music/silence.ac3
MythLogCommand.sh Running: /usr/bin/mplex.real -M -f 8 -v 0 --sync-offset 0ms -o /video/dsk1/temp/work/1/final.mpg /video/dsk1/temp/work/1/stream.mv2 /video/dsk1/temp/work/1/stream0.ac3
MythLogCommand.sh Running: /usr/bin/mplex.real -M -f 8 -v 0 --sync-offset -3ms -o /video/dsk1/temp/work/2/final.mpg /video/dsk1/temp/work/2/stream.mv2 /video/dsk1/temp/work/2/stream0.ac3


---

