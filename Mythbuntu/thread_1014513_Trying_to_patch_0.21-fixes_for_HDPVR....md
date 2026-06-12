---
title: "Trying to patch 0.21-fixes for HDPVR..."
date: 2008-12-17
forum: Mythbuntu
---

### Post by zoiks on 2008-12-17
Trying to get mythtv to use the Hauppauge HD-PVR (1212)...

Following the instructions at
[http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR)

This is what I've done:

  1) Downloaded, compiled, installed hdpvr. Tested it by capturing a few seconds of video that played back using VLC. (Crashes mplayer, though.)
  2) Checked out latest svn fixes version. Configured and compiled mythtv (just to check I have dependencies). Compiles fine.

But here's where I'm stuck:

  3) Tried to apply the patches (from #5866 and #5604) for using the HD-PVR:

```
mythbox@coral:~/sources/mythtv/release-0-21-fixes/mythtv$ patch -p0 -i ../../**mpegrecorder-hdpvr-v1.1.patch** 
patching file libs/libmythtv/mpegrecorder.h
Hunk #1 FAILED at 80.
Hunk #2 FAILED at 106.
Hunk #3 succeeded at 88 with fuzz 1 (offset -26 lines).
2 out of 3 hunks FAILED -- saving rejects to file libs/libmythtv/mpegrecorder.h.rej
patching file libs/libmythtv/mpegrecorder.cpp
Hunk #1 succeeded at 14 with fuzz 2 (offset -5 lines).
Hunk #2 FAILED at 82.
Hunk #3 FAILED at 483.
Hunk #4 succeeded at 375 (offset -135 lines).
Hunk #5 FAILED at 394.
Hunk #6 FAILED at 439.
Hunk #7 succeeded at 446 with fuzz 2 (offset -147 lines).
Hunk #8 succeeded at 476 (offset -147 lines).
Hunk #9 FAILED at 666.
Hunk #10 FAILED at 676.
Hunk #11 FAILED at 723.
Hunk #12 FAILED at 770.
Hunk #13 FAILED at 986.
Hunk #14 FAILED at 1049.
Hunk #15 FAILED at 1147.
Hunk #16 FAILED at 1157.
Hunk #17 FAILED at 1307.
Hunk #18 FAILED at 1404.
Hunk #19 FAILED at 1430.
Hunk #20 FAILED at 1447.
Hunk #21 FAILED at 1461.
Hunk #22 FAILED at 1529.
Hunk #23 FAILED at 1549.
Hunk #24 FAILED at 1656.
Hunk #25 FAILED at 1690.
21 out of 25 hunks FAILED -- saving rejects to file libs/libmythtv/mpegrecorder.cpp.rej

```

and

```
mythbox@coral:~/sources/mythtv/release-0-21-fixes/mythtv$ patch -p0 -i ../../**DeviceReadBuffer-polltimeout.2.patch** 
patching file libs/libmythtv/DeviceReadBuffer.h
patching file libs/libmythtv/DeviceReadBuffer.cpp
Hunk #1 succeeded at 89 (offset -1 lines).
Hunk #2 FAILED at 108.
Hunk #3 succeeded at 119 (offset -6 lines).
Hunk #4 succeeded at 232 (offset -8 lines).
Hunk #5 succeeded at 252 (offset -8 lines).
Hunk #6 succeeded at 281 (offset -8 lines).
Hunk #7 succeeded at 307 (offset -8 lines).
Hunk #8 succeeded at 316 (offset -8 lines).
Hunk #9 succeeded at 396 (offset -8 lines).
Hunk #10 succeeded at 412 (offset -8 lines).
1 out of 10 hunks FAILED -- saving rejects to file libs/libmythtv/DeviceReadBuffer.cpp.rej

```

So the question is, how do I get the patches to apply? SVN version says 19395.

Thanks in advance!

Edit: Added SOLVED to the title since my issue is now fixed.

---

### Post by managementboy on 2008-12-19
> **zoiks said:**
> Trying to get mythtv to use the Hauppauge HD-PVR (1212)...

Following the instructions at
[http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR)

This is what I've done:

  1) Downloaded, compiled, installed hdpvr. Tested it by capturing a few seconds of video that played back using VLC. (Crashes mplayer, though.)
  2) Checked out latest svn fixes version. Configured and compiled mythtv (just to check I have dependencies). Compiles fine.

But here's where I'm stuck:

  3) Tried to apply the patches (from #5866 and #5604) for using the HD-PVR:

```
mythbox@coral:~/sources/mythtv/release-0-21-fixes/mythtv$ patch -p0 -i ../../**mpegrecorder-hdpvr-v1.1.patch** 
patching file libs/libmythtv/mpegrecorder.h
Hunk #1 FAILED at 80.
Hunk #2 FAILED at 106.
Hunk #3 succeeded at 88 with fuzz 1 (offset -26 lines).
2 out of 3 hunks FAILED -- saving rejects to file libs/libmythtv/mpegrecorder.h.rej
patching file libs/libmythtv/mpegrecorder.cpp
Hunk #1 succeeded at 14 with fuzz 2 (offset -5 lines).
Hunk #2 FAILED at 82.
Hunk #3 FAILED at 483.
Hunk #4 succeeded at 375 (offset -135 lines).
Hunk #5 FAILED at 394.
Hunk #6 FAILED at 439.
Hunk #7 succeeded at 446 with fuzz 2 (offset -147 lines).
Hunk #8 succeeded at 476 (offset -147 lines).
Hunk #9 FAILED at 666.
Hunk #10 FAILED at 676.
Hunk #11 FAILED at 723.
Hunk #12 FAILED at 770.
Hunk #13 FAILED at 986.
Hunk #14 FAILED at 1049.
Hunk #15 FAILED at 1147.
Hunk #16 FAILED at 1157.
Hunk #17 FAILED at 1307.
Hunk #18 FAILED at 1404.
Hunk #19 FAILED at 1430.
Hunk #20 FAILED at 1447.
Hunk #21 FAILED at 1461.
Hunk #22 FAILED at 1529.
Hunk #23 FAILED at 1549.
Hunk #24 FAILED at 1656.
Hunk #25 FAILED at 1690.
21 out of 25 hunks FAILED -- saving rejects to file libs/libmythtv/mpegrecorder.cpp.rej

```

and

```
mythbox@coral:~/sources/mythtv/release-0-21-fixes/mythtv$ patch -p0 -i ../../**DeviceReadBuffer-polltimeout.2.patch** 
patching file libs/libmythtv/DeviceReadBuffer.h
patching file libs/libmythtv/DeviceReadBuffer.cpp
Hunk #1 succeeded at 89 (offset -1 lines).
Hunk #2 FAILED at 108.
Hunk #3 succeeded at 119 (offset -6 lines).
Hunk #4 succeeded at 232 (offset -8 lines).
Hunk #5 succeeded at 252 (offset -8 lines).
Hunk #6 succeeded at 281 (offset -8 lines).
Hunk #7 succeeded at 307 (offset -8 lines).
Hunk #8 succeeded at 316 (offset -8 lines).
Hunk #9 succeeded at 396 (offset -8 lines).
Hunk #10 succeeded at 412 (offset -8 lines).
1 out of 10 hunks FAILED -- saving rejects to file libs/libmythtv/DeviceReadBuffer.cpp.rej

```

So the question is, how do I get the patches to apply? SVN version says 19395.

Thanks in advance!

I looked at the tickets and the poster there referenced his patches as working with svn version r19054 but TRUNK... try that version.

---

### Post by zoiks on 2008-12-19
> **managementboy said:**
> I looked at the tickets and the poster there referenced his patches as working with svn version r19054 but TRUNK... try that version.

Thanks.

OK I think that explains it. The patches only work with an earlier SVN rev than the rev I have (but mythbuntu fixes seems to be 18722). I suppose I could try to revert but I imagine that will be fruitless.

---

### Post by blackoper on 2008-12-23
[http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=351743;page=2;sb=post_latest_reply;so=ASC;mh=25;list=mythtv]("http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=351743;page=2;sb=post_latest_reply;so=ASC;mh=25;list=mythtv")

that thread shows you how to patch fixes for hdpvr

---

### Post by zoiks on 2008-12-24
OK, for those interested, I got this working great. Here's what I did: 

(Warning: This is a sledgehammer approach to getting HDPVR to work with 0.21-fixes in mythbuntu; In general, this will ruin the consistency you get with standard mythbuntu releases and packages. Some things like MythbuntuControlCenter and other stuff may not work right, and future myth updates from repos will clobber what you do here.)

First off, some preliminary things.

1] Compiled and installed hdpvr (as directed in the wiki above, [http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR) ). Made sure I could capture H.264 from /dev/video0 (played back with VLC - mplayer crashed on it.) No problems here. The command to get the source code was

```
hg clone http://hg.jannau.net/hdpvr/

```

2] Compiled and installed channel changer (called mythchanger) available here:

[https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

No troubles compiling/running. I am using a Motorola DCH3416 and found the correct usage is "mythchanger -f 7 -c <num>". Using "-f 6" kinda works (is much faster, for one), but causes the cable tuner to go into some guide mode on its video output whenever a channel is "changed" to the channel it's already on.

3] Changed the settings on the Motorola box to output only 720p and set the 4:3 override to "Off". (The DCH3416 manual was found by googling.) The appropriate settings mode was entered by hitting the "menu" button on the box just after power it *off*.

4] Applied the following database instructions to change the mythconverg database (from [http://www.gossamer-threads.com/lists/mythtv/users/351743#351743](http://www.gossamer-threads.com/lists/mythtv/users/351743#351743) ), after opening the database with "mysql -umythtv -p<password> mythconverg" :

```
INSERT INTO profilegroups SET name = 'HD-PVR Recorders', cardtype =
'HDPVR', is_default = 1;
INSERT INTO recordingprofiles SET name = 'Default', profilegroup = 13;
INSERT INTO recordingprofiles SET name = 'Live TV', profilegroup = 13;
INSERT INTO recordingprofiles SET name = 'High Quality', profilegroup = 13;
INSERT INTO recordingprofiles SET name = 'Low Quality', profilegroup = 13; 

```

***Note that the link above also provides the necessary steps to take if you ever want to use the same database for the trunk (or future 0.22) or any other version of mythtv!*** If you don't feel comfortable, you might want to back up your database.

Now, for the mythtv source code stuff:

5] Checked out the fixes SVN branch. My revision at the time was 19401 (which is where I'll keep it for now. Notably my mythbuntu-shipped mythtv is at 18722).

6] Compiled to make sure all needed header libraries were installed. Several libXXX-dev installed from repositories. (I can't remember them all.) My configure line looked like

```
./configure --disable-distcc --enable-hdpvr --enable-opengl-video --enable-opengl-vsync --enable-libfftw3 --enable-libfaad

```

Notably, I had to add libfaad explicitly because otherwise sound on mythtv would puke.

7] Applied the patch found here

[http://www.mentasm.com/mythtv/hdpvr_mythtv-fixes_r18528v3.diff.gz](http://www.mentasm.com/mythtv/hdpvr_mythtv-fixes_r18528v3.diff.gz)

This patch applied cleanly, but a test compile revealed an error related to undeclared "cout". The offending lines were just commented out, like so

[in file h264utils.cpp]
```
    //    if (log2_max_frame_num < 1)
    //    {
    //        VERBOSE(VB_IMPORTANT, "KeyframeSequencer::decode_Header: "
    //                "SPS has not been parsed!");
    //        return;
    //    }

```

After that compilation was good.

8] Applied the two patches found here

[http://www.gossamer-threads.com/lists/mythtv/users/351743#351743](http://www.gossamer-threads.com/lists/mythtv/users/351743#351743)

hdpvr-ac3.patch applied without issue.

DeviceReadBuffer-polltimeout.patch had one hunk fail, namely this one

```
***************
*** 103,108 ****
      {
          VERBOSE(VB_IMPORTANT,
                  LOC_ERR + QString("Start(): pthread_create failed.") + ENO);
          error = true;
      }
  }
--- 108,115 ----
      {
          VERBOSE(VB_IMPORTANT,
                  LOC_ERR + QString("Start(): pthread_create failed.") + ENO);
+ 
+         QMutexLocker locker(&lock);
          error = true;
      }
  }


```

So in the file DeviceReadBuffer.cpp, I manually replaced

```
    pthread_create(&thread, NULL, boot_ringbuffer, this);                 

```

which I believe was at line 107, with the following lines

```
    if (pthread_create(&thread, NULL, boot_ringbuffer, this) != 0)
      {
        VERBOSE(VB_IMPORTANT,
                LOC_ERR + QString("Start(): pthread_create failed.") + ENO);
	QMutexLocker locker(&lock);
        error = true;
      }

```

After that, compile was good to go.

9] Did sudo make install, but but forgot to change the default location. Therefore, everything went into /usr/local/bin instead of /usr/bin. Fixed this by moving the files into /usr/bin instead.

10] Mythbackend still started as a service correctly via /etc/init.d/mythtv-backend, so I didn't have to change that.

But mythfrontend would not autostart after that, so I changed the file ~/.config/autostart/mythtv.desktop (which is a symlink to /usr/share/applications/mythtv.desktop) so the Exec line says

```
Exec=/usr/bin/mythfrontend.bak --service

```

explicitly. The file mythfrontend.bak is a symlink to /usr/share/mythtv/mythfrontend.sh, which comes from mythbuntu, and sets up logfiles and such.

11] After that, had a couple minor issues with themes and mythplugins (mostly just to make sure they were in the correct directories, since I didn't change the default locations from the SVN source).

All in all, everything is working great, with the only two flaws I've found being an initial rough patch whenever the HD-PVR first starts recording (a long pause and a bunch of lost frames and screwed up audio) and a couple of the visualizers for mythmusic are screwed up. The rough patch in the HDPVR only lasts the first 10 seconds or so, and only occurs when the HDPVR first starts to encode video. But it doesn't crash myth or anything so I can live with it. After many hours of use, live TV, recordings, etc., it's been very stable for me.

The plan is to sit on this version of myth until 0.22 trunk becomes a release. Hopefully by then, resolution changes will be supported.

**Note:** I'm writing all this from memory, so I may have missed a step or two, though I don't think so. It did take a while to figure all this out. I now have an HDHomeRun providing 2 inputs, and a HD-PVR providing all the encoding for the content that is encrypted from the cable company.

Many special thanks to the developers who created these patches, drivers, etc., with great coding skills. Thanks also to Yeechang Lee who pointed me in the right direction on the mailing list.

These mailing list threads provide relevant information on all this as well:
[http://www.gossamer-threads.com/lists/mythtv/users/359956](http://www.gossamer-threads.com/lists/mythtv/users/359956)
[http://www.gossamer-threads.com/lists/mythtv/users/352286](http://www.gossamer-threads.com/lists/mythtv/users/352286)
[http://www.gossamer-threads.com/lists/mythtv/users/351743](http://www.gossamer-threads.com/lists/mythtv/users/351743)

Edit: I forgot to mention that I of course had to recompile the plugins due to version mismatch. Hopefully if you can get this far, you can recompile the plugins yourself. :)

---

### Post by blackoper on 2008-12-26
ok I've got everything patched and ready to go. I'm at step 9

so should I use this to configure to avoid putting the svn in the wrong directory

./configure --prefix=/usr/ --enable-hdpvr --enable-xvmc --enable-opengl-video --enable-opengl-vsync --enable-libfftw3 --enable-libfaad --enable-lirc

and will I need to remove any of the myth .21 install that came preinstalled with mythbuntu 8.10 before I do the make install?

---

### Post by zoiks on 2008-12-26
> **blackoper said:**
> ok I've got everything patched and ready to go. I'm at step 9

so should I use this to configure to avoid putting the svn in the wrong directory

./configure --prefix=/usr/ --enable-hdpvr --enable-xvmc --enable-opengl-video --enable-opengl-vsync --enable-libfftw3 --enable-libfaad --enable-lirc

and will I need to remove any of the myth .21 install that came preinstalled with mythbuntu 8.10 before I do the make install?

Glad to see you got through the tougher steps (patching and compiling). I hope you can let us know how it turned out for you.

- Your use of --prefix I think is correct; that should put the binaries in the correct place (as well as themes, etc.). If I were to do this again I think I'd do it that way.

- I honestly don't know if you should remove any of the myth packages that came with mythbuntu. On the one hand, it would make your setup a little cleaner, in the sense that you didn't just clobber the binaries that were set up by the distro, and it would keep your apt databases more consistent. On the other hand, removing mythtv packages may cause other packages or elements to be removed that you want to keep.

The way I'm doing it (and it's just me) is I go ahead and clobber the binaries mythbuntu put in for me, knowing that in the worst possible case I'd would just have to force a reinstall of the mythtv packages, overwriting the binaries I put in there myself. Of course, in that case I'd also have to fix the mythconverg database (from what I did in step number 4) using the instructions provided in that link from the mailing lists. To that end, from the mailing list archives, we have from Mark Buechler:

```
If the above changes are made, and at some later time you decide to update
to a newer MythTV release or to trunk, when MythTV updates to schema 1223,
it will fail and you'll have to manually change your schema in the database
to 1223 to get past it:

update settings set data = 1223 where value = 'DBSchemaVer' and data = 1222;

```

Of course, if you clobber the existing binaries you can't allow mythbuntu to update the myth packages because you'll then be re-clobbering the binaries with the distro stuff. For myself, I'm just not going to update myth packages through apt-get until a future release natively supports the hdpvr.

Cheers.

---

### Post by blackoper on 2008-12-26
Ok good I just wanted to check before I did something that is hard to recover from...

I did every bit of this upgrade from ssh and a putty client from work :) I won't be able to test it until I get home. I started with a basic 8.10 64 bit install with ssh installed and went from there. Took a few hours.

yeah I plan on not upgrading the backend until .22 At that point hopefully a database transition tool will be made for us few that patched to hdpvr (if not I'll manually edit the database).

yeah hardest part for me was remembering how to use the patch function for svn files. had to do a bit of googleing since I hadn't patched something in a while.

also for anyone else trying this some helpful hints:
for getting 19401 version of fixes:
svn co -r 19401 [http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv) 
svn co -r 19401 [http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythplugins](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythplugins) 
svn co -r 19401 [http://svn.mythtv.org/svn/branches/release-0-21-fixes/myththemes](http://svn.mythtv.org/svn/branches/release-0-21-fixes/myththemes) 

command for applying patches from the mythtv directory for final two patches (done from the directory before mythtv for 1st patch):
patch < (location of patch file *.diff)

and for getting most of the required dev packages to compile myth you can consult: [http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy]("http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy")  - you will need to change some of the names to what apt-get tells you on some as this is an old listing

5:53 pm - well everything is now installed and ready to go. I just have to wait till I can get home and test it out. I have to say compiling with an intel quad core is sooo much faster than even a dual core. I compiled mythtv in about 90 seconds with the -j4 option

---

### Post by zoiks on 2008-12-26
Since you bring it up, it's worth reminding that you'll need some good CPU horsepower to play the H.264 recordings from the Hauppauge 1212 HD-PVR. As for my own CPU, it's an Intel E8400 dual core 3GHz chip, with 2 gigs of RAM on the MB. My graphics card is an old nVidia quadro NVS-285 with 128 Megs of RAM, which seems to be performing adequately for me thus far.

In addition, my Hauppauge unit is rev E1. Happily, I didn't have to hook it up to a windows machine to get the firmware installed.

---

### Post by blackoper on 2008-12-26
ok I can confirm it works great. I had to set my motorola 6412 box to output 720p and also turned override option from 480p to off.

For some reason the optical spdif passthrough isn't working so I just ran a coax spdif from my cable box to receiver and have the optical going to hdpvr

I used the simple 6200ch channel change script to control the tv channels and it's working perfectly for me.
All I have left to do now is specify what /dev/# each device gets so they don't change around every boot. Thanks Zoiks for the help

---

### Post by blackoper on 2008-12-27
I am probably going to see if I can patch mythcommflag with this patch: [http://svn.mythtv.org/trac/ticket/5809](http://svn.mythtv.org/trac/ticket/5809) so I can then do commercial cutting of the hdpvr files. script for it is here: [http://www.mythtv.org/wiki/index.php/User:Iamlindoro](http://www.mythtv.org/wiki/index.php/User:Iamlindoro)

I'll just manually edit mythcommflag main.cpp tonight and then recompile and see if it works (after backing it up) :)

---

### Post by trimtab on 2008-12-27
Zoiks, what initial version of Mythbuntu are you using AND what are the specs of your Myth box? 

CPU?
CLOCK RATE?
MEMORY?
VIDEO CARD?
Disk Storage and type?
It appears you are using only an HDHomerun and the HDPVR, any other recorders?

Thanks in advance.

---

### Post by blackoper on 2008-12-27
zoiks posted some of that stuff earlier
> **zoiks said:**
> Since you bring it up, it's worth reminding that you'll need some good CPU horsepower to play the H.264 recordings from the Hauppauge 1212 HD-PVR. As for my own CPU, it's an Intel E8400 dual core 3GHz chip, with 2 gigs of RAM on the MB. My graphics card is an old nVidia quadro NVS-285 with 128 Megs of RAM, which seems to be performing adequately for me thus far.

In addition, my Hauppauge unit is rev E1. Happily, I didn't have to hook it up to a windows machine to get the firmware installed.


my hardware and software is listed here:
[http://mythtv.org/wiki/index.php/User:Blackoper]("http://mythtv.org/wiki/index.php/User:Blackoper")

---

### Post by zoiks on 2008-12-27
> **trimtab said:**
> Zoiks, what initial version of Mythbuntu are you using AND what are the specs of your Myth box? 

CPU?
CLOCK RATE?
MEMORY?
VIDEO CARD?
Disk Storage and type?
It appears you are using only an HDHomerun and the HDPVR, any other recorders?

Thanks in advance.

Initial version of Mythbuntu: 8.10 (after upgrading from 8.04).

CPU = Intel E8400 dual core
CLOCK RATE = 3GHz
MEMORY = 2Gigabytes
VIDEO CARD = Nvidia Quadro NVS 285 with 128 MB RAM
Disk Storage = 3x WD GP drives, 750Gigs each, software raid5 array (1.5 TB net storage)
HDHR and HDPVR are the only inputs I'm using (3 total).
I still have installed a PVR-500 (dual tuner) but I'm no longer using them. I'm sure they'd record if I reconfigured them in Myth.
TV = Sharp Aquos 52"

FWIW, my CPU is typically running at 75% of total capacity while playing the hdpvr files.

---

### Post by zoiks on 2008-12-27
> **blackoper said:**
> zoiks posted some of that stuff earlier



my hardware and software is listed here:
[http://mythtv.org/wiki/index.php/User:Blackoper]("http://mythtv.org/wiki/index.php/User:Blackoper")

Jeezus H Christmas dude, you sure got a lot of hardware in your entertainment center!

BTW, your link to "link patch .21 fixes with hdpvr" goes to [www.example.com](www.example.com). Presumably you meant to point to this thread. Hey, do you want to write a wiki for this?

---

### Post by blackoper on 2008-12-27
yeah that projector is 150 pounds by itself.. beginning to warp the darn thing. My network rack area is pretty packed with stuff too.

I'll go ahead and create a new wiki entry and step by step it.. problem is the myth devs don't seem that happy with the hack as you noticed in the mythtv-user thread. They may just delete it after it's done :)

---

### Post by blackoper on 2008-12-27
Here is the wiki entry on mythtv.org/wiki

[http://mythtv.org/wiki/index.php/Patch_myth.21-fixes_for_hdpvr_on_Ubuntu_8.10]("http://mythtv.org/wiki/index.php/Patch_myth.21-fixes_for_hdpvr_on_Ubuntu_8.10")

go ahead and edit that page at will. I'm sure I missed some stuff. Also can you send an email to the list about it. I don't think I have any emails currently subscribed as I just browse gossamer threads

*Edit: Reread that thread and this wiki entry is going to annoy Robert Macnamara. Anyone that uses this better know how to manually revert your database for .22. I also added a larger warning

---

### Post by zoiks on 2008-12-28
Heh, I understand now why Robert's response to my first message was "the only way to support an HDPVR is to go with 0.22 trunk."

I was thinking of going with trunk but saw nothing but dire warnings of apocalypse, so I held back. Thankfully, some people have backported the hdpvr patches to -fixes. It made things work great for me, and I was hoping for others, too, so I don't see why that has to be a bad thing. My household's WAF has improved tremendously now that I don't make my wife watch some of her favorite stuff in SD when it's available in HD.

Anyway, I'm guessing your wiki will get yanked.

(I just took a look at the wiki. Looks nice!)

---

### Post by blackoper on 2008-12-28
anyone got any ideas on how to accomplish commercial cutting with this. I tried an older script that I put on the wiki. It can cut the video according to the cutpoints, but the audio was totally off.

Macnamara as expected has declined helping with getting the commercial cutting script working... oh well.

---

### Post by blackoper on 2009-01-12
Well after some usage in .21, the video generated by hdpvr works fine in myth, but editing in things like Avidemux has some problems.
The video is all out of order due to something with the way it's being generated by myth. I've got a workaround of using some windows conversion tools but I'm going to give .22 svn a try on my backup dualcore server and see if the out of order issue is still present.

---

### Post by trimtab on 2009-04-01
Okay, I've just built an 0.21-fixes "FrankenMyth" that includes the following capabilities:

- HD-PVR
  HD-PVR recording/playback capabilities in the 0.21-fixes branch.

- HDHomerun multirec support
  The HDHomerun can record multiple channels on a single tuner. In my area the cable company provides FOX and CBS HDTV on a single multiplex and ABC and NBC on another. Now Myth via the HDHomerun can record all the HDTV off the networks in primetime using only 2 tuners.

- VDPAU video playback
  Hardware accerlerated video deinterlacing support on a Nvidia 9500 card. This makes H.264 playback "comfortable" on my system.

I'll report back on if it all works. I need to do at least a week of testing. My set up also has a PVR500 dual-channel recorder that works.

Zoiks instructions made this a lot easier. Thx!:-)

---

### Post by trimtab on 2009-04-16
It basically "all works" with a few gotchas.

HDHomerun multirec usually works, but very occasionally gets confused and records the same stream as 2 different channels.

The HD-PVR requires that you let it settle with a sleep 1 after a channel change via firewire when recording. If you don't, your recordings will start with audio static. And that static can last from a second to minutes. Even with the 1 second sleep, you get a different more pleasant side effect: The audio will drop out about a second into the recording and return at the first keyframe.... usually within 10 seconds.

The HD-PVR itself has a tendency to lose and restart encoding sometimes  on high def channels. In playback this causes a lose of video and audio for a second, but the recording continues to play while Myth knits the video together in a slightly distorted way. . You can actually see the HD-PVR blue lights go off and back on during recording when this happens. (This is a known HD-PVR issue that Hauppauge has yet to solve. MythTV appears to be re-starting the stream when the HD-PVR drops it.)

HD-PVR recordings can also make MythFrontend barf occasionally on playback leaving a blue screen and a message about losing video playback. The easiest way around that is to just skip ahead of spot in the video file that caused the frontend to stop streaming video. This may be VDPAU/HDPVR combination problem since all my playback is via VDPAU now.

Even with these HD-PVR recordings are 1000% more reliable than Firewire and the file sizes are a lot smaller. I now just use Firewire to change channels.

So basically it all works and this is where I'll wait probably until an 0.22-fixes is released. I expect 0.22 to very buggy when it is initially released given all the major changes and improvements that are going into it.

:popcorn:

---

### Post by jyavenard on 2009-04-25
Hi.

For those wanting a HD-PVR support in 0.21 without too much hassle.

I've created packages that include VDPAU supports, as well as a few improvements to mythtv.

To get HDPVR supports, you need to compile however as I didn't build hdpvr support by default.

But it's rather easy.
Activate my "testing" repository
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

To compile with HD-PVR support.
(instructions are there [http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/4/26_Testing___MythTV_20450-2.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/4/26_Testing___MythTV_20450-2.html)) but I copy it here one more time


#First install all the dependencies you need to compile mythtv.
$ sudo apt-get build-dep mythtv
$ cd mythtv-testing
$ dpatch apply-all


#If on Intrepid or Hardy, do:

$ dpatch deapply 30_python26_transition


#Now compile

CFLAGS="-g -O2 -fPIC -DPIC" ./configure --compile-type=debug --prefix=/usr --runtime-prefix=/usr --enable-lirc --enable-audio-alsa --enable-audio-oss --enable-audio-jack --enable-dvb --enable-ivtv --enable-firewire --enable-joystick-menu --enable-opengl-vsync --with-bindings=perl --enable-opengl-video --enable-ffmpeg-pthreads --enable-vdpau  --enable-xvmc --enable-xvmc-vld --enable-xvmc-pro --enable-glx-procaddrarb --enable-libfaad --enable-libfaac --enable-libmp3lame --enable-libxvid --enable-libfftw3 --enable-hdpvr

$ make

$ make install


Before you run it, make sure you read:

[http://mythtv.org/wiki/Patch_myth.21-fixes_for_hdpvr_on_Ubuntu_8.10](http://mythtv.org/wiki/Patch_myth.21-fixes_for_hdpvr_on_Ubuntu_8.10)

Obviously ignore how to download, patch and compile mythtv as I’ve done it for you.


You need to modify your database schema. This will break future automatic update.

You’ve been warned!

---

### Post by brianafischer on 2009-05-11
I am considering an Acer Aspire Revo for a frontend in conjunction with a HD-PVR backend.  I would like to use Ubuntu Jaunty 9.04 for both PCs.  Has anyone tested this method on Januty?  Anyone have any comments or advice?

Thanks!

---

### Post by bob1234 on 2009-05-25
A special thanks to jyavenard and everyone.

I think I need some help. I purchased a HD-PVR and have been waiting to use it. When I saw this guide/repository I decided to give it a try. I started with a clean install.

I added the repositories, updated everything, Compile and install hdpvr driver, Setup LIRC changer, Modify the database, downloaded the mythtv source from jyavenard's testing repository, apt-get all dependencies, uncommented HD-PVR patch, patched the mythtv, set my CFLAGS, stopped backend, "make" then "make install", start backend, setup tuners.

Once I am complete, several things are broken. The system will not show livetv and does not seem to be able to activate the HD-PVR. I know that the HDPVR is working because I can capture video from it using the cat command. I can no longer launch mythfrontend from the menu and have to use a terminal. I can no longer launch myth backend setup from menu and must use terminal. I must also manually stop the backend before doing this.

Any help would be greatly appreciated.

The only step I can not fingure out is the mythweb step where I am supposed to copy the new mythweb data from the fixes plugins and edit the mythweb.conf file. Would this break everything. How do I apply this step...

---

