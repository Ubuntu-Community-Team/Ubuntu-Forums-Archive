---
title: "playing a 720p h264 mkv file in mplayer"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by barnjo on 2007-01-27
Hi all, I have a 720p mkv file encoded using the h264 codec, and cant get smooth playback.

I have compiled the latest version of mplayer from source.

When I start playing the file its fine but about 30secs in it basically stops playing with mplayer complaining theres too much memory in the buffer.

I have an AMD Athlon 2400+ running at 2GHz, 1GB RAM and an Nvidia GeForce FX 5600 256MB RAM.

If it is also useful knowing I have the latest nVidia beta drivers (v9746) and have beryl SVN installed.

Any help getting smooth playback would be appreciated, cause I don't really want to boot into WinXP just to watch some video.

Thanks

---

### Post by yabbadabbadont on 2007-01-27
Are you sure that the video will play smoothly in XP on that same machine?  I have an AthlonXP 2800+ and it has trouble keeping up with 720p videos...  If it does play smoothly in XP, then I wonder if the player you use there is silently dropping frames?

---

### Post by shirilover on 2007-01-27
Have you tried to play the file when not using beryl?
Xv video output has problems with beryl.

---

### Post by raphoun on 2007-01-29
In Windows XP there is CoreAVC for playing x264 720/1080p in linux Mplayer is suppose to be the best but less than CoreAVC.
I can play my 720p x264 in XP with CoreAVC but in mplayer I cant get smooth playback too. 

Because of this I have to keep Windows on my computer...:( 

P.S: Try without beryl

Raphaël

---

### Post by twidget on 2007-02-08
I've been trying the same thing in xubuntu with a 1.5ghz p4 and  an fx5200. It'll play just fine then get jerky and/or miss subtittles for a bit and then go back to playing normaly. ive got a cpu monitor running and the weird thing is that most of the time it doesnt show that much load. Every once in a while though it hits 100% and stays there for a few seconds.Looks kinda like a bug to me. is there an alternate codec for playing mkvs out there? if so it would be interesting to see if it behaves the same....

---

### Post by !nkubus on 2007-02-09
I do have the exact same issues.

I've tried feisty, edgy, fluxbuntu, knoppmyth and I always have troubles playing smmothly, for that i'm also oblige to keep a windows dual boot to ply theses files which makes me feel dirty.

Gstreamer have some out of sync issues
mplayer complains there is to much frames dropping
xine is out of sync also
vlc audio is fine the the whole movie is sluggish, and hangs up about each minutes.

if anyone managed to get a smooth playback plese let me know

thanks

---

### Post by twidget on 2007-02-09
i tried 2 regular mkvs from different sources last night and they behaved worse than my high def ones. one tried to play and the froze the system and the other one just froze the system outright. I think theres a problem with the codec. does anyone have any idea which set of codecs provide mkv support?

---

### Post by ss87 on 2007-02-09
I'm dual booting with XP MCE on an ACER core duo 1.66ghz with 1gb ram and I've struggled with these files in ubuntu 6.10 whereas they play perfectly in XP... One of the things that keeps me on it too. Regular MKV playback isn't great either. Any suggestions? Thanks.

---

### Post by lunarmelody on 2007-02-20
I've found it'll run fine in xine... just make sure you download the extra media codecs. :)

---

### Post by shelbydz on 2007-04-15
installing and using xine didn't work for me. the system still drops frames. I think we just need a better codec for X264. 

Any ideas??

---

### Post by paridoth on 2007-04-21
same problem here bad playback and or out of syn videos when trying to play 720p videos, havent even though about messing with 1020 stuff, don't know enough about codecs to sugest anything, just wanted to through my hat into the lot, will subscribe to this thread, hope someone has a sugestion

---

### Post by rama on 2007-05-01
Same problem here. Video runs smoothly @ WinXP with CoreAVC codec. Running @ Kubuntu, I always get the sound 3-4 seconds earlier than the image! Tests on an Athlon 2600+, 1GB ram, nvidia 6200

---

### Post by Thug14 on 2007-05-21
i am facing the same problem,while playing the file in mplayer,it plays fine for  a few minutes and then the video starts lagging the audio by 4-5 seconds

---

### Post by taisao on 2007-07-04
this is the file details where I have try with:

[http://anidb.info/perl-bin/animedb.pl?show=file&fid=329020](http://anidb.info/perl-bin/animedb.pl?show=file&fid=329020)

it seems to work good with MPlayer.

I have to change something to make it work smoothly =>

MPlayer Preferences -> Video -> Available drivers -> "xv    X11/Xv"  (the second items in my list)

source: [http://www.linuxquestions.org/questions/showthread.php?p=285997#post285997](http://www.linuxquestions.org/questions/showthread.php?p=285997#post285997) (post #10)

may it works for you guys too :popcorn:

---

### Post by olejorgen on 2008-02-09
I got a core duo 1.66 too. Haven't got smooth playback yet. Trying to compile mplayer atm.

---

