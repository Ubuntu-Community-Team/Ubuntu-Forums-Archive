---
title: "MythExport: Export your MythTV recordings to your iPod or PSP"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by rhpot1991 on 2008-01-15
I posted instruction on howto install and configure on the wiki:
[https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

Give it a try out and leave some feedback.  If you have a ffmpeg line that works with another portable device, post it up in here or drop me an email and I can add it to the script.

Next version will add RSS generation and some file maintenance, as soon as I get a GUI in place so it is usable.

-John

Edit: Changed URL

---

### Post by SeanOB on 2008-02-12
Hello,

I'm getting this error when I run the script:
ffmpeg2pass-0.log: No such file or directory

Complete redirect output:
```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:22:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from '/mnt/myth/tv_recording/2063_20080211232900.mpg':
  Duration: 00:31:55.9, start: 0.289378, bitrate: 5190 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
ffmpeg2pass-0.log: No such file or directory

```

This is my job line:
mythexport.pl exportdir=/mnt/myth/iphone starttime=%STARTTIME% chanid=%CHANID% size=480x272 aspect=16:9 audio_bitrate=96kb video_bitrate=300kb export_device=ipod export_codec=h264 > ~/temp/debug.txt

Any ideas?  Where is it trying to put that log?

I ran in debug mode and then manually ran the commands and didn't have an issue.

Thanks,

Sean

---

### Post by mogmog on 2008-02-12
Thanks, found it easy to follow and set up. I also corrected some mistakes in the code examples for you.


In the end the lack of RSS in mythexport made me pick mythtv2psp.sh, but it didn't work too well out of the box and it's quite old by now. Also my PSP didn't recognize the feed at first.
I made some modifications to myth2psp and got it to work in the end though.

---

### Post by SeanOB on 2008-02-12
And now back to me :)

I hacked the debug mode to both display and run the system calls.  Anyone see anything obvious here?  I don't see it.  I have no problems just running the commands (that follow "USING") manually...  some permissions issue.

```

cat debug.txt 
Using compatibility mode


 Source filename:/mnt/myth/tv_recording/2063_20080211225900.mpg 
Destination filename:/mnt/myth/iphone/Comedy_Central_Pacific__The_Daily_Show_With_Jon_Stewart__20.mp4
 


USING nice -n19 ffmpeg -y -i /mnt/myth/tv_recording/2063_20080211225900.mpg -an -v 1 -threads auto -vcodec h264 -b 300kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 320x240 -f mp4 -pass 1 /dev/null 

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:22:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from '/mnt/myth/tv_recording/2063_20080211225900.mpg':
  Duration: 00:31:56.3, start: 0.289400, bitrate: 5189 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
ffmpeg2pass-0.log: Permission denied


USING nice -n19 ffmpeg -y -i /mnt/myth/tv_recording/2063_20080211225900.mpg -v 1 -threads auto -vcodec h264 -b 300kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 320x240 -acodec aac -ab 96kb -ar 48000 -ac 2 -f mp4 -pass 2 '/mnt/myth/iphone/Comedy_Central_Pacific__The_Daily_Show_With_Jon_Stewart__20.mp4' 2>&1 

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:22:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from '/mnt/myth/tv_recording/2063_20080211225900.mpg':
  Duration: 00:31:56.3, start: 0.289400, bitrate: 5189 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
ffmpeg2pass-0.log: No such file or directory


USING AtomicParsley '/mnt/myth/iphone/Comedy_Central_Pacific__The_Daily_Show_With_Jon_Stewart__20.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork Comedy_Central_Pacific_ --TVShowName "The Daily Show With Jon Stewart" --TVEpisode "EP002930531200" --TVEpisodeNum 21 --TVSeason 130 --description "" --title "" 2>&1 


AtomicParsley error: bad mpeg4 file (ftyp atom missing or alignment error).

mv: cannot stat `/mnt/myth/iphone/*temp*.mp4': No such file or directory

```

---

### Post by SeanOB on 2008-02-12
Aha!
Script was running in root dir (/).

So I added a little:
chdir $exportdir;

before the system calls and now it seems happy (or at least is running the first pass now).

-Sean

---

### Post by rhpot1991 on 2008-02-13
> **mogmog said:**
> Thanks, found it easy to follow and set up. I also corrected some mistakes in the code examples for you.


In the end the lack of RSS in mythexport made me pick mythtv2psp.sh, but it didn't work too well out of the box and it's quite old by now. Also my PSP didn't recognize the feed at first.
I made some modifications to myth2psp and got it to work in the end though.

Keep an eye out, RSS support will be added shortly.  I have it working but it needs some user input so I am in the process of creating a GUI for configuring everything.

---

### Post by rhpot1991 on 2008-02-13
> **SeanOB said:**
> Aha!
Script was running in root dir (/).

So I added a little:
chdir $exportdir;

before the system calls and now it seems happy (or at least is running the first pass now).

-Sean

Thanks for that Sean.  I will add it to the script when I get a chance.

---

### Post by thatkidandy on 2008-02-27
mythexport worked beautifully once I got the 'bugs' worked out

one small 'flaw' I ran into is that your system relies on the original naming scheme determined by mythtv in order to properly find the files. since I am running a freq cron job for mythrename to rename all the source recordings (not new links), mythexport could not find these files. I worked around this by having mythrename create symlinks instead (and leave the source files untouched), but you may want to investigate other ways to pull the file location. I tried to poke around the database to see where this information was stored but with little luck (I am also not experienced enough to know what to do with that info one I get it :P ).

anyway just a little heads up, rhpot1991

regardless, thank you SO much for this tool :)

---

### Post by Michael Thornton on 2008-02-27
Newbie here seeking some help.

I followed the directions but I am having at least two problems:

1. I get the error Unknown Codec ACC.  I have tried to find information on how to get all the codex installed for fmpeg, but I just can't seem to get it done.

2. I also get the error a previous poster is getting with "No such file or directory"

Any help appreciated.

EDIT - found directions on how to build ffmpeg with the needed codecs.  Still need help on #2.  I tried adding the line to the script per the other post in this thread, but I must have done it wrong since it still will not work.

---

### Post by rhpot1991 on 2008-02-29
> **Michael Thornton said:**
> Newbie here seeking some help.

I followed the directions but I am having at least two problems:

1. I get the error Unknown Codec ACC.  I have tried to find information on how to get all the codex installed for fmpeg, but I just can't seem to get it done.

2. I also get the error a previous poster is getting with "No such file or directory"

Any help appreciated.

EDIT - found directions on how to build ffmpeg with the needed codecs.  Still need help on #2.  I tried adding the line to the script per the other post in this thread, but I must have done it wrong since it still will not work.

Re-download mythexport.pl I added the line in there that should fix the "No such file or directory" error described above.  As far as ffmpeg, there is a very easy way of getting a good version that will do everything you need it to do.  Enable the medibuntu repository, add this to your /etc/apt/sources.list file:

```
deb http://packages.medibuntu.org/ gutsy free non-free
```

Then:
```
sudo apt-get update
sudo apt-get upgrade
```

And it should upgrade your ffmpeg for you.  If you still get the "No such file or directory" error, go head and add "debug" to the end of your mythexport line and run a job, then check /var/log/mythtv/mythbackend.log for the resulting ffmpeg line and try to run that by hand in your recordings directory, should help find whatever the problem may be.

---

### Post by rhpot1991 on 2008-02-29
> **thatkidandy said:**
> mythexport worked beautifully once I got the 'bugs' worked out

one small 'flaw' I ran into is that your system relies on the original naming scheme determined by mythtv in order to properly find the files. since I am running a freq cron job for mythrename to rename all the source recordings (not new links), mythexport could not find these files. I worked around this by having mythrename create symlinks instead (and leave the source files untouched), but you may want to investigate other ways to pull the file location. I tried to poke around the database to see where this information was stored but with little luck (I am also not experienced enough to know what to do with that info one I get it :P ).

anyway just a little heads up, rhpot1991

regardless, thank you SO much for this tool :)

You are right, I am not pulling the recording name from the DB.  I will modify the script to do so when I get some time.

---

### Post by rhpot1991 on 2008-03-03
Check out the wiki for a new installation method, making things much easier.

[https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

---

### Post by thatkidandy on 2008-03-13
mythexport failed after upgrading to myth 0.21. I did fix it after a little tinkering.

my backend log looked like this:
```

2008-03-13 12:29:39.043 JobQueue: Started "Export to Iphone (High)" for "MythBusters" recorded from channel 2048 at Thu Mar 13 09:59:00 2008
No config found; attempting to find mythbackend via UPnP.
2008-03-13 12:29:41.590 MainServer::HandleAnnounce Monitor
2008-03-13 12:29:41.593 adding: iota as a client (events: 0)
No backends found.  Please copy /home/mythtv/.mythtv/config.xml from a working MythTV installation instead.
Compilation failed in require at /usr/bin/mythexport line 33.
BEGIN failed--compilation aborted at /usr/bin/mythexport line 33.
2008-03-13 12:29:44.469 JobQueue: Finished "Export to Iphone (High)" for "MythBusters" recorded from channel 2048 at Thu Mar 13 09:59:00 2008.

```

line 33 in mythexport is:
```
use MythTv;
```

It could no longer find the backend I am assuming? Mine was running fine. 

It worked again after copying the config.xml from my home dir to the mythtv user dir. Could be an isolated update issue but just a heads up...

---

### Post by rhpot1991 on 2008-03-13
thatkidandy: can you post the output of dpkg -l libmyth-perl

Also what version of ubuntu/mythbuntu are you on and how did you install MythExport (by hand, via apt?)

---

### Post by thatkidandy on 2008-03-13
I am using Mythbuntu 7.10, I just updated to Mythtv 0.21 via apt.

I have installed mythexport via apt. Before copying the config file (which fixed the issue) I did try purging mythexport/atomic and reinstalling; however I still saw the same error.

Output of dpkg -l libmyth-perl
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  libmyth-perl                      0.21.0-0ubuntu2~gutsy1            A PERL library to access some MythTV features

```

again, thanks for your work :)

---

### Post by rhpot1991 on 2008-03-13
The config file you are referring to is config.xml in ~/.mythtv (or /home/mythtv/.mythtv if you are using a mythtv user to auto start everything) correct?  I recall seeing that error when I was testing MythExport on a fresh install without actually setting up MythTV yet.  I will have to look into it and see if there is any way this can happen without skipping some of the setup steps.

---

### Post by thatkidandy on 2008-03-13
> **rhpot1991 said:**
> The config file you are referring to is config.xml in ~/.mythtv (or /home/mythtv/.mythtv if you are using a mythtv user to auto start everything) correct?  I recall seeing that error when I was testing MythExport on a fresh install without actually setting up MythTV yet.  I will have to look into it and see if there is any way this can happen without skipping some of the setup steps.

To clarify, I had to copy config.xml from my personal user directory (/home/thatkidandy/.mythtv) to mythtv's at /home/mythtv/.mythtv (which the backend runs as).

:)

---

### Post by freymann on 2008-03-20
This is very neat indeed. I have it setup to export to ipod in *.mp4 and it works fine!

We use Archos 404's here, and I need something that ends in *.avi which is divx format. I thought I could just change the export_codec from mpeg4 to xvid in the command line but it still outputs *.mp4

I haven't seen anybody else talking about other output options though :-(

Oh, and I'm running MythBuntu 7.10 with all updates and I had the error about the missing config file.

It seems that the final setup uses the user account you created during the install as the main mythtv directory

So instead of 

/home/mythtv/.mythtv/files...

being utilized, it's

/home/your_first_username/.mythtv/files...

To keep MythExport happy and just created a symlink from my home directory to the /home/mythtv requirement. Easy enough.

---

### Post by rhpot1991 on 2008-03-20
> **freymann said:**
> This is very neat indeed. I have it setup to export to ipod in *.mp4 and it works fine!

We use Archos 404's here, and I need something that ends in *.avi which is divx format. I thought I could just change the export_codec from mpeg4 to xvid in the command line but it still outputs *.mp4

I haven't seen anybody else talking about other output options though :-(


You can try to just rename the resulting xvid file to .avi and see if it works.  I have been pumping them all out as .mp4 as that is what iTunes requires.  If you get a setup working for Archos players let me know and I will add them as a device.  If the iPod files don't work, it would be a good idea to look up the specs for the Archos and then you can use the debug option to get the ffmpeg line that is used to generate the iPod video and you can modify that in attempt to make some working video for your Archos.

---

### Post by freymann on 2008-03-21
> **rhpot1991 said:**
> You can try to just rename the resulting xvid file to .avi and see if it works.

 I tried that and the archos doesn't recognize the format at all.

> If you get a setup working for Archos players let me know and I will add them as a device. 

 Thanks!

 I've been tinkering with the ffmpeg command to make this happen and I have one that works great from the command line.

 If you could add an "archos" selection to MythExport that does this:

```

ffmpeg -i infile.mpg -vcodec mpeg4 -s 320x240 -b 906k -acodec mp3 -ab 192kb outfile.avi

```

 That would be super! :-)

---

### Post by rhpot1991 on 2008-03-28
> **freymann said:**
> 

 If you could add an "archos" selection to MythExport that does this:

```

ffmpeg -i infile.mpg -vcodec mpeg4 -s 320x240 -b 906k -acodec mp3 -ab 192kb outfile.avi

```


Can you try doing that with -acodec aac instead?  Were you able to find any information anywhere about what sort of max/min resolutions/bitrates and so on it likes?

---

### Post by freymann on 2008-03-28
> **rhpot1991 said:**
> Can you try doing that with -acodec aac instead?  Were you able to find any information anywhere about what sort of max/min resolutions/bitrates and so on it likes?

My inkling was this wouldn't work because I've run into issues before and MP3 was the only thing that worked for sound...

But I did try converting a short 30 min program using -acodec aac and as expected, when viewed on the archos av400 there's no sound. We have to stick to mp3.

Back at [www.archos.com](www.archos.com) I searched for our model (the AV400 series) and here's a bit of info I gleamed from their documentation:

-max 704x480 @ 30f/s
(although 320x240 works great for viewing on the actual unit itself)

-will play MPEG-4 video in DVD quality with CD quality stereo sound

-video playback is MPEG-4 SP w/MP3 or ADPCM stereo sound

When I converted my test 30 min. tv show it ended up being 237MB which is great.

My originally suggested ffmpeg line is the one to use, although I would suggest calling it Archos AV400, but most likely it will work with all models. The newer models support AC3 sound, but the AV400 series doesn't.

I hope that helps!

---

### Post by mickfromperth on 2008-03-30
Hello.

I'm recieving an error when mythexport tries to connect to the database.

Any tips on what I've done wrong?
---
2008-03-30 20:40:20.466 JobQueue: Started "export recording to xvid test settings" for "Battlestar Galactica" recorded from channel 1001 at Thu Mar 27 21:20:00 2008
DBI connect('database=mythconverg:host=localhost;port=3306','mythtv',...) failed: Access denied for user 'mythtv'@'localhost' (using password: YES) at /usr/share/perl5/MythTV.pm line 337
Cannot connect to database: 

2008-03-30 20:40:23.448 JobQueue: Finished "export recording to xvid test settings" for "Battlestar Galactica" recorded from channel 1001 at Thu Mar 27 21:20:00 2008.
---

I have confirmed the dbase password are correct.  Mythfrontent is what creates the config.xml file that mythexport uses.

---
myth@myth-desktop:~/Desktop$ cat /home/myth/.mythtv/config.xml 
<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>79cfb0b8-6f08-439a-a476-89fff3e1cf8a</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>mypass</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>
---

I have the same error from nuvexport.  I'd *really* appreciate some pointers on how to resolve this.  Everything else works?? (mythfrontend; mythweb...)

Mick

---

### Post by rhpot1991 on 2008-03-30
> **mickfromperth said:**
> 

I have the same error from nuvexport.  I'd *really* appreciate some pointers on how to resolve this.  Everything else works?? (mythfrontend; mythweb...)

Mick

Can you verify that your frontend is actually running as mythtv and not some other user.  If it is you need to copy or symlink the config.xml into that users's .mythtv directory.

Can you share some more information on your system, like are the backend and frontend both running on the same system.  What version of Ubuntu/Mythbuntu/MythTV are you running.  How did you verify the MySQL username and password and so on.

You should verify that there isn't a mysql.txt file with differen't information in it.  It could be pulling from that instead.

---

### Post by mickfromperth on 2008-03-30
Hi rhpot1991.

I'm running ubuntu 7.10 with mythbuntu packages.  Is there a scriped way to check what all my myth-package versions are?  When I started this; I was running one of the weekly cvs builds from about a month ago.  Last week I allowed synaptec to replace these packages with the v21 backports.  Hwoever; this nuvexport issue existed before and after the backport.

I'm running the back-end and frontend on the same box.

I've downloaded the latest version of nuvexport (v5 with svn/cvs update date of early march).

I'm using the mythexport script's via apt-get as per this howto.

About two days ago I noticed an extra user in /home/users.  My normal user is "myth".  But this user was "mythtv".  I removed that folder completely and this did not change the status of the issue.

locate mysql.txt give me only 2 files; and the contents of these files are the same.

locate config.xml is what highlighted the extra user folder; but now am back to only having a file under /etc/mythtv/. and /home/myth/.mythtv/.

The content of all the files though however is and was the same.  diff'ing the copies of each other I get no output.  And reading the passwords they are the same.

I have confirmed the passwords and settings are the same as that in myth-fronend gui.  Going to setup or settings.  It's about 2 layers into the menu alhtough I can't remember the exact steps.  There is the "localhost" setting; the port settings (0 in myth-frontend). and the username and password.

I'm usuming the setting in the GUI are correct as it can watch tv fine; and displays the tvguide fine.  Is there an issue with assuption?  I ahve no idea what is database fed and what is not??

Lastly; I don't know how to confirm the user a process is running under?  How can I check this?

Mick

---

### Post by mickfromperth on 2008-03-31
[PHP]
locate config.xml is what highlighted the extra user folder; but now am back to only having a file under /etc/mythtv/. and /home/myth/.mythtv/.[/PHP]

This was wrong.  Seems I still had a bung config.xml lying around.  After updating it with the correct settings this now works.

I think what is happening is myth-frontent runs as user myth.  If updates config.xml under user myth home folder.  Byth backend runs as user mythtv.  Any script called by mythbackend runs as user mythtv and therefore the config.xml created by mythfrontend is not found.

I still don't know how to confirm what user a process is running as.  But if this is the case; would this be considered a bug in mythubuntu??

Mick

---

### Post by mickfromperth on 2008-04-02
Hello.

One more question: is it possible to have mythexport replace my recordings?  I'm assuming mythexport is using nuvexport or is related in some way, so I'm assuming it's probably not possible but I'll throw it out there just the same??

If not, are there any scripts out there that people have which will handle disk management automagically.  What I'de like is that all my recordings are deleted by mythtv as needed to ensure capacity.  But I'd also like for these converted video's to expire as well.

As I'm only doing this compression to save space, this would be very neet!

Mick

---

### Post by rhpot1991 on 2008-04-02
> **mickfromperth said:**
> Hello.

One more question: is it possible to have mythexport replace my recordings?  I'm assuming mythexport is using nuvexport or is related in some way, so I'm assuming it's probably not possible but I'll throw it out there just the same??

If not, are there any scripts out there that people have which will handle disk management automagically.  What I'de like is that all my recordings are deleted by mythtv as needed to ensure capacity.  But I'd also like for these converted video's to expire as well.

As I'm only doing this compression to save space, this would be very neet!

Mick

Currently it does not.  Though it is in the works so we can have our recordings work with the 360 over UPnP.  I would suggest just making your own cronjob to delete exported file after they are over so many days old?

---

### Post by The Odometer on 2008-04-12
Ok, I'm lost. It clearly isn't working for me. I'm sure I'm missing something obvious. Please excuse my lack of knowledge. Here's what I get when I attempt to run mythexport in a terminal. Please help me!!

chris@mythbox:~$ mythexport exportdir=/mythtv/ipod starttime=20071225200 chanid=1032 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.
Use of uninitialized value in substitution (s///) at /usr/bin/mythexport line 170.
Use of uninitialized value in substitution (s///) at /usr/bin/mythexport line 173.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 180.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 181.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 181.
Use of uninitialized value in pattern match (m//) at /usr/bin/mythexport line 184.


 Source filename:/var/lib/mythtv/recordings/ 
Destination filename:/mythtv/ipod/SPSOUTH---20071225200
 
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/ -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/SPSOUTH---20071225200.mp4' 2>&1 



USING AtomicParsley '/mythtv/ipod/SPSOUTH---20071225200.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork SPSOUTH --TVShowName "" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "" --title "" 2>&1 


Thanks for any help you can give me. :)

---

### Post by rhpot1991 on 2008-04-12
> **The Odometer said:**
> Ok, I'm lost. It clearly isn't working for me. I'm sure I'm missing something obvious. Please excuse my lack of knowledge. Here's what I get when I attempt to run mythexport in a terminal. Please help me!!

chris@mythbox:~$ mythexport exportdir=/mythtv/ipod starttime=20071225200 chanid=1032 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.
Use of uninitialized value in substitution (s///) at /usr/bin/mythexport line 170.
Use of uninitialized value in substitution (s///) at /usr/bin/mythexport line 173.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 180.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 181.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 181.
Use of uninitialized value in pattern match (m//) at /usr/bin/mythexport line 184.


 Source filename:/var/lib/mythtv/recordings/ 
Destination filename:/mythtv/ipod/SPSOUTH---20071225200
 
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/ -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/SPSOUTH---20071225200.mp4' 2>&1 



USING AtomicParsley '/mythtv/ipod/SPSOUTH---20071225200.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork SPSOUTH --TVShowName "" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "" --title "" 2>&1 


Thanks for any help you can give me. :)

Remove the debug flag from your line.  When you do that it outputs the commands it will use instead of running them.  The point of debug is that you can get these commands and run them yourself if something goes wrong.

---

### Post by The Odometer on 2008-04-12
Ok..thanks for the help so far. I did that, here's what I got:

chris@mythbox:~$ mythexport exportdir=/mythtv/ipod starttime=20071225200 chanid=1032 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.
Use of uninitialized value in substitution (s///) at /usr/bin/mythexport line 170.
Use of uninitialized value in substitution (s///) at /usr/bin/mythexport line 173.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 180.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 181.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 181.
Use of uninitialized value in pattern match (m//) at /usr/bin/mythexport line 184.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 268.
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-shared
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Mar 29 2008 20:51:38, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
/var/lib/mythtv/recordings/: Unknown format
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open /mythtv/ipod/SPSOUTH---20071225200.mp4 for reading: No such file or directory
rm: cannot remove `/mythtv/ipod/SPSOUTH---20071225200.mp4': No such file or directory
mv: cannot stat `/mythtv/ipod/*temp*': No such file or directory


Any ideas now?

Thanks!

---

### Post by rhpot1991 on 2008-04-14
What versions of mythtv and mythexport do you have?

Run:
dpkg -l mythtv-common | grep ^ii
dpkg -l mythexport | grep ^ii

It looks like it didn't actually find the file name in the database, are you sure the recording actually exists there?  Does it play in the frontend?  Was this file actually recorded by MythTV, or did you import it somehow?

---

### Post by The Odometer on 2008-04-14
> **rhpot1991 said:**
> What versions of mythtv and mythexport do you have?

Run:
dpkg -l mythtv-common | grep ^ii
dpkg -l mythexport | grep ^ii

It looks like it didn't actually find the file name in the database, are you sure the recording actually exists there?  Does it play in the frontend?  Was this file actually recorded by MythTV, or did you import it somehow?

Yes, the file does play in the front end, and was recorded using MythTV. I found out one problem, the file name was incorrect. However, I'm still getting an error. I've changed all the permissions on both the mythtv recording folder (/var/lib/mythtv/recordings) and the /mythtv/ipod folders to allow all users to write to them. (Just to get this to work).


Here's what I am getting...
chris@mythbox:~$ mythexport exportdir=/mythtv/ipod starttime=20071225200000 chanid=1032 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 
ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open /mythtv/ipod/SPSOUTH-College_Flash_Classics-2001_Football_Alabama_vs_Sou.mp4 for reading: No such file or directory
rm: cannot remove `/mythtv/ipod/SPSOUTH-College_Flash_Classics-2001_Football_Alabama_vs_Sou.mp4': No such file or directory
mv: cannot stat `/mythtv/ipod/*temp*': No such file or directory
chris@mythbox:~$ 

My version of mythtv is ii  mythtv-common  0.21.0-0ubuntu2~gutsy1 A personal video recorder application (common data)

My version of mythexport is: mythexport     1.0.1-0ubuntu2~ppa5 Export MythTV recording to portable media players

I also just ran the debug command, and I got this output...

chris@mythbox:~$ mythexport exportdir=/mythtv/ipod starttime=20071225200000 chanid=1032 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debug
Going into new mode


 Source filename:/var/lib/mythtv/recordings/1032_20071225200000.mpg 
Destination filename:/mythtv/ipod/SPSOUTH-College_Flash_Classics-2001_Football_Alabama_vs_Sou
 


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1032_20071225200000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/SPSOUTH-College_Flash_Classics-2001_Football_Alabama_vs_Sou.mp4' 2>&1 



USING AtomicParsley '/mythtv/ipod/SPSOUTH-College_Flash_Classics-2001_Football_Alabama_vs_Sou.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork SPSOUTH --TVShowName "College Flash Classics" --TVEpisode "EP004559050029" --TVEpisodeNum 28 --TVSeason  --description "" --title "2001 Football: Alabama vs. South Carolina" 2>&1 


Any ideas now?

Thanks for the help so far. I think I'm getting closer...

---

### Post by rhpot1991 on 2008-04-14
Provided you aren't doing anything strange with user accounts, you directories permissions should look like this:
drwxrwsr-x  4 mythtv mythtv 4096 2008-03-25 20:52 recordings

Try running the ffmpeg line output with the debug command and see what that does.

libraw1394.so.5 is for firewire I think, are you using anything firewire here?  You can try installing libraw1394-8 and libraw1394-dev and see if they help at all.

---

### Post by The Odometer on 2008-04-14
Seems as if I fixed it. I had followed some other directions with ffmpeg--and my ffmpeg seemed to be messed up. I uninstalled ffmpeg, and reinstalled it and it worked. I already had installed the libraw1394, but it wasn't finding it. Thanks for your help! I appreciate it!

---

### Post by ratclma on 2008-06-08
I am new to mythtv and mythexport and am getting a similar problem can somebody help please?
below is the results for the mythexport and then if i run the ffmpeg command on it's own.

mark@ubuntu:~$ mythexport exportdir=/mythtv/ipod starttime=20080601220000 chanid=1007 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.


 Source filename:/mnt/nas/tv/1007_20080601220000.mpg 
Destination filename:/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4
 
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.


USING nice -n19 ffmpeg -i /mnt/nas/tv/1007_20080601220000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' 2>&1 



USING AtomicParsley '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork BBC-THREE --TVShowName "Family Guy" --TVEpisode "fp.bbc.co.uk/4J5EGK" --TVEpisodeNum  --TVSeason  --description "Peter starts an anti-immigration group, but he quickly changes his mind when he finds out that he was born in Mexico. Adult humour." --title "Padre De Familia" 2>&1 

mark@ubuntu:~$ ffmpeg -i /mnt/nas/tv/1007_20080601220000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' 2>&1
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mpegts, from '/mnt/nas/tv/1007_20080601220000.mpg':
  Duration: 00:19:56.6, start: 67426.773378, bitrate: 4398 kb/s
  Stream #0.0[0x26c]: Video: mpeg2video, yuv420p, 720x576, 6500 kb/s, 25.00 fps(r)
  Stream #0.1[0x26d](eng): Audio: mp2, 48000 Hz, stereo, 256 kb/s
  Stream #0.2[0x26f](eng): Subtitle: dvbsub
  Stream #0.3[0x26e](eng): Audio: mp3
Output #0, mp4, to '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4':
  Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240, q=2-31, 300 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: aac, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

Thanks

---

### Post by rhpot1991 on 2008-06-08
> **ratclma said:**
> I am new to mythtv and mythexport and am getting a similar problem can somebody help please?
below is the results for the mythexport and then if i run the ffmpeg command on it's own.

mark@ubuntu:~$ mythexport exportdir=/mythtv/ipod starttime=20080601220000 chanid=1007 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.


 Source filename:/mnt/nas/tv/1007_20080601220000.mpg 
Destination filename:/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4
 
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.


USING nice -n19 ffmpeg -i /mnt/nas/tv/1007_20080601220000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' 2>&1 



USING AtomicParsley '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork BBC-THREE --TVShowName "Family Guy" --TVEpisode "fp.bbc.co.uk/4J5EGK" --TVEpisodeNum  --TVSeason  --description "Peter starts an anti-immigration group, but he quickly changes his mind when he finds out that he was born in Mexico. Adult humour." --title "Padre De Familia" 2>&1 

mark@ubuntu:~$ ffmpeg -i /mnt/nas/tv/1007_20080601220000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' 2>&1
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mpegts, from '/mnt/nas/tv/1007_20080601220000.mpg':
  Duration: 00:19:56.6, start: 67426.773378, bitrate: 4398 kb/s
  Stream #0.0[0x26c]: Video: mpeg2video, yuv420p, 720x576, 6500 kb/s, 25.00 fps(r)
  Stream #0.1[0x26d](eng): Audio: mp2, 48000 Hz, stereo, 256 kb/s
  Stream #0.2[0x26f](eng): Subtitle: dvbsub
  Stream #0.3[0x26e](eng): Audio: mp3
Output #0, mp4, to '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4':
  Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240, q=2-31, 300 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: aac, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

Thanks

Verify that your mythtv user (or user running the job) can actually write to /mythtv/ipod/.  Looks like they can't.

Your permissions should be the same as the other mythtv directories: drwxrwsr-x.  If its not run this:```
sudo 2775 chmod /mythtv/ipod
``` Then make sure mythtv is the owner (or group at least), If not do this:```
sudo chown mythtv:mythtv /mythtv/ipod
```

Also note, you don't have to use /mythtv/ipod/ and that directory may not exist unless you created it.   By default mythtv directories live under /var/lib/mythtv/ so you can always throw it there as well.

---

### Post by ratclma on 2008-06-08
> **rhpot1991 said:**
> Verify that your mythtv user (or user running the job) can actually write to /mythtv/ipod/.  Looks like they can't.

Your permissions should be the same as the other mythtv directories: drwxrwsr-x.  If its not run this:```
sudo 2775 chmod /mythtv/ipod
``` Then make sure mythtv is the owner (or group at least), If not do this:```
sudo chown mythtv:mythtv /mythtv/ipod
```

Also note, you don't have to use /mythtv/ipod/ and that directory may not exist unless you created it.   By default mythtv directories live under /var/lib/mythtv/ so you can always throw it there as well.

Tried as you suggested but still seem to be getting the problem:

mark@ubuntu:~$ sudo chmod 2775 /mythtv/ipod
mark@ubuntu:~$ sudo chown mythtv:mythtv /mythtv/ipod
mark@ubuntu:~$ mythexport exportdir=/mythtv/ipod starttime=20080601220000 chanid=1007 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.


 Source filename:/var/lib/mythtv/recordings/1007_20080601220000.mpg 
Destination filename:/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4
 
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1007_20080601220000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' 2>&1 



USING AtomicParsley '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork BBC-THREE --TVShowName "Family Guy" --TVEpisode "fp.bbc.co.uk/4J5EGK" --TVEpisodeNum  --TVSeason  --description "Peter starts an anti-immigration group, but he quickly changes his mind when he finds out that he was born in Mexico. Adult humour." --title "Padre De Familia" 2>&1 

Thanks for your help so far.

---

### Post by mooseman089 on 2008-06-19
Hi I'm also looking to convert my mythtv videos for my ipod but I saw in your post that you were going to work on adding rss support so the videos can be downloaded into the itunes podcast.  I was just wondering if that has already been added or are you still working on it.

---

### Post by rhpot1991 on 2008-06-21
> **ratclma said:**
> Tried as you suggested but still seem to be getting the problem:

mark@ubuntu:~$ sudo chmod 2775 /mythtv/ipod
mark@ubuntu:~$ sudo chown mythtv:mythtv /mythtv/ipod
mark@ubuntu:~$ mythexport exportdir=/mythtv/ipod starttime=20080601220000 chanid=1007 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.


 Source filename:/var/lib/mythtv/recordings/1007_20080601220000.mpg 
Destination filename:/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4
 
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1007_20080601220000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' 2>&1 



USING AtomicParsley '/mythtv/ipod/BBC-THREE_Family_Guy_Padre_De_Familia_20080601220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork BBC-THREE --TVShowName "Family Guy" --TVEpisode "fp.bbc.co.uk/4J5EGK" --TVEpisodeNum  --TVSeason  --description "Peter starts an anti-immigration group, but he quickly changes his mind when he finds out that he was born in Mexico. Adult humour." --title "Padre De Familia" 2>&1 

Thanks for your help so far.

I don't see anything sticking out that is wrong there.  Did you try running those ffmpeg lines by hand to see what happens?

---

### Post by rhpot1991 on 2008-06-21
> **mooseman089 said:**
> Hi I'm also looking to convert my mythtv videos for my ipod but I saw in your post that you were going to work on adding rss support so the videos can be downloaded into the itunes podcast.  I was just wondering if that has already been added or are you still working on it.

I have this done but need to package it up, stay tuned for an update.

---

### Post by The Odometer on 2008-06-22
> **mooseman089 said:**
> Hi I'm also looking to convert my mythtv videos for my ipod but I saw in your post that you were going to work on adding rss support so the videos can be downloaded into the itunes podcast.  I was just wondering if that has already been added or are you still working on it.

I'm not certain we're talking about the same thing--but I use ITunes to take my videos from my mythtv backend to my IPOD. What I did was created a Samba share on my backend--connected it to my windows computer with ITunes--and simply drag the shows into ITunes. It works perfectly every time.

If that wasn't what you were referring to--then forgive me...but I thought I'd throw my two cents worth in.

---

### Post by torch12 on 2008-07-13
A couple of notes and questions:

I have version 1.0.0 configured and everything works perfectly.... but it is somewhat incomplete for my needs.

My primary goal of using mythexport is to be able to view recordings on my AppleTV. I do not have that running yet. I am waiting for the RSS/video podcasting capability that has been referred to on a couple of occasions. Any idea on an ETA? I chose to use this tool instead of myth2ipod despite it having that capability because this one seems easier to use.

How about adding AppleTV as a supported device? I really don't know what the "export_device" setting does, but if it changes some of the coding information, an AppleTV setting would probably be useful. ATV has some quirky requirements.

I would like to second the idea of automating the deletion of the source recording after the export has completed. In this particular case, Myth is really just being used to record junk and export it. I do not need the source recording after that and the space savings would be significant.

And last, I have noticed reference to version 1.0.1 in a couple of posts. But apt-get only fines 1.0.0 for me. Is 1.0.1 designated for for a specific version of Ubuntu? I have a somewhat limited understanding of Ubuntu in general so I'm not certain how to get the latest of stuff all the time. I typically just rely on the built-in update mechanisms.

Thanks!
Rick

---

### Post by Joeb454 on 2008-08-28
This thread is continued with a new thread outside the forum archive,

Please find that thread at: [http://ubuntuforums.org/showthread.php?t=903505](http://ubuntuforums.org/showthread.php?t=903505)

---

