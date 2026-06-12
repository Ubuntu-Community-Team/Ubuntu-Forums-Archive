---
title: "Mythbuntu 9.10 Video"
date: 2009-11-08
forum: Mythbuntu
---

### Post by amlino on 2009-11-08
I recently upgrade 9.04 to 9.10 and I am unable to play .avi (DIVX) videos on 9.10.

The video command line I have is:

mplayer -fs -zoom -quiet -vo xv %s 

When I choose a video to play, it seems the video is starting based on the log below. There is only a warning message... The screen gets blank and does not play the video and there is no audio as well.

Playing /mythtv-rec/videos/BABY_LOONEY_TUNES_VOL4.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  720x544  24bpp  29.970 fps  1801.7 kbps (219.9 kbyte/s)
Clip info:
 Software: transcode-1.0.2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 544 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.32:1 - prescaling to correct movie aspect.
VO: [xv] 720x544 => 720x544 Planar YV12  [fs] [zoom]
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
GNOME screensaver enabled

Exiting... (Quit)


Any ideas?

Thanks,
Marcello

---

### Post by rubrboots on 2009-11-09
I am having a similar problem. I have always used mplayer to play videos in previous versions of myth, since it is much better than the internal player. I can not play any video file though mplayer now. I have tried to use the internal player, some videos play well, while others play but I completely lose control of the keyboard and have to do a hard reboot.
?????

---

### Post by geolizardo on 2009-11-09
I don't have a fix to your problem, but I have had the keyboard control issue problem happen as well.  Instead of doing a hard boot, I have been using the remote control to stop the video.  It somehow still works fine.  
Also, I did a CTRL-ESC to bring up the Ubuntu applications menu.  Then I was able to ALT-TAB back to the mythfrontend that was running the video and then I had keyboard control back.  That move isn't going to impress the girls, but it worked for me.

---

### Post by rubrboots on 2009-11-09
Thanks geolizard, CTRL-ESC is not working for me, and I have not bothered to set my remote up just yet. However I have found that I can ssh into that machine and kill the frontend. 

amlino: this was posted by **SiHa** on another thread and it worked for me.
To disable storage groups for Videos

> Backend setup > Storage Directories. Select 'Videos' and delete '/var/lib/mythtv/videos'. The entry will default to '/'.

When exiting the setup, it will complain that '//.test/' cannot be written, select 'No thanks, I know what I'm doing'.

---

### Post by SiHa on 2009-11-09
> **rubrboots said:**
> I am having a similar problem. I have always used mplayer to play videos in previous versions of myth, since it is much better than the internal player. I can not play any video file though mplayer now...

From the Mythvideo 0.22 Transition Guide: [[COLOR="Blue"]_here_[/COLOR]](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)
> External Video Players (mplayer, xine, VLC) will not work with videos hosted on an SG

And a fresh install of 9.10 defaults to using SG's. Even if you setup nfs shares, if they point to the default dir (/var/lib/mythtv/videos), then Myth will attempt to stream them via the SG, and ignore the locally mounted share. So if you want to use mplayer, you'll have to either disable the SG, or store amd mount the nfs share somewhere else.

Edit: The nfs bits assume that you have a remote frontend, I forget that many people don't!. The point is that Myth will attempt to access videos via the SG in preference to a locally available file on the same path.

---

### Post by NTolerance on 2009-11-28
> **SiHa said:**
> From the Mythvideo 0.22 Transition Guide: [[COLOR="Blue"]_here_[/COLOR]](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)


And a fresh install of 9.10 defaults to using SG's. Even if you setup nfs shares, if they point to the default dir (/var/lib/mythtv/videos), then Myth will attempt to stream them via the SG, and ignore the locally mounted share. So if you want to use mplayer, you'll have to either disable the SG, or store amd mount the nfs share somewhere else.

Edit: The nfs bits assume that you have a remote frontend, I forget that many people don't!. The point is that Myth will attempt to access videos via the SG in preference to a locally available file on the same path.

In my case I'm running an install of 9.04 that was upgraded to 9.10.  There are no Mythvideo storage groups defined and all my videos are in /var/lib/mythtv/video as they always have been.  Yet I still can't use mplayer.  Is there a surefire way to make sure the storage groups are not being used in Mythvideo?

---

### Post by mjezell on 2009-11-29
Take a look at the [[COLOR=Blue]Mythvideo page[/COLOR]]("http://www.mythtv.org/wiki/MythVideo") on the MythTV Wiki.  I think some of your problems are explained there.  Hope this helps.

---

### Post by rsay on 2009-11-29
I am having the same problem. I haven't figured out the cause yet. One workaround that I discovered is just to switch to the internal player.

Replace "mplayer -fs -zoom -quiet -vo xv %s" with "Internal" Unfortunately, the internal player doesn't work as efficiently for me as mplayer and it causes some jumps and skips when I playback on my Acer aspire revo. 

If it saves you some time, you don't need to kill the frontend, just mplayer. SSH works fine for that. You can also just switch to another shell and issue the command from the same machine. Ctrl-alt-F3 for example. 

What I find odd about this bug is that I can sometimes go to the command line and play the same video with the same mplayer settings and it works. Other times, I get the hang. Also, it doesn't always hang at the same exact instant in the video. Sometimes it plays a few seconds first.  

There is something that is just a little bit odd about the way things get launched from inside mythtv in karmic. I used to start Frets on Fire from inside mythtv, but now I have to exit myth and start the program from a desktop launcher (using the same command that used to work inside myth). I have some vague suspicions that a pulseaudio problem could be behind this, but I don't know how to track down the source of the problem.

---

### Post by rsay on 2009-11-29
I am running mythtv 0.21 fixes on Karmic btw. This does seem to have some relationship to audio. I can get mplayer to run from inside mythtv with:
```
mplayer -fs -zoom -quiet -vo xv -ao oss %s
```

Here is a strange observation I made about this bug.

1. Go to the command line with mythtvfrontend stopped.
   ```
mplayer -ao pulse somefile.avi
``` Works
   ```
mplayer -ao alsa somefile.avi
``` Works
   ```
mplayer -ao oss somefile.avi
``` Works


2. Start mythfrontend (in a window if necessary), then from command line:
   ```
mplayer -ao pulse somefile.avi
``` Hangs
   ```
mplayer -ao alsa somefile.avi
```  Hangs
   ```
mplayer -ao oss somefile.avi
``` Works

As soon as mythfrontend is exited, all the commands in #1 work again. Somehow, mythfrontend is blocking mplayer! I'm going to file a bug report now.

EDIT - Bug report filed. [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/490124]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/490124")

You guys will probably at least want to subscribe to the bug and possibly add information about your own configurations.

---

### Post by oweddle on 2009-11-30
I apologize if this isn't the right place to post this. I am a noob on these forums. Any help would be appreciated...

I had Mythtv 0.21 on Ubuntu 9.04. I upgraded to Ubuntu 9.10 which automatically updated my Mythtv to 0.22. 
The only major problem I have now is MythVideo will not see any new movies I add. It shows all my old movies already on mythvideo, and even lets me update the info and covers on them. But It will not add any new movies I put in my movies folder.
I am guessing it could be an issue with MySQL?

If someone can point me in the right direction, I would appreciate it.

Thank you
Oliver Weddle

---

### Post by tgm4883 on 2009-11-30
> **oweddle said:**
> I apologize if this isn't the right place to post this. I am a noob on these forums. Any help would be appreciated...

I had Mythtv 0.21 on Ubuntu 9.04. I upgraded to Ubuntu 9.10 which automatically updated my Mythtv to 0.22. 
The only major problem I have now is MythVideo will not see any new movies I add. It shows all my old movies already on mythvideo, and even lets me update the info and covers on them. But It will not add any new movies I put in my movies folder.
I am guessing it could be an issue with MySQL?

If someone can point me in the right direction, I would appreciate it.

Thank you
Oliver Weddle

It would have been much better to start a new thread for this.

That being said, hit M then scan for changes.

---

### Post by oweddle on 2009-12-01
> **tgm4883 said:**
> It would have been much better to start a new thread for this.

That being said, hit M then scan for changes.


That's why I mentioned I'm a noob and asked to be pointed in the right direction. I couldn't find where to start a new thread.
Well I feel like an idiot now, but scanning for changes fixed it. The other versions automatically updated the movies list. Didn't realize the change.

Thank you tmg4883

---

### Post by NTolerance on 2009-12-05
> **rsay said:**
> I am running mythtv 0.21 fixes on Karmic btw. This does seem to have some relationship to audio. I can get mplayer to run from inside mythtv with:
```
mplayer -fs -zoom -quiet -vo xv -ao oss %s
```

Here is a strange observation I made about this bug.

1. Go to the command line with mythtvfrontend stopped.
   ```
mplayer -ao pulse somefile.avi
``` Works
   ```
mplayer -ao alsa somefile.avi
``` Works
   ```
mplayer -ao oss somefile.avi
``` Works


2. Start mythfrontend (in a window if necessary), then from command line:
   ```
mplayer -ao pulse somefile.avi
``` Hangs
   ```
mplayer -ao alsa somefile.avi
```  Hangs
   ```
mplayer -ao oss somefile.avi
``` Works

As soon as mythfrontend is exited, all the commands in #1 work again. Somehow, mythfrontend is blocking mplayer! I'm going to file a bug report now.

EDIT - Bug report filed. [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/490124]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/490124")

You guys will probably at least want to subscribe to the bug and possibly add information about your own configurations.

Thanks rsay, your fix using OSS works well.

---

### Post by quasifly on 2009-12-06
> **tgm4883 said:**
> It would have been much better to start a new thread for this.

That being said, hit M then scan for changes.

When should I hit M? On what screen?

Thanks

---

### Post by SiHa on 2009-12-06
When you are in the Watch Videos screen: Media Library -> Watch Videos -> Press 'M'

---

### Post by kubug on 2009-12-30
> **oweddle said:**
> I apologize if this isn't the right place to post this. I am a noob on these forums. Any help would be appreciated...

I had Mythtv 0.21 on Ubuntu 9.04. I upgraded to Ubuntu 9.10 which automatically updated my Mythtv to 0.22. 
The only major problem I have now is MythVideo will not see any new movies I add. It shows all my old movies already on mythvideo, and even lets me update the info and covers on them. But It will not add any new movies I put in my movies folder.
I am guessing it could be an issue with MySQL?

If someone can point me in the right direction, I would appreciate it.

Thank you
Oliver Weddle

When inside your movie browser (where all your movies are displayed) press M (for menu) and select "Scan for changes"... voila!


Edit: Ok ok.. I am about 3 weeks late. I guess one should go ALL THE WAY to the end of the thread before adding ones comment. Sorry.

---

### Post by kubug on 2009-12-30
> **NTolerance said:**
> Thanks rsay, your fix using OSS works well.

I had the same issue. I couldn't play some .mkv files with the internal player and mplayer seemed to just stop and sit there (forwarding with arrow keys would just move me up some frames and then it would sit again). 

I did not use SG (Storage Groups) but rather stream the movies from another server via NFS. 

What finally worked for me was this commant that I added to the movies that didn't play properly in the internal player:

> mplayer -fs -zoom -vo xv -ao alsa %s 

The -vo option could also be vdpau if you have the necessary hardware.

---

