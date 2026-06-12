---
title: "video capture device - no sound with VLC, poor video with mplayer"
date: 2013-11-30
forum: Multimedia Software
---

### Post by squakie on 2013-11-30
First off just let me say I don't know squat about audio and video, so if I'm being dumb please let me know and explain - thanks!

I have a DVC-100 capture device, capturing VHS tapes to disk.  I had the same luck with it in Mint as I have in Ubuntu, so at least I know it's an "operator error" and nothing with the OS such as a driver or something.

I found a site for using this device with Mint using mplayer via the command line.  That works, but the video is very jittery, dropping frames and in the end not syncing with the sound - the sound is way ahead of the video.  I don't know anything about mplayer, and I've tried reading the docs for it and mencoder (is it even in use now or did something take its' place?).  I really don't understand what the heck to do versus trying to read the docs.  When I close out the mplayer window and return to the terminal window, there are a lot of messages about the video buffer being full and dropped frames.

So, I read another thread that said to use VLC.  I've been trying just play for now without actually recording to disk yet, but I have no sound.  I had to set the frame rate up to 60 as the default is so low that, well,  "it ain't pretty".  I know that the sound should be on hw:2.0 but I don't a place to specify that in VLC.

Any help for a lost old fool would be appreciated.

---

### Post by squakie on 2013-12-01
I found a many years old post in reply to my old userid where user rmt1947 was helping me with an EasyCap DC60 -one of the ones that actually works in Ubuntu instead of the one I have now.  The command that worked then was:

1>mc.out 2>mc.err mencoder tv:// -tv driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=30:adevice=/dev/easysnd1:amode=1:forceaudio:immediatemode=0 -msglevel all=9 -ffourcc DX50 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=15 -vf pp=lb,scale=640:480 -oac mp3lame -o test.avi
I can't make heads ot tails of any of this stuff.  My video from the Dazzle DVC-100 is /dev/video0, while the sound I just know is specified as 2,0 with something like hdw: or some such thing in fromt of it in other programs.

Can anyone help me adapt this to the DVC-100?  I've read the man page for mencoder but I don't know anything about video/audio so I don't know what the heck it is talking about ;)

---

### Post by squakie on 2013-12-03
Well, forget it.  Couldn't get this working in the time I needed.  Erased everything, installed a 30gb Windows XP installation and used the rest to reinstall 13.04.  I only had Ubuntu on it before so I didn't see a way to shrink an Ubuntu installatioin.

Note to those who may try something like this:  BEFORE you do it, back up everything you may need.  This is the SECOND time I got in a hurry and didn't think.  After installation, Yahoo wanted my login again - I didn't know the password as it was in my Thunderbird mail before.  Tried asking for a reset - an email was sent to my "backup" address, which just so happens was deleted by the provider because of lack of usage.  A tiring and really not too amusing 8 1/2 hours later I finally found a password that worked.  Not to mention the other "stuff" I had saved under Ubuntu that I hadn't back up (oh fun).  So, when you see posts saying to back up before you start, do it.  I have many years of technical experience in IT and yet I blew everything I needed away.

---

