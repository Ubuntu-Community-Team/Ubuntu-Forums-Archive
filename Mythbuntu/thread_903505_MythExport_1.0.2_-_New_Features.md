---
title: "MythExport 1.0.2 - New Features"
date: 2008-08-28
forum: Mythbuntu
---

### Post by rhpot1991 on 2008-08-28
MythExport 1.0.2 has been released.  For more information check out the wiki: [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

New Features:

- RSS Support. Just hit [http://X.X.X.X/mythexport](http://X.X.X.X/mythexport). This will work with your internal URL and, if configured, your external URL as well.
- File cleanup. A daily cronjob will delete files when they reach their expiration date.
- New "none" device & codec. Instead of exporting the video, a symlink is made to the original recording. ** THIS FEATURE MAY NEED ADDITIONAL TESTING **
- Some bug fixes. 

If you have any problems with the RSS feed make sure your config.xml is symlinked as mentioned in the troubleshooting portion of the wiki.

As always let me know if you have any problems or have any feedback to provide.

UPDATE: I am moving the packages to the Mythbuntu Testing PPA.  This way I can do some development on my own PPA without breaking everyone's system.  You should remove my PPA from your apt sources and add this one instead: [http://launchpad.net/~mythbuntu-testing/+archive](http://launchpad.net/~mythbuntu-testing/+archive)

ANOTHER UPDATE: Medibuntu will not be releasing ffmpeg for Intrepid, MythExport 1.0.5 on the Mythbuntu Testing PPA deals with this.

---

### Post by ReddogOne on 2008-08-29
Brilliant. Just what I have been waiting for. Shall be trying it out over the weekend. Good work those involved :D

---

### Post by ReddogOne on 2008-08-29
In the instructions it says...

> Troubleshooting

Verify that the user which runs the script has permissions to create files in the directory you are exporting to. 

What directory am I exporting to? I used the default but like an idiot I didn't note it down!

I'm getting ERROR: Directory i snot writeable when I run the mythexport command on the instruction page (not sure if this should work like that).

Looking throw the script I think its /home/mythtv but I'm sure I made it so everyone should be able to do anything (maybe I haven't).

Any help would be great...

---

### Post by rhpot1991 on 2008-08-29
> **ReddogOne said:**
> In the instructions it says...
What directory am I exporting to? I used the default but like an idiot I didn't note it down!

Check /etc/mythtv/mythexport.cfg
If you don't want to use this directory then do ```
sudo dpkg-reconfigure mythexport
``` and pick a different one.

> **ReddogOne said:**
> I'm getting ERROR: Directory i snot writeable when I run the mythexport command on the instruction page (not sure if this should work like that).

The info that goes into mythexport is specific to the recordings on your system so I would guess that it wouldn't match up.  If you want to run a test I would follow the wiki and make a user job and then go pick a recording to test with, you can see this done in the wiki and the newest version of mythweb allows you to easily run jobs on recordings.

> **ReddogOne said:**
> Looking throw the script I think its /home/mythtv but I'm sure I made it so everyone should be able to do anything (maybe I haven't).

Any help would be great...

Using home directories is normally frowned upon in MythTV in general as different users run different parts of myth and you may get some permission problems.  Try something like /mythtv/ or /var/log/mythtv(the default).

---

### Post by syphr42 on 2008-08-29
Just a note if anyone out there is trying this and is getting a server 500 error when hitting [http://X.X.X.X/mythexport](http://X.X.X.X/mythexport) - check your apache2 error.log. For me, it said it couldn't find perl lib XML/RSS.pm so I did a 'sudo apt-get install libxml-rss-perl' (which grabbed that and a bunch of required dependencies) and then everything started working.

Edit: forgot to mention that I am running Hardy.

---

### Post by rhpot1991 on 2008-08-29
> **syphr42 said:**
> Just a note if anyone out there is trying this and is getting a server 500 error when hitting [http://X.X.X.X/mythexport](http://X.X.X.X/mythexport) - check your apache2 error.log. For me, it said it couldn't find perl lib XML/RSS.pm so I did an 'sudo apt-get install libxml-rss-perl' (which grabbed that and a bunch of required dependencies) and then everything started working.

Look like I missed a dependency, thanks for the heads up.  
Edit: Bug created, fixed and uploaded to PPA.

Also worth noting that if your config.xml is not linked like is described in the bottom of the wiki, you may get a server 500 error as well.

---

### Post by mooseman089 on 2008-08-30
When I try going to [http://mythserv/mythexport](http://mythserv/mythexport) I get a 404 error. I was wondering if there was any other steps I need to do to configure the rss support.

---

### Post by rhpot1991 on 2008-08-30
> **mooseman089 said:**
> When I try going to [http://mythserv/mythexport](http://mythserv/mythexport) I get a 404 error. I was wondering if there was any other steps I need to do to configure the rss support.

First run```
dpkg -l mythexport |grep ^ii
```
and make sure your version is 1.0.2-0ubuntu2~ppa2

Then I would check /var/www and make sure there is a symlink to /usr/share/mythtv/mythweb

Are you positive you can access apache on this box to begin with?  Try hitting it without the mythexport on the end to make sure it is accessible.

---

### Post by mooseman089 on 2008-08-30
Ok for some reason I dont have new mythexport I guess
```
dpkg -l mythexport |grep ^ii
ii  mythexport                                 1.0-0ubuntu1                                         Export MythTV recording to portable media players

```
I'm using 8.04 so I'm not sure why it isn't up to date.

---

### Post by rhpot1991 on 2008-08-30
> **mooseman089 said:**
> Ok for some reason I dont have new mythexport I guess
```
dpkg -l mythexport |grep ^ii
ii  mythexport                                 1.0-0ubuntu1                                         Export MythTV recording to portable media players

```
I'm using 8.04 so I'm not sure why it isn't up to date.

In 8.04 you need to go add my PPA to your apt sources (directions in the wiki).  This is new functionality for the upcoming intrepid release.

---

### Post by ReddogOne on 2008-08-30
> **rhpot1991 said:**
> First run```
dpkg -l mythexport |grep ^ii
```
and make sure your version is 1.0.2-0ubuntu2~ppa2

EDIT: Sorted this ---- I have ...ppa1! How do I upgrade? ---- Must have done something silly. Added the sources but somehow still got older versions?!?!?!?!

Current status is I still don't seem to be generating the ipod videos but I am now getting an rss feed in my browser but because I don't seem to be creating the vids its empty!

Thing is the job seems to run (by looking at status on mythweb) for a few seconds (testing on a 4 minute recording).

(Breaking news rss feed is now listing recording did job on but no vid exists!)

---

### Post by mooseman089 on 2008-08-30
Ok I added the repo and now the rss is working great.  I noticed that the video looks interlaced which is a little annoying I was wondering if there was an option to do deinterlacing and also the file includes the commercials is there anyway to remove them?

---

### Post by rhpot1991 on 2008-08-30
> **ReddogOne said:**
> I have ...ppa1! How do I upgrade?

Current status is I still don't seem to be generating the ipod videos but I am now getting an rss feed in my browser but because I don't seem to be creating the vids its empty!

Thing is the job seems to run (by looking at status on mythweb) for a few seconds (testing on a 4 minute recording).

(Breaking news rss feed is now listing recording did job on but no vid exists!)

Just upgrade again, I added ppa2 last night to fix the dependency issue.

Check your backend logs (/var/log/mythtv/mythbackend.log) and find mythexport running in there.  Perhaps you have a version of ffmpeg that cannot do aac(if so check the wiki link and get ffmpeg from medibuntu)?  If you are still having problems add the debug option and run the user job on another recording, this will spit out some ffmpeg lines into your backend log, you can then run these by hand to see what is going wrong.

---

### Post by rhpot1991 on 2008-08-30
> **mooseman089 said:**
> Ok I added the repo and now the rss is working great.  I noticed that the video looks interlaced which is a little annoying I was wondering if there was an option to do deinterlacing and also the file includes the commercials is there anyway to remove them?

For deinterlacing you can try modifying the mythexport script in /usr/bin.  There is a -deinterlace option for ffmpeg, so you can just find the proper line that should be executing and add it in there.  Let me know how the results look.  Also, what device are you looking at these with?

As far as the commercials, there is an automatic script on this page: [http://www.mythtv.org/wiki/index.php/Removing_Commercials](http://www.mythtv.org/wiki/index.php/Removing_Commercials).  I don't much care for it as the commercial flagging has lots of false positives and I think its easier to just skip over commercials than to lose content.  You can go in and remove the commercials yourself as mentioned in that wiki page and then run mythexport on them and they will be commercial free.  Depends if you have the time for this or not.

---

### Post by ReddogOne on 2008-09-02
> **rhpot1991 said:**
> Check your backend logs (/var/log/mythtv/mythbackend.log) and find mythexport running in there.  Perhaps you have a version of ffmpeg that cannot do aac(if so check the wiki link and get ffmpeg from medibuntu)?  If you are still having problems add the debug option and run the user job on another recording, this will spit out some ffmpeg lines into your backend log, you can then run these by hand to see what is going wrong.

Screamed to the sound of trumpets... "Got it working"!

ffmpeg was missing so got them and all the over medi stuff I could. Still didn't work but thanks to you pointing me to the log sorted it all out.

(Sorry not in front of myth box so the rest is from memory).

Getting an error on line 301 or mythexport script about concatenating un initialised values... but seems to work anyway! 

For some reason I have to use /home/mythtv/ipod in the command rather than /mythtv/ipod so maybe I have a problem somewhere else.

I also needed to change the link in /var/www (and the rest) to point to /home/mythtv/ipod for them to seen on /mycomputer/mythexport/video so something else not quite working right.

But it most definitely is a working proof of concept. MythBox recording TV has serving them (through a windows box running iTunes) to my AppleTV and iPod.

Would be nice to have two rss, one for high res and one for low but I'm quite happy with what it does now. Guessing it might not be such a hard thing for me to change now you (rhpot1991) has done the hard work.

(Now just need to get iTunes running in wine or virtualBox for a one box solution)

---

### Post by rhpot1991 on 2008-09-02
> **ReddogOne said:**
> 
Getting an error on line 301 or mythexport script about concatenating un initialised values... but seems to work anyway!
 
This is normal, the listing data doesn't always have all the info needed so it will warn you about appending empty strings.

> **ReddogOne said:**
> 
For some reason I have to use /home/mythtv/ipod in the command rather than /mythtv/ipod so maybe I have a problem somewhere else.

I also needed to change the link in /var/www (and the rest) to point to /home/mythtv/ipod for them to seen on /mycomputer/mythexport/video so something else not quite working right.

Did you tell it /home/mythtv/ipod when the install asked you for the directory?  It should be creating that directory if it doesn't exist but maybe that isn't working.

> **ReddogOne said:**
> 
But it most definitely is a working proof of concept. MythBox recording TV has serving them (through a windows box running iTunes) to my AppleTV and iPod.

Would be nice to have two rss, one for high res and one for low but I'm quite happy with what it does now. Guessing it might not be such a hard thing for me to change now you (rhpot1991) has done the hard work.

(Now just need to get iTunes running in wine or virtualBox for a one box solution)
The RSS feed should work with other applications that can read podcasts, not just iTunes.  Granted I've pretty much only tested with iTunes but podcasting has some standards so it should work with other apps.

I have some ideas for the multiple RSS feeds situation, I'll throw some things together tonight and see if its too late to get them included in intrepid.

---

### Post by rhpot1991 on 2008-09-02
UPDATE: I am moving the packages to the Mythbuntu Testing PPA.  This way I can do some development on my own PPA without breaking everyone's system.  You should remove my PPA from your apt sources and add this one instead: [http://launchpad.net/~mythbuntu-testing/+archive](http://launchpad.net/~mythbuntu-testing/+archive)

---

### Post by xykevinr on 2008-09-02
Can I have some help with installing please ?

Download worked ok, then during the install part, I was asked for database userid and password - i left them blank as suggested. Then I got access denied.

I then did an apt-get remove mythexport atomicparsley, hoping to get another go. But now I dont get the option of supplying the userid, it just fails. 

How do I start again ?

thanks, Kevin

---

### Post by rhpot1991 on 2008-09-02
> **xykevinr said:**
> Can I have some help with installing please ?

Download worked ok, then during the install part, I was asked for database userid and password - i left them blank as suggested. Then I got access denied.

I then did an apt-get remove mythexport atomicparsley, hoping to get another go. But now I dont get the option of supplying the userid, it just fails. 

How do I start again ?

thanks, Kevin
If MythExport is installed then you can
```
sudo dpkg-reconfigure mythexport
```

If it isn't installed then you can
```
sudo dpkg --purge mythexport
```

If in doubt do the 2nd and it will remove it.  As far as your MySQL password, by default your username will be root and your password will be empty.  When you install MySQL it asks you if you want to set a root password, if you did this then you want to enter that if not then you want to leave it blank.

If you forgot this password then you can
```
sudo dpkg-reconfigure mysql-server-5.0
```

---

### Post by ReddogOne on 2008-09-02
> **rhpot1991 said:**
> This is normal, the listing data doesn't always have all the info needed so it will warn you about appending empty strings.

Cool.

> **rhpot1991 said:**
> Did you tell it /home/mythtv/ipod when the install asked you for the directory?  It should be creating that directory if it doesn't exist but maybe that isn't working.

I think i left everything as the default. But I do know I messed the repos up so maybe something went funny. This is my proof of concept box so when I do it properly I'll be more careful.

> **rhpot1991 said:**
> The RSS feed should work with other applications that can read podcasts, not just iTunes.  Granted I've pretty much only tested with iTunes but podcasting has some standards so it should work with other apps.

What I explained badly is I wanted both rss to be read by iTunes but the high quality one is for my AppleTV and the lower one for my iPod. I think if you put a high quality one on the iPod it doesn't seem to re-encode it at a lower resolution/bitrate so it takes loads of space up on the iPod. 

Is your iTunes on a windows machine. My next task is to look into getting it running 'within' ubuntu using wine or VirtualBox but not sure if this is a none started or not.

> **rhpot1991 said:**
> I have some ideas for the multiple RSS feeds situation, I'll throw some things together tonight and see if its too late to get them included in intrepid.

Looking forward to seeing them. Things like what you are doing really put the icing on the mythTV cake! It mythtv also supported Freeview+ (UK) I'd be in heaven... yes I'm sad like that ;)

---

### Post by ReddogOne on 2008-09-16
Everything is all going well and its great being able to 'watch TV' on my iPod and AppleTV (software as new).

However I find I'm recording a lot of radio programmes. Is there a way I can put these recorded programs on my iPod without the video element as the iPod leaves the back light on, using up the battery.

Cheers...

---

### Post by rhpot1991 on 2008-09-18
> **ReddogOne said:**
> Everything is all going well and its great being able to 'watch TV' on my iPod and AppleTV (software as new).

However I find I'm recording a lot of radio programmes. Is there a way I can put these recorded programs on my iPod without the video element as the iPod leaves the back light on, using up the battery.

Cheers...

Get the latest version from the Mythbuntu Testing PPA and you should now have a mp3 option.

---

### Post by rhpot1991 on 2008-09-18
> **ReddogOne said:**
> 
What I explained badly is I wanted both rss to be read by iTunes but the high quality one is for my AppleTV and the lower one for my iPod. I think if you put a high quality one on the iPod it doesn't seem to re-encode it at a lower resolution/bitrate so it takes loads of space up on the iPod. 

Grab the latest release from the Mythbuntu Testing PPA, and check the wiki.  I just updated it, you can now tell the script a podcast name and then use that to only pull those specific recordings via the RSS feed.  Hopefully the documentation is pretty clear, if not ask away and I will clean it up.

> **ReddogOne said:**
> 
Is your iTunes on a windows machine. My next task is to look into getting it running 'within' ubuntu using wine or VirtualBox but not sure if this is a none started or not.


Yep, running on Windows.  I mostly do my iTunes stuff at work so I never bothered to look for other solutions.

---

### Post by ReddogOne on 2008-09-18
> **rhpot1991 said:**
> Get the latest version from the Mythbuntu Testing PPA ...

Very Brilliant! 

I'll give all the new stuff a go over the weekend (along with trying to find out why the backend keeps 'crashing').

---

### Post by sgunther on 2008-09-21
Any idea why when I run mythexport I get my backend filling up (Over 1 GB for 1 day) with...

frame=63230 q=2.0 size=  196510kB time=2109.1 bitrate= 763.3kbits/s

Any way to stop it?  I figure it is ffmpeg doing this....

---

### Post by nigel502 on 2008-09-23
Question - 

I can run the job from the command line, having the output showup through my itunes RSS/podcast feed, however whenever I run the job through mythweb the jobs do not run. 

My job that gets stuck is:
mythexport exportdir=/home/nwright/ipod starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4


My job from the command line says:
mythexport exportdir=/home/user/ipod starttime=20080921200000 chanid=1009 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4

Anything obvious? I'm running the most recent version.

---

### Post by rhpot1991 on 2008-09-24
> **nigel502 said:**
> Question - 

I can run the job from the command line, having the output showup through my itunes RSS/podcast feed, however whenever I run the job through mythweb the jobs do not run. 

My job that gets stuck is:
mythexport exportdir=/home/nwright/ipod starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4


My job from the command line says:
mythexport exportdir=/home/user/ipod starttime=20080921200000 chanid=1009 size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4

Anything obvious? I'm running the most recent version.

One thing I see is that your directory does not match between the two, could be a typo?  If that is not the problem then try checking your backend logs (located /var/log/mythtv/) for errors or hints.  You should also verify that you actually enabled running of the user job, just creating them doesn't make then runable.  Check the wiki as there are screen shots of this there.

---

### Post by rhpot1991 on 2008-09-24
> **sgunther said:**
> Any idea why when I run mythexport I get my backend filling up (Over 1 GB for 1 day) with...

frame=63230 q=2.0 size=  196510kB time=2109.1 bitrate= 763.3kbits/s

Any way to stop it?  I figure it is ffmpeg doing this....

I have verified the logs can grow to a very sizable size.  I will look into it and see if I can silence ffmpeg while still keeping the useful data around.

---

### Post by ReddogOne on 2008-09-24
Somewhere along the way I've messed it up. I get the following in the log...

> 2008-09-24 21:32:35.981 JobQueue: Started "Export to iPod (Medium)" for "Strictly Come Dancing" recorded from channel 5228 at Tue Sep 23 18:30:00 2008
2008-09-24 21:32:38.135 MainServer::HandleAnnounce Monitor
2008-09-24 21:32:38.140 adding: simon-desktop as a client (events: 0)
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/MythTV/StorageGroup.pm line 57.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.
Use of uninitialized value in concatenation (.) or string at /usr/bin/mythexport line 244.
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mpegts, from '/var/lib/mythtv/recordings/5228_20080923183000.mpg':
  Duration: 00:29:55.4, start: 16083.686178, bitrate: 5595 kb/s
  Stream #0.0[0x262]: Video: mpeg2video, yuv420p, 720x576, 6500 kb/s, 25.00 fps(r)
  Stream #0.1[0x263](eng): Audio: mp2, 48000 Hz, stereo, 256 kb/s
  Stream #0.2[0x265](eng): Subtitle: dvbsub
  Stream #0.3[0x264](eng): Audio: mp3
Output #0, mp4, to '/home/mythtv/ipod/BBC-TWO_Strictly_Come_Dancing_It_Takes_Two_20080923183000.mp4':
  Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240, q=2-31, 600 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: aac, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

AtomicParsley error: bad mpeg4 file (ftyp atom missing or alignment error).

mv: cannot stat `/home/mythtv/ipod/*temp*.mp4': No such file or directory
2008-09-24 21:32:39.362 JobQueue: Finished "Export to iPod (Medium)" for "Strictly Come Dancing" recorded from channel 5228 at Tue Sep 23 18:30:00 2008.

From command

> mythexport exportdir=/home/mythtv/ipod starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4

Any ideas? Went wrong somewhere when moving from yours to the test repository though I might have got one of your test ones at some point.

---

### Post by ReddogOne on 2008-09-24
Realised you need to put the podcast_name in! Not the mp4 generates but I don't get the rss feed. But I think this might be because somehow I've gone back to an old mythexport.

Installing a newer version of mythexport it wants a password... not sure what for!

EDIT: newer version sorted it!

---

### Post by rhpot1991 on 2008-09-24
> **ReddogOne said:**
> Realised you need to put the podcast_name in! Not the mp4 generates but I don't get the rss feed. But I think this might be because somehow I've gone back to an old mythexport.

Installing a newer version of mythexport it wants a password... not sure what for!

EDIT: newer version sorted it!

The podcast_name should be optional, if you don't put it in then it will still be accessible through the RSS but only if you don't specify a name.

Is the password you are referring to the mysql password it asks you for while installing?  I had to modify the table structure and need the mysql info to do so, so that is why it is asking you.  If it is elsewhere then that is something that should be looked into.

---

### Post by nigel502 on 2008-09-24
Thanks for the quick reply - I realized I didn't enable the run job option in backend-setup.

Once I did that all queued jobs fired on through.

Hello IT - did you try turning it on and off again.

Thanks,

---

### Post by ReddogOne on 2008-09-25
> **rhpot1991 said:**
> Is the password you are referring to the mysql password it asks you for while installing?  I had to modify the table structure and need the mysql info to do so, so that is why it is asking you.  If it is elsewhere then that is something that should be looked into.

Not sure why but its stop working again! AFAIK nothing changed.

It could the the mysql which I don't have set to anything. But don't get any output in the window after I just press return.

EDIT: The error I get after entering the password is : ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

One thing I thought was I un-installed and then re-installed the mythexport could this have applied the change twice or something.

EDIT (Again) May actually only work on some channels. Set up a load of recordings and exports on a number of different channels. Will report findings.

---

### Post by xinix on 2008-09-29
How do you remove a file from the RSS?  Everything works fine but I'm not sure how to get things out off the RSS.  I've tried deleting the mp4 file, but the show is still listed when I go to [http://127.0.0.1/mythexport](http://127.0.0.1/mythexport).  I'm sure it's simple enough but I'm missing it.

Thanks

---

### Post by rhpot1991 on 2008-09-29
> **xinix said:**
> How do you remove a file from the RSS?  Everything works fine but I'm not sure how to get things out off the RSS.  I've tried deleting the mp4 file, but the show is still listed when I go to [http://127.0.0.1/mythexport](http://127.0.0.1/mythexport).  I'm sure it's simple enough but I'm missing it.

Thanks

The easiest way to delete them would be to install something like phpmyadmin and go ahead and remove that recording from the mythexport table in the mythconverg database.  You can also do the same with the mysql command line client.

If you haven't already removed the video file then it may be easy to just modify the "delDate" column for this recording (make it an earlier date than today's date) and then the daily cron job will remove this recording all together when it runs again.

---

### Post by xinix on 2008-09-30
Thanks for the tip, I already have phpmyadmin installed so it was simple enough to clear the entries.  Though eventually it would be nice to have another option that doesn't involve editing the DB entry by hand.  Not complaining, this app rocks, and as I've learned things clear out automatically after a month.

---

### Post by ReddogOne on 2008-09-30
> **ReddogOne said:**
> EDIT (Again) May actually only work on some channels. Set up a load of recordings and exports on a number of different channels. Will report findings.

It seems that the problem in trying to mythexport a recording of a new episode of which a previous episode has failed to mythexport! 

For example. Strickly Come Dancing (BBC2) failed to mythexport the first time I recorded it. Now every recording of the same problem fails to export! All new recordings seem to export correctly.

If I get a chance I will try cleaning the DB and see what happens... but its been a while since I've done such a thing! A special clean option for mythexport would be cool.

Though I think I might do a clean install when next release of MythTV comes out.

---

### Post by rhpot1991 on 2008-09-30
> **ReddogOne said:**
> It seems that the problem in trying to mythexport a recording of a new episode of which a previous episode has failed to mythexport! 

For example. Strickly Come Dancing (BBC2) failed to mythexport the first time I recorded it. Now every recording of the same problem fails to export! All new recordings seem to export correctly.

If I get a chance I will try cleaning the DB and see what happens... but its been a while since I've done such a thing! A special clean option for mythexport would be cool.

Though I think I might do a clean install when next release of MythTV comes out.

I am thinking that your recording may be corrupted then.  Do other episodes of this show work, other shows from this channel?

Easiest way to clean would be to just install phpmyadmin and go ahead and clean the table by hand as you mess with things.

If you don't want to run phpmyadmin you can just do this:
```

mysql -uroot -p mythconverg
[enter password]
>delete from mythexport;
>exit;
```

---

### Post by ReddogOne on 2008-10-01
> **rhpot1991 said:**
> I am thinking that your recording may be corrupted then.  Do other episodes of this show work, other shows from this channel?

Other episodes of the show do not work.
Other shows on the channel work.

I'll try cleaning the DB and see what happens.

Cheers...

---

### Post by rhpot1991 on 2008-10-01
> **ReddogOne said:**
> Other episodes of the show do not work.
Other shows on the channel work.

I'll try cleaning the DB and see what happens.

Cheers...

Check the backend log in /var/log/mythtv just after you try to export that show.  If it fails there will be errors in there.

---

### Post by ReddogOne on 2008-10-01
> **rhpot1991 said:**
> Check the backend log in /var/log/mythtv just after you try to export that show.  If it fails there will be errors in there.

I get the stuff I quoted in post 29. Its not too helpful I'm afraid.

---

### Post by smalcolm on 2008-10-21
My MythTV box is behind a few firewalls so the 1.0.2 version of "mythexportRSS.cgi" didn't have the correct value in HTTP_HOST when my front-end reverse proxy (Apache) web server returns the output of the script from the MythTV web server. So I started learning & hacking to be able to sync some TV & Radio to my Nokia N95 automatically (and automatically backup selected recordings to my server that runs [Subsonic]("http://subsonic.sourceforge.net/"))...

See attachment for a updated "mythexportRSS.cgi" script that should be suitable for inclusion in a 1.0.3 release (after some testing & little code cleanup).

Highlights include:
[LIST]
[*]Works for me in a Reverse Proxy configuration.
[*]Use MIME::Types to automate MIME Type detection so RSS/Podcast software isn't confused by Audio only (codec=mp3) exports advertising themselves as "video/mpeg". There are other options to automate the creation of a valid MIME so please comment on the accuracy of this Perl Module?
[*]Added the file size 'length' element to each enclosure for each item so that the RSS is can consumed by software that validates the syntax of the entire XML before using it. eg: [Subsonic]("http://subsonic.sourceforge.net/")'s podcast reciever uses a Java parser.
[*]Fixed the Content-Type, so that Subsonic and Nokia Podcasting application can now subscribe to the feed. *Yes, you should now easily be able to have your Nokia automatically save onto your phone the latest TV and/or Radio that you have exported from MythTV!*
[*]Added rudimentary Category support: Try viewing the output in IE7 for an example of how it uses the (potentially multiple per item) <category> tag(s) to create a search+browse interface. Would be very useful for a long list of exported media.
[*]Sensible defaults for "managingEditor" and "webMaster" (and added a TTL so that the feed can be cached).
[/LIST]
 

[FONT="Courier New"][SIZE="1"]Disclaimer: These improvements make it easier still to replicate (your) digital media so your advised to use this capability only for legitimate (personal) viewing as defined by the laws of the country your resident in (and/or downloading from).[/SIZE][/FONT]
 
Work should still be done on the "multiple RSS feed" concept. The current mod-rewrite rule is good but might be able to be improved to handle spaces in the name of a feed/category (value of podcastName in the database 'mythexport' table). A heirarchy of feeds/categories would be the ultimate solution?
CURRENTLY WORK:  /mythtv/mythexport/?podcastName=Audio/The Chris Moyles Show
CURRENTLY FAILS: /mythtv/mythexport/Audio/The Chris Moyles Show/

Also the method of using stat() to get the filesize may not be portable. Someone please test this CGI running on a non-Linux box?

**rhpot1991:** Please re-package a new DEB and me to the Credits/Authors? :lolflag:

P.S. Mythexport could in theory distribute the processing of the data to other Myth (slave) Backends if they have access to the data on shared storage or can be sent the data?

---

### Post by belbo on 2008-10-23
Hi all. This is my first post on ubuntuforums. It looks to me like this thread is a dedicated and general mythexport thread, so hopefully I'm posting in the right place. I've just started using mythexport to transcode tv recordings to ipod format. Some of my recordings transcode perfectly but others have the audio completely out of sync. Based on my googling it seems that nobody else has reported such a problem - so hopefully I'm doing something very basic wrong. Does anyone have any ideas about how to fix this ?

The source recordings are Australian dvb-t broadcasts and all are automatically transcoded to a lower framerate and audio bitrate using mythtranscode before using mythexport. There are no sync or other problems with the source recordings.

The audio sync problem arises both when running mythexport from the command line and as a user job. 

I haven't figured out if there is a pattern to which recordings have the problems and those that don't. It seems a bit random at the moment. About 1 in 3 or 4 have the problem.

The following is my current command for the user job -

mythexport exportdir=/var/lib/mythtv/mythexport starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=96kb video_bitrate=300kb export_device=ipod export_codec=mpeg4

I have tried an audio bitrate of 192kb and video bitrate of 600kb but this does not solve the problem.

I'm using ubuntu 8.04, mythtv 0.21, have an amd 4850e dual core processor and 2gb ram with 256mb dedicated to onboard (ATI Radeon) graphics.

If anybody has ideas that may help I'd appreciate it. Thanks.

---

### Post by belbo on 2008-10-27
bump. anybody able to help ? would people recommend I post this under a separate topic heading ? thanks.

---

### Post by rhpot1991 on 2008-10-27
> **belbo said:**
> Hi all. This is my first post on ubuntuforums. It looks to me like this thread is a dedicated and general mythexport thread, so hopefully I'm posting in the right place. I've just started using mythexport to transcode tv recordings to ipod format. Some of my recordings transcode perfectly but others have the audio completely out of sync. Based on my googling it seems that nobody else has reported such a problem - so hopefully I'm doing something very basic wrong. Does anyone have any ideas about how to fix this ?

The source recordings are Australian dvb-t broadcasts and all are automatically transcoded to a lower framerate and audio bitrate using mythtranscode before using mythexport. There are no sync or other problems with the source recordings.

The audio sync problem arises both when running mythexport from the command line and as a user job. 

I haven't figured out if there is a pattern to which recordings have the problems and those that don't. It seems a bit random at the moment. About 1 in 3 or 4 have the problem.

The following is my current command for the user job -

mythexport exportdir=/var/lib/mythtv/mythexport starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=96kb video_bitrate=300kb export_device=ipod export_codec=mpeg4

I have tried an audio bitrate of 192kb and video bitrate of 600kb but this does not solve the problem.

I'm using ubuntu 8.04, mythtv 0.21, have an amd 4850e dual core processor and 2gb ram with 256mb dedicated to onboard (ATI Radeon) graphics.

If anybody has ideas that may help I'd appreciate it. Thanks.

2 things that I would try:
1. Make sure your ffmpeg is up to date, hopefully the latest from medibuntu
2. Try to mess around with exporting the recording before you transcode, see if you can eliminate one or the other?  I have only ever transcoded with the mpeg2 lossless myself.

If you don't get any results from the above we work on getting some sample clips to me to mess around with.

---

### Post by paulbawon on 2008-11-10
Ok, this is a great script but I'm having the same consistent problem over and over on my setup and I've run into a dead end trying to debug it.

If I get the script to transcode my myth recordings via either single pass x264 or standard mp4 the database script update my database fine and I end up with the the recording showing in the RSS feed.

However, if I use two pass x264 recordings it doesn't update the RSS and I get the following error in my mythbackend.log:

 > Finished writing to temp file.
DBD::mysql::st execute failed: MySQL server has gone away at /usr/bin/mythexport line 339.
ERROR: Unable to update table. at /usr/bin/mythexport line 339.

I can't for the life of me think what is causing this. Can you shed any light on this? Is anyone else experiencing this?

(And yes, my config file exists in all of the places listed in the wiki...)

---

### Post by rhpot1991 on 2008-11-12
I just uploaded a new version for Intrepid to the Mythbuntu Testing PPA, this deals with the problem that Medibuntu will not be releasing ffmpeg for Intrepid, MythExport 1.0.5 deals with this.

Get it here and let me know how it works: [https://launchpad.net/~mythbuntu-testing/+archive](https://launchpad.net/~mythbuntu-testing/+archive)

---

### Post by rhpot1991 on 2008-11-12
> **smalcolm said:**
> 
Highlights include:
[LIST]
Works for me in a Reverse Proxy configuration.

I fixed this as a bug which is available on the latest PPA build, but not in the current Ubuntu build: [https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/288186](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/288186)

> **smalcolm said:**
> 
[LIST]
[*]Use MIME::Types to automate MIME Type detection so RSS/Podcast software isn't confused by Audio only (codec=mp3) exports advertising themselves as "video/mpeg". There are other options to automate the creation of a valid MIME so please comment on the accuracy of this Perl Module?
[*]Added the file size 'length' element to each enclosure for each item so that the RSS is can consumed by software that validates the syntax of the entire XML before using it. eg: [Subsonic]("http://subsonic.sourceforge.net/")'s podcast reciever uses a Java parser.
[*]Fixed the Content-Type, so that Subsonic and Nokia Podcasting application can now subscribe to the feed. *Yes, you should now easily be able to have your Nokia automatically save onto your phone the latest TV and/or Radio that you have exported from MythTV!*
[*]Added rudimentary Category support: Try viewing the output in IE7 for an example of how it uses the (potentially multiple per item) <category> tag(s) to create a search+browse interface. Would be very useful for a long list of exported media.
[*]Sensible defaults for "managingEditor" and "webMaster" (and added a TTL so that the feed can be cached).
[/LIST]

Most of these are enhancements, so I will not be able to get them through in this iteration.  Once Jaunty development starts, they can be backported if they get enough testing.
 

> **smalcolm said:**
> 
Work should still be done on the "multiple RSS feed" concept. The current mod-rewrite rule is good but might be able to be improved to handle spaces in the name of a feed/category (value of podcastName in the database 'mythexport' table). A heirarchy of feeds/categories would be the ultimate solution?
CURRENTLY WORK:  /mythtv/mythexport/?podcastName=Audio/The Chris Moyles Show
CURRENTLY FAILS: /mythtv/mythexport/Audio/The Chris Moyles Show/

I plan on revisiting the multiple feed concept, it was thrown in last minute for a user who needed the functionality.

> **smalcolm said:**
> 
P.S. Mythexport could in theory distribute the processing of the data to other Myth (slave) Backends if they have access to the data on shared storage or can be sent the data?
Yes, you can do this.  You will need to install MythExport on both backends and make sure that the recording structures match up on them.  This way it can find the recordings in the same place no matter which backend it is running on.  Nothing a little NFS sharing can't handle.  Thanks for submitting the patch and sorry I took so long to reply, was busy trying to clean everything up for the release (turns out the bugs didn't get in anyways :()

---

### Post by belbo on 2008-11-17
Hi. Thanks a lot for your reply. Sorry for taking a while to respond - haven't been watching the post and haven't done any ipod transcodes for a while. Will try out your suggestions and get back to you. Really nice of you to offer having a look at sample clips. Cheers.

---

### Post by SpaceBas on 2008-11-20
Just wanted to pop in and say thanks - It tooke me a few hours to get MythExport up and running (mostly due to my impatiance) but now that it is working, I'm really impressed. Great work!

While the ability to use it with my iPod is nice, its even more fun to send the RSS feed to Boxee :) 

Thanks again!

---

### Post by SpaceBas on 2008-11-21
Hey Folks,
In addition to the praise above, I have a few questions.

First, I am trying to set up two jobs: 1 to convert for the appletv (and boxee) and another for iPod.

I have set up the following file strucutre
/local/media/Myth/vidoes - appleTV (high res stuff)
/local/media/Myth/videos/ipod  - ipod files
the jobs are placing the files in the correct locations, but the RSS feeds to not seem to work
the [http://mythserve/mythexport/ipod](http://mythserve/mythexport/ipod)  feed is empty, and the file appears in the main [http://mythserve/mythexport](http://mythserve/mythexport) feed (although it fails since the file is in the ../videos/ipod directory )

Secondly, does anyone have suggestions for settings for HD files for the ATV? My content is mostly all 1080p or 720p captures so I'm starting with HD stuff to begin with. I'm mostly looking for a fast transcode that is compatable with FrontRow (really using a MacMini, but the ATV format works well as a reference)

I say "fast transcode" to highlight that I'm using mpeg4, h.264 seems to run all night, even on my c2d 2.66ghz box. 

Looking foward to hearing what thoughts or suggestions this group has - thanks in advance 
-N
edited to add:

I've dome some reading and am going to ditch the ATV stuff - mythrename.pl works better for boxee
but now the iPod stuff is totally failing

```
iPod Job:
mythexport exportdir=/local/media/Myth/videos podcast_name=ipod starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4
```

```
mythtv@telluride:/local/media/Myth$ mythexport  starttime=20081023200000 chanid=1231 size=480x320 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debugGoing into new mode
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport line 194.


 Source filename:/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg 
Destination filename:/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000
 
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 314.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 314.


USING nice -n19 ffmpeg -i "/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg" -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 480x320 '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4' 2>&1 



USING AtomicParsley '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVE-HD --TVShowName "The This Old House Hour" --TVEpisode "EP007674100088" --TVEpisodeNum  --TVSeason  --description "Prefabricating interior and exterior wall systems; Douglas fir and live oak timbers frame the dining area; plug and play wiring system." --title "" 2>&1 
```


```
mythtv@telluride:/local/media/Myth$ nice -n19 ffmpeg -i "/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg" -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 480x320 '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4' 2>&1 
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpegts, from '/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg':
  Duration: 00:59:58.3, start: 28709.168811, bitrate: 13089 kb/s
  Program 1 
    Stream #0.0[0x31]: Video: mpeg2video, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 13500 kb/s, 29.97 tb(r)
    Stream #0.1[0x34](   ): Audio: liba52, 48000 Hz, stereo, 192 kb/s
Output #0, mp4, to '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 300 kb/s, 29.97 tb(c)
    Stream #0.1(   ): Audio: libfaac, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by mooseman089 on 2008-11-25
I was wondering if you had any recommendations on what to do with a setup that has a slave backend because I noticed if a show is recorded on the slave's tuner mythexport doesn't work.

---

### Post by rhpot1991 on 2008-11-26
> **SpaceBas said:**
> 
I have set up the following file strucutre
/local/media/Myth/vidoes - appleTV (high res stuff)
/local/media/Myth/videos/ipod  - ipod files
the jobs are placing the files in the correct locations, but the RSS feeds to not seem to work
the [http://mythserve/mythexport/ipod](http://mythserve/mythexport/ipod)  feed is empty, and the file appears in the main [http://mythserve/mythexport](http://mythserve/mythexport) feed (although it fails since the file is in the ../videos/ipod directory )

The RSS feed doesn't currently support multiple directories, you would be best just letting them all sit in the same directory and just using the podcast naming feature to have an appletv and an ipod podcast.

> **SpaceBas said:**
> 
```
iPod Job:
mythexport exportdir=/local/media/Myth/videos podcast_name=ipod starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4
```

```
mythtv@telluride:/local/media/Myth$ mythexport  starttime=20081023200000 chanid=1231 size=480x320 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4 debugGoing into new mode
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport line 194.


 Source filename:/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg 
Destination filename:/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000
 
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 314.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 314.


USING nice -n19 ffmpeg -i "/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg" -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 480x320 '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4' 2>&1 



USING AtomicParsley '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVE-HD --TVShowName "The This Old House Hour" --TVEpisode "EP007674100088" --TVEpisodeNum  --TVSeason  --description "Prefabricating interior and exterior wall systems; Douglas fir and live oak timbers frame the dining area; plug and play wiring system." --title "" 2>&1 
```


```
mythtv@telluride:/local/media/Myth$ nice -n19 ffmpeg -i "/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg" -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 480x320 '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4' 2>&1 
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpegts, from '/local/media/Myth/recordings/The This Old House Hour - 2008-10-23, 8-00 PM - Untitled.mpg':
  Duration: 00:59:58.3, start: 28709.168811, bitrate: 13089 kb/s
  Program 1 
    Stream #0.0[0x31]: Video: mpeg2video, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 13500 kb/s, 29.97 tb(r)
    Stream #0.1[0x34](   ): Audio: liba52, 48000 Hz, stereo, 192 kb/s
Output #0, mp4, to '/local/media/Myth/videos/WCVE-HD-The_This_Old_House_Hour--20081023200000.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 300 kb/s, 29.97 tb(c)
    Stream #0.1(   ): Audio: libfaac, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

I don't really see anything wrong here, have you tried with more than one recording?  Perhaps the recording file is corrupt?

---

### Post by rhpot1991 on 2008-11-26
> **mooseman089 said:**
> I was wondering if you had any recommendations on what to do with a setup that has a slave backend because I noticed if a show is recorded on the slave's tuner mythexport doesn't work.

The best current way to approach this would be to map out an NFS share of where the recordings are on the slave backend that way the master backend can see the recordings.

You could also install mythexport on the slave box and setup an NFS share to where ever mythexport needs to dump the files.  With the new RSS feature the packages will leave a lot of junk that you really don't need on a slave backend, you would be better just copying the script over on your own. And then installing the following dependencies: libmyth-perl, atomicparsley, libdbi-perl, libdbd-mysql-perl (could use some verification, I'm going off the top of my head here).  Once that is done as long as your config.xml is in the right places then mythexport should be able to see the master backend.  Perhaps I can make a mythexport-lite package if this would fit people's needs.

---

### Post by mooseman089 on 2008-11-28
I tried your second method of copying over the mythexport scripts and installing those dependencies and setup the nfs share but when the userjob runs I get this error
nice: ffmpeg: No such file or directory
I know the recording is stored in /var/lib/mythtv/recordings on the slave and I can play it fine but it looks like mythexport can't find it. Any input on what I'm doing?

---

### Post by rhpot1991 on 2008-11-28
> **mooseman089 said:**
> I tried your second method of copying over the mythexport scripts and installing those dependencies and setup the nfs share but when the userjob runs I get this error
nice: ffmpeg: No such file or directory
I know the recording is stored in /var/lib/mythtv/recordings on the slave and I can play it fine but it looks like mythexport can't find it. Any input on what I'm doing?

Make sure you have the following insatlled: ffmpeg, libavcodec-unstripped-51, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, libswscale-unstripped-0 

If that doesn't help add the debug option to your user job and try running the ffmpeg line yourself, then make sure that the file paths are all correct.

---

### Post by SpaceBas on 2008-11-30
> **rhpot1991 said:**
> 

I don't really see anything wrong here, have you tried with more than one recording?  Perhaps the recording file is corrupt?

Thanks rhpot1991 - it appears that any HD shows fail due to the audio feed - could it be the codec that is used for the HD stuff?

---

### Post by LorenzoS on 2008-12-12
First, thanks very much for this great utility.  

I had this working great under Hardy, and after upgrading to Intrepid today reinstalled version 1.0.6 and it’s running great still.  However, I notice my mythbackend.log now has lots of stuff I did not notice before even though I do not have debug specified in my command line.  

My job command is 
```
mythexport exportdir=/mythtv/mythexport starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4
```

And I have tons of stuff in mythbackend.log that looks like this:```
frame=  271 fps= 38 q=8.0 size=     562kB time=8.7 bitrate= 531.8kbits/s    
frame=  296 fps= 38 q=7.0 size=     609kB time=9.5 bitrate= 528.1kbits/s    
frame=  317 fps= 39 q=6.0 size=     651kB time=10.1 bitrate= 526.0kbits/s    
frame=  337 fps= 39 q=6.0 size=     691kB time=10.8 bitrate= 522.3kbits/s    
frame=  357 fps= 39 q=5.0 size=     725kB time=11.5 bitrate= 514.6kbits/s 
``` 

And this:```
Started writing to temp file.
 Progress: >0%-----------------------------------------------------------------------------|
 Progress: >1%-----------------------------------------------------------------------------|--------------------------------------------------.
.
.
 Progress: ==========================================================================>99%--|
 Progress: ===========================================================================>100%|
 Finished writing to temp file.
```

I don’t think it’s a problem but it does seem to clutter my log and I wonder if there is a way to reduce the verbosity?

---

### Post by lingenfr on 2008-12-23
I think that I have set this up according to the wiki and information in this forum, but it is not working. I tried running my userjob from the command line and here is what I got. I am trying to export a file for my psp.

linghome@MYTHTV-BACKEND:/var/lib/mythtv/videos$ mythexport exportdir=/var/lib/mythtv/videos/psp starttime=%STARTTIME% chanid=%CHANID% size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4
DBD::mysql::st execute failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '%CHANID% AND rec.starttime='%STARTTIME%'' at line 3 at /usr/bin/mythexport line 136.
ERROR: Cannot connect to database

Any help appreciated.

---

### Post by rhpot1991 on 2008-12-25
> **LorenzoS said:**
> First, thanks very much for this great utility.  

I had this working great under Hardy, and after upgrading to Intrepid today reinstalled version 1.0.6 and it’s running great still.  However, I notice my mythbackend.log now has lots of stuff I did not notice before even though I do not have debug specified in my command line.  

My job command is 
```
mythexport exportdir=/mythtv/mythexport starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=300kb export_device=ipod export_codec=mpeg4
```

And I have tons of stuff in mythbackend.log that looks like this:```
frame=  271 fps= 38 q=8.0 size=     562kB time=8.7 bitrate= 531.8kbits/s    
frame=  296 fps= 38 q=7.0 size=     609kB time=9.5 bitrate= 528.1kbits/s    
frame=  317 fps= 39 q=6.0 size=     651kB time=10.1 bitrate= 526.0kbits/s    
frame=  337 fps= 39 q=6.0 size=     691kB time=10.8 bitrate= 522.3kbits/s    
frame=  357 fps= 39 q=5.0 size=     725kB time=11.5 bitrate= 514.6kbits/s 
``` 

And this:```
Started writing to temp file.
 Progress: >0%-----------------------------------------------------------------------------|
 Progress: >1%-----------------------------------------------------------------------------|--------------------------------------------------.
.
.
 Progress: ==========================================================================>99%--|
 Progress: ===========================================================================>100%|
 Finished writing to temp file.
```

I don’t think it’s a problem but it does seem to clutter my log and I wonder if there is a way to reduce the verbosity?

That is normal, I will look into adding an option to suppress that in the next version.

---

### Post by rhpot1991 on 2008-12-25
> **lingenfr said:**
> I think that I have set this up according to the wiki and information in this forum, but it is not working. I tried running my userjob from the command line and here is what I got. I am trying to export a file for my psp.

linghome@MYTHTV-BACKEND:/var/lib/mythtv/videos$ mythexport exportdir=/var/lib/mythtv/videos/psp starttime=%STARTTIME% chanid=%CHANID% size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4
DBD::mysql::st execute failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '%CHANID% AND rec.starttime='%STARTTIME%'' at line 3 at /usr/bin/mythexport line 136.
ERROR: Cannot connect to database

Any help appreciated.

Those variables in between the %'s are userjob specific.  When you run it from your command line by hand you will need to plug in the correct values yourself.  It looks like you need to look at the wiki again and follow the section about setting up the userjob, you shouldn't need to run anything from the command line unless you are debugging a problem.

---

### Post by SpaceBas on 2009-01-02
> **rhpot1991 said:**
> 


I don't really see anything wrong here, have you tried with more than one recording?  Perhaps the recording file is corrupt?

Rhpot - thanks for the reply.
I have been using Mythexport for a good month now and observing the behavior carefully. Without a doubt it is failing on all my HDTV recordings, although there are a few exceptions (30 Rock for instance). It works on all of my SD video. 

Interestingly I'm using an HDhomerun which is a digital only tuner so for SD content, I'd think the video feed would be the same as with HD. That brings me back to audio - are there any known bugs with 5.1 audio - might that be the cause?

---

### Post by johnelle on 2009-01-02
I thought I saw a reference in the release notes to a cron job to do the clean up on the rss feed after I delete stuff on my own but I don't see any cron jobs running.  

I know I can start hacking the database but I really didn't want to. 

Is there any other way to make sure that the feed contents match the actual files sitting there?

---

### Post by rhpot1991 on 2009-01-03
> **SpaceBas said:**
> Rhpot - thanks for the reply.
I have been using Mythexport for a good month now and observing the behavior carefully. Without a doubt it is failing on all my HDTV recordings, although there are a few exceptions (30 Rock for instance). It works on all of my SD video. 

Interestingly I'm using an HDhomerun which is a digital only tuner so for SD content, I'd think the video feed would be the same as with HD. That brings me back to audio - are there any known bugs with 5.1 audio - might that be the cause?

I have used it fine on recordings from my HDHR in the past.  Do you have specific examples of shows that always fail (you can PM them to me if you don't want to paste them in here).  This way I can record one of them and see if I can reproduce the issue.

I once had an episode of Mythbusters that exported without sound, but the another episode worked fine so I never looked into what actually happened.

---

### Post by rhpot1991 on 2009-01-04
> **johnelle said:**
> I thought I saw a reference in the release notes to a cron job to do the clean up on the rss feed after I delete stuff on my own but I don't see any cron jobs running.  

I know I can start hacking the database but I really didn't want to. 

Is there any other way to make sure that the feed contents match the actual files sitting there?

The cronjob lives in /etc/cron.daily/mythexport

It runs daily and removes the exported files and DB entries once they hit an expiration date.

If you deleted the files yourself then you will need to wait for the db entries to expire or go ahead and remove them yourself.

---

### Post by lingenfr on 2009-01-09
> **rhpot1991 said:**
> Those variables in between the %'s are userjob specific.  When you run it from your command line by hand you will need to plug in the correct values yourself.  It looks like you need to look at the wiki again and follow the section about setting up the userjob, you shouldn't need to run anything from the command line unless you are debugging a problem.

Yes, I am trying to figure out why the userjob is not working. I did follow the wiki. I will plug in actual values and see if I can identify the problem. Thanks.

---

### Post by rhpot1991 on 2009-01-09
> **lingenfr said:**
> Yes, I am trying to figure out why the userjob is not working. I did follow the wiki. I will plug in actual values and see if I can identify the problem. Thanks.

Add debug on the end of your user job.  Then run the job.  This will cause the job to spit out ffmpeg commands instead of trying to run them.  You can then attempt to run those commands and see if there are any issues.  Feel free to paste the results in here or use [http://mythbuntu.pastebin.com](http://mythbuntu.pastebin.com)

---

### Post by lingenfr on 2009-01-09
I will try the debug as well, but I did get it to run and here are my errors:

mythexport exportdir=/var/lib/mythtv/videos/psp starttime=20081214200000 chanid=1060 size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport line 190.
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 310.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 310.
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpeg, from '/var/lib/mythtv/recordings/1060_20081214200000.mpg':
  Duration: 01:59:57.9, start: 0.189289, bitrate: 5191 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Incorrect frame size

AtomicParsley error: bad mpeg4 file (ftyp atom missing or alignment error).

rm: cannot remove `/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000.mp4': Is a directory
mv: cannot stat `/var/lib/mythtv/videos/psp/*temp*': No such file or directory

Here it is with debug:

mythexport exportdir=/var/lib/mythtv/videos/psp starttime=20081214200000 chanid=1060 size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport line 190.


 Source filename:/var/lib/mythtv/recordings/1060_20081214200000.mpg
Destination filename:/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000

Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 310.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 310.


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1060_20081214200000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 800kb -ar 24000 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 480 -aspect 16:9 -r 30000/1001 -f psp '/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000.mp4' 2>&1



USING AtomicParsley '/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork MTV --TVShowName "Adam Sandler's Eight Crazy Nights" --TVEpisode "MV001267390000" --TVEpisodeNum  --TVSeason  --description "During Hanukkah, a temperamental lout (Adam Sandler) drinks, gets in trouble with the law and performs community service. Animated." --title "" 2>&1

---

### Post by rhpot1991 on 2009-01-10
> **lingenfr said:**
> I will try the debug as well, but I did get it to run and here are my errors:

mythexport exportdir=/var/lib/mythtv/videos/psp starttime=20081214200000 chanid=1060 size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport line 190.
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 310.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 310.
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpeg, from '/var/lib/mythtv/recordings/1060_20081214200000.mpg':
  Duration: 01:59:57.9, start: 0.189289, bitrate: 5191 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Incorrect frame size

AtomicParsley error: bad mpeg4 file (ftyp atom missing or alignment error).

rm: cannot remove `/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000.mp4': Is a directory
mv: cannot stat `/var/lib/mythtv/videos/psp/*temp*': No such file or directory

Here it is with debug:

mythexport exportdir=/var/lib/mythtv/videos/psp starttime=20081214200000 chanid=1060 size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4 debug
Going into new mode
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport line 190.


 Source filename:/var/lib/mythtv/recordings/1060_20081214200000.mpg
Destination filename:/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000

Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 310.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 310.


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1060_20081214200000.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 800kb -ar 24000 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 480 -aspect 16:9 -r 30000/1001 -f psp '/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000.mp4' 2>&1



USING AtomicParsley '/var/lib/mythtv/videos/psp/MTV-Adam_Sandler_s_Eight_Crazy_Nights--20081214200000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork MTV --TVShowName "Adam Sandler's Eight Crazy Nights" --TVEpisode "MV001267390000" --TVEpisodeNum  --TVSeason  --description "During Hanukkah, a temperamental lout (Adam Sandler) drinks, gets in trouble with the law and performs community service. Animated." --title "" 2>&1

Have you tried with other recordings?  It seems like this recording might be corrupt.  If other recordings don't work, what kind of hardware do you use, what settings for recording, etc?

---

### Post by lingenfr on 2009-01-10
Tried it again with a different recording. Here is what I got:

-------------------------------------------------------------------------
mythexport exportdir=/var/lib/mythtv/videos/psp starttime=20090103210404 chanid=1048 size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 310.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 310.
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpeg, from '/var/lib/mythtv/recordings/1048_20090103210404.mpg':
  Duration: 00:40:55.5, start: 0.189256, bitrate: 5192 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Incorrect frame size
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open /var/lib/mythtv/videos/psp/DISN-The_Even_Stevens_Movie--20090103210404.mp4 for reading: No such file or directory
rm: cannot remove `/var/lib/mythtv/videos/psp/DISN-The_Even_Stevens_Movie--20090103210404.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/videos/psp/*temp*': No such file or directory
linghome@MYTHTV-BACKEND:~$ mythexport exportdir=/var/lib/mythtv/videos/psp starttime=20090103210404 chanid=1048 size=480 x 272 aspect=16:9 audio_bitrate=192kb video_bitrate=800kb export_device=psp export_codec=mpeg4 debug
Going into new mode


 Source filename:/var/lib/mythtv/recordings/1048_20090103210404.mpg
Destination filename:/var/lib/mythtv/videos/psp/DISN-The_Even_Stevens_Movie--20090103210404

Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 310.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 310.


USING nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1048_20090103210404.mpg -acodec aac -ab 192kb -vcodec mpeg4 -b 800kb -ar 24000 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 480 -aspect 16:9 -r 30000/1001 -f psp '/var/lib/mythtv/videos/psp/DISN-The_Even_Stevens_Movie--20090103210404.mp4' 2>&1



USING AtomicParsley '/var/lib/mythtv/videos/psp/DISN-The_Even_Stevens_Movie--20090103210404.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork DISN --TVShowName "The Even Stevens Movie" --TVEpisode "MV001357800000" --TVEpisodeNum  --TVSeason  --description "Members (Shia LaBeouf, Nick Spano, Tom Virtue) of a family unwittingly appear on a reality-television show after the producer sends them to an island for a vacation." --title "" 2>&1
-------------------------------------------------------------------------

I guess I don't know on settings. I go into mythweb and select Record Once and check the box for Flag Commercials. I have a nuvexport job that creates xvid/mp3/avi files. If it is not obvious here, I have used the information on the wiki to try and set up a job to create files for the psp. I set up a similar job for ipod, but neither work. It is entirely possible that I am overlooking something fundamental.

---

### Post by johnelle on 2009-01-10
After success with MP4 I was going to switch some of my other batch (nuvexport) jobs over but it seems everything mythexport produces ends in ".mp4" which is not really appropriate for an xvid file.  I don't see any parameter to control the suffix(?).  I thought maybe zune would do it but didn't work. My first attempt at a windows media player compatible file was:

> 
mythexport exportdir=/media/storage starttime=%STARTTIME% chanid=%CHANID% size=480x320 export_device=zune export_codec=xvid

The file is playable by a MS media player but it is not registered for mp4 file types.  It crashes quicktime which is the default mp4 player.

John

---

### Post by rhpot1991 on 2009-01-10
> **lingenfr said:**
> 
I guess I don't know on settings. I go into mythweb and select Record Once and check the box for Flag Commercials. I have a nuvexport job that creates xvid/mp3/avi files. If it is not obvious here, I have used the information on the wiki to try and set up a job to create files for the psp. I set up a similar job for ipod, but neither work. It is entirely possible that I am overlooking something fundamental.

So you are running nuvexport on the recordings before you run MythExport?

---

### Post by lingenfr on 2009-01-10
> **rhpot1991 said:**
> So you are running nuvexport on the recordings before you run MythExport?

No, not even sure how that could be done. I have 3 userjobs. I have one nuvexport job that creates xvid/mp3/avi files for my video collection. Then I have two mythexport jobs. I for PSP and one for Ipod. Neither of the mythexport jobs work.

---

### Post by rhpot1991 on 2009-01-10
> **johnelle said:**
> After success with MP4 I was going to switch some of my other batch (nuvexport) jobs over but it seems everything mythexport produces ends in ".mp4" which is not really appropriate for an xvid file.  I don't see any parameter to control the suffix(?).  I thought maybe zune would do it but didn't work. My first attempt at a windows media player compatible file was:



The file is playable by a MS media player but it is not registered for mp4 file types.  It crashes quicktime which is the default mp4 player.


First thing first, there are only 2 options that will get you anything that isnt .mp4: mp3 or archos (will produce .avi)

Now, what is the point of what you are trying to accomplish?  I'd say you have a few options here:
1. Use vlc on windows
2. Use ipod device and open in quicktime/itunes
3. Use MythTV Player: [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/) (also included on the Mythbuntu CD)
4. Fix your default application for mp4s so that a good application is used

---

### Post by rhpot1991 on 2009-01-10
> **lingenfr said:**
> No, not even sure how that could be done. I have 3 userjobs. I have one nuvexport job that creates xvid/mp3/avi files for my video collection. Then I have two mythexport jobs. I for PSP and one for Ipod. Neither of the mythexport jobs work.

This is really weird, everything I see about ffmpeg throwing that error says that the problem occurs when you try to open a corrupted video file with ffmpeg.  I asked before (and didn't see an answer), what kind of tuner are you using?

---

### Post by lingenfr on 2009-01-11
> **rhpot1991 said:**
> I asked before (and didn't see an answer), what kind of tuner are you using?

You're right, I don't think I did. I have a Hauppauge PVR-150, a PVR-150 MCE and a WINTV-PVR-USB2. The recordings that I have been testing with were made by one of the two PVR-150's.

---

### Post by rhpot1991 on 2009-01-11
> **lingenfr said:**
> You're right, I don't think I did. I have a Hauppauge PVR-150, a PVR-150 MCE and a WINTV-PVR-USB2. The recordings that I have been testing with were made by one of the two PVR-150's.

Hmmmm, the PVR-150s should work pretty well, heck I have one and a 350.  What are your settings under Setup > Setup > TV Settings > Recording Profiles > MPEG 2 Encoders > Default (you should probably check that the rest match as well) > 3rd Page - Stream Type, 4th Page - Codec

Mine are MPEG-2 PS and MPEG-2 Hardware Encoder.

See what your setting are for these, you can try changing them but they will not apply until a new recording uses them.

---

### Post by rjackal on 2009-01-15
i've been running the latest Mythexport on Mythbuntu 8.10 things have been going smooth. But of late I have hit a rough patch. I have googled and read, and reinstalled Mythexport to no avail. I checked the mythbackend logs and I found the following:
"Argument "xvid" isn't numeric in numeric eq (==) at /usr/bin/mythexport line 122.
Argument "mpeg4" isn't numeric in numeric eq (==) at /usr/bin/mythexport line 122."
Can someone point me in the right direction?
Thanks

---

### Post by johnelle on 2009-01-15
> **rhpot1991 said:**
> First thing first, there are only 2 options that will get you anything that isnt .mp4: mp3 or archos (will produce .avi)

Now, what is the point of what you are trying to accomplish?  I'd say you have a few options here:
1. Use vlc on windows
2. Use ipod device and open in quicktime/itunes
3. Use MythTV Player: [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/) (also included on the Mythbuntu CD)
4. Fix your default application for mp4s so that a good application is used
The point is to accommodate my Creative Zen which uses MS file codecs.  It comes with a transcoding package but the closer I get to native MS the better.  Some of my friends and family use the IPOD so I am generating MP4s but I am not an itunes/ipod fan so I want an option to generate files more compatible with my zen.

---

### Post by rhpot1991 on 2009-01-16
> **rjackal said:**
> i've been running the latest Mythexport on Mythbuntu 8.10 things have been going smooth. But of late I have hit a rough patch. I have googled and read, and reinstalled Mythexport to no avail. I checked the mythbackend logs and I found the following:
"Argument "xvid" isn't numeric in numeric eq (==) at /usr/bin/mythexport line 122.
Argument "mpeg4" isn't numeric in numeric eq (==) at /usr/bin/mythexport line 122."
Can someone point me in the right direction?
Thanks

Make sure you have the latest from the testing PPA, this shouldn't be an issue if you have the latest and greatest.

---

### Post by rhpot1991 on 2009-01-16
> **johnelle said:**
> The point is to accommodate my Creative Zen which uses MS file codecs.  It comes with a transcoding package but the closer I get to native MS the better.  Some of my friends and family use the IPOD so I am generating MP4s but I am not an itunes/ipod fan so I want an option to generate files more compatible with my zen.

I'm not sure anyone has confirmed Zen support with any of the existing options, so you get to be the first.

If this is the player you have: [http://us.creative.com/products/product.asp?category=213&subcategory=214&product=16999&nav=1](http://us.creative.com/products/product.asp?category=213&subcategory=214&product=16999&nav=1)
Then it claims it can support the following: Video Playback Format: MJPEG, WMV9 and (with transcoding - MPEG1 and 2, MPEG4-SP, DivX 4 and 5 and XviD)

So, I would try the archos devices first, with the xvid codec.  I see some example ffmpeg lines that are very similar to the archos one that I use.  Let me know if this works, if not I can get you a test version to try out.

---

### Post by gaz2373 on 2009-02-11
Hi I am running into difficulties with mythexport and mythbuntu amd64 which is intrepid 8.10

I found ffmpeg to be at fault so to cut a long story short built the lasted version as at Feb 2009 and enabled pretty much everything. 
On running the command
'ffmpeg -i /mnt/nas/tv/1007_20080601220000.mpg -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/file.mp4'

I got a trell error so fixed it with the new flag method of
+4mv+aic -trellis

But now I get the error 
'Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height'

as far as I can tell the audio codec is installed so any help on this would be greatly appreciated.

---

### Post by rhpot1991 on 2009-02-11
> **gaz2373 said:**
> Hi I am running into difficulties with mythexport and mythbuntu amd64 which is intrepid 8.10

I found ffmpeg to be at fault so to cut a long story short built the lasted version as at Feb 2009 and enabled pretty much everything. 
On running the command
'ffmpeg -i /mnt/nas/tv/1007_20080601220000.mpg -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/file.mp4'

I got a trell error so fixed it with the new flag method of
+4mv+aic -trellis

But now I get the error 
'Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height'

as far as I can tell the audio codec is installed so any help on this would be greatly appreciated.

You don't want to build the latest version, the flags will not match up.  What you need to do is enable the Mythbuntu testing PPA and get the latest version of MythExport from there (release is still held up in the SRU process).  This should automagically install ffmpeg and all the corresponding dependencies from the Ubuntu repos.  Make sure you completely remove your compiled ffmpeg first.

---

### Post by gaz2373 on 2009-02-11
Hi rhpot1991 thank you for your quick response.

I have installed mythexport from the testing but still have problems with ffmpeg not all the codecs are enabled:

ffmpeg -version

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
FFmpeg r11872+debian_3:0.svn20080206-12ubuntu3
libavutil   3212800
libavcodec  3355136
libavformat 3409664
libavdevice 3407872


Perhaps I do not have the right sources in my sources.list please see below

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse


# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) intrepid main

---

### Post by rhpot1991 on 2009-02-11
> **gaz2373 said:**
> Hi rhpot1991 thank you for your quick response.

I have installed mythexport from the testing but still have problems with ffmpeg not all the codecs are enabled:

ffmpeg -version

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
FFmpeg r11872+debian_3:0.svn20080206-12ubuntu3
libavutil   3212800
libavcodec  3355136
libavformat 3409664
libavdevice 3407872


Perhaps I do not have the right sources in my sources.list please see below

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse


# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) intrepid main

That seems to match up with mine, was exactly is the issue you are seeing?

---

### Post by gaz2373 on 2009-02-11
When I run the ffmpeg mannual generated by myth export as below I get the codec error.


ffmpeg -i "/var/lib/mythtv/recordings/7302_20090131120000.mpg" -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 '/mythtv/BBC-2-England-Malcolm_in_the_Middle-Tiki_Lounge-20090131120.mp4' 2>&1

~
~
Input #0, mpegts, from '/var/lib/mythtv/recordings/7302_20090131120000.mpg':
  Duration: 00:19:55.5, start: 44913.978456, bitrate: 7872 kb/s
  Program 1
    Stream #0.0[0x13ec]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 7980 kb/s, 25.00 tb(r)
    Stream #0.1[0x13ed](eng): Audio: mp2, 48000 Hz, stereo, 256 kb/s
    Stream #0.2[0x13ee](NAR): Audio: mp2, 48000 Hz, stereo, 256 kb/s
    Stream #0.3[0x13f0](eng): Subtitle: dvbsub
File '/mythtv/BBC-2-England-Malcolm_in_the_Middle-Tiki_Lounge-20090131120.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/mythtv/BBC-2-England-Malcolm_in_the_Middle-Tiki_Lounge-20090131120.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240 [PAR 4:3 DAR 16:9], q=2-31, 300 kb/s, 25.00 tb(c)
    Stream #0.1(eng): Audio: libfaac, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by gaz2373 on 2009-02-14
After further investigation I have found that there appears to be an issue with the audio codec arguments on my system. I can encode the video side of things no problem but audio keeps throwing up errors. 

After a lot of trial and error I have found I can get ffmpeg to encode with audio using the following:

-acodec libfaac -ac 2 -ab 192kb -ar 48000

The files now encode without error -ac 2 sets the output to stereo and -ar 48000 sets the rate at 48000hz

After adding these settings to the script it now works like a dream.

Thanks for this excellent script.

---

### Post by rhpot1991 on 2009-02-20
> **gaz2373 said:**
> After further investigation I have found that there appears to be an issue with the audio codec arguments on my system. I can encode the video side of things no problem but audio keeps throwing up errors. 

After a lot of trial and error I have found I can get ffmpeg to encode with audio using the following:

-acodec libfaac -ac 2 -ab 192kb -ar 48000

The files now encode without error -ac 2 sets the output to stereo and -ar 48000 sets the rate at 48000hz

After adding these settings to the script it now works like a dream.

Thanks for this excellent script.

Thanks for this update, I added this option as a tweak in the upcoming jaunty release.

---

### Post by rhpot1991 on 2009-02-20
Anyone using the latest and greatest from the Mythbuntu Testing PPA please add a comment to the following bugs indicating that everything is working fine for you:

[https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/282498](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/282498)
[https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/297016](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/297016)
[https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/288184](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/288184)
[https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/297019](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/297019)
[https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/288186](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/288186)

Once this SRU is finally said and done, I can work on getting the Jaunty version out on the Mythbuntu Testing PPA.  Lots of new features :)

-John

---

### Post by Calmor on 2009-03-10
Hi all,

I'm trying to set up MythExport on my system to use with my PSP, and have having some issues with the web portion.

My system is running Mythbuntu 8.10 x64, upgraded from 8.04, so there may be a few issues remaining from the upgrade. 

I purged and reinstalled MythExport this morning as the previous install must have not worked completely (most of the files in /var/www/mythexport were missing).  I'm now running mythexport 1.99.2-0ubuntu1~ppa0.2.

After installation, I was getting the 500 Internal Server Error message.  Checking the apache2 error.log, I found that I needed to install libhtml-template-perl.  (I received error messages on line 5 of file.cgi)

Now, the web interface works, but whenever attempting to access or write the configuration files, I get more 500 errors.  The error.log file shows:

```
[Tue Mar 10 07:49:05 2009] [error] [client xxx.xxx.x.xxx] No config, so a new one will be made. at /var/www/mythexport/save_setup.cgi line 15., referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup_details.cgi
[Tue Mar 10 07:49:05 2009] [error] [client xxx.xxx.x.xxx] '_SYNTAX' is not defined at /usr/share/perl5/Config/Simple.pm line 529., referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup_details.cgi
[Tue Mar 10 07:49:05 2009] [error] [client xxx.xxx.x.xxx] Premature end of script headers: save_setup.cgi, referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup_details.cgi

```

I tried to copy and paste the ipod config from the Ubuntu MythExport wiki into my config, to see if it was an issue with the lack of a configuration, but now get a similar message:

```
[Tue Mar 10 08:03:07 2009] [error] [client xxx.xxx.x.xxx] Something went wrong. No supported configuration file syntax found. Either the file is of wrong syntax, or there is a bug in guess_syntax() method. at /usr/share/perl5/Config/Simple.pm line 184, <FH> line 4., referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup.cgi
[Tue Mar 10 08:03:07 2009] [error] [client xxx.xxx.x.xxx] Premature end of script headers: setup_edit.cgi, referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup.cgi

```

I then tried installing libconfig-simple-perl but it was already installed, and tried to uncomment the use command in setup_details.cgi that calls config::simple, to no avail.


I get the same messages when trying other options, such as choosing "user job" from the web interface.

Do you have any suggestions that I might try?

Thank you for your help!

---

### Post by rhpot1991 on 2009-03-10
> **Calmor said:**
> Hi all,

I'm trying to set up MythExport on my system to use with my PSP, and have having some issues with the web portion.

My system is running Mythbuntu 8.10 x64, upgraded from 8.04, so there may be a few issues remaining from the upgrade. 

I purged and reinstalled MythExport this morning as the previous install must have not worked completely (most of the files in /var/www/mythexport were missing).  I'm now running mythexport 1.99.2-0ubuntu1~ppa0.2.

After installation, I was getting the 500 Internal Server Error message.  Checking the apache2 error.log, I found that I needed to install libhtml-template-perl.  (I received error messages on line 5 of file.cgi)

Now, the web interface works, but whenever attempting to access or write the configuration files, I get more 500 errors.  The error.log file shows:

```
[Tue Mar 10 07:49:05 2009] [error] [client xxx.xxx.x.xxx] No config, so a new one will be made. at /var/www/mythexport/save_setup.cgi line 15., referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup_details.cgi
[Tue Mar 10 07:49:05 2009] [error] [client xxx.xxx.x.xxx] '_SYNTAX' is not defined at /usr/share/perl5/Config/Simple.pm line 529., referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup_details.cgi
[Tue Mar 10 07:49:05 2009] [error] [client xxx.xxx.x.xxx] Premature end of script headers: save_setup.cgi, referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup_details.cgi

```

I tried to copy and paste the ipod config from the Ubuntu MythExport wiki into my config, to see if it was an issue with the lack of a configuration, but now get a similar message:

```
[Tue Mar 10 08:03:07 2009] [error] [client xxx.xxx.x.xxx] Something went wrong. No supported configuration file syntax found. Either the file is of wrong syntax, or there is a bug in guess_syntax() method. at /usr/share/perl5/Config/Simple.pm line 184, <FH> line 4., referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup.cgi
[Tue Mar 10 08:03:07 2009] [error] [client xxx.xxx.x.xxx] Premature end of script headers: setup_edit.cgi, referer: http://xxx.xxx.x.xxx:xxxx/mythexport/setup.cgi

```

I then tried installing libconfig-simple-perl but it was already installed, and tried to uncomment the use command in setup_details.cgi that calls config::simple, to no avail.


I get the same messages when trying other options, such as choosing "user job" from the web interface.

Do you have any suggestions that I might try?

Thank you for your help!

Discussion for the 2.0 release should take place in this thread instead: [http://ubuntuforums.org/showthread.php?p=6851017](http://ubuntuforums.org/showthread.php?p=6851017)

I am trying to reproduce this issue on my machines, I'll post back when I have something.

---

### Post by snaef on 2009-03-11
I am having the same problem.  Let me know if you need any log files.

---

### Post by danskelly on 2009-03-11
Me too!

---

### Post by rhpot1991 on 2009-03-11
As I noted in the 2.0 release thread ([http://ubuntuforums.org/showthread.php?p=6851017](http://ubuntuforums.org/showthread.php?p=6851017)) this issue is fixed in 1.99.3 release on the Testing PPA.  Please move all discussion of the latest version to the above mentioned thread, thanks.

---

