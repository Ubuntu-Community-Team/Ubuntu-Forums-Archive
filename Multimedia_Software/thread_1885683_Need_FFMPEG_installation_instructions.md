---
title: "Need FFMPEG installation instructions"
date: 2011-11-23
forum: Multimedia Software
---

### Post by PDA1 on 2011-11-23
I'm running Ubuntu 10.04

Previously I've used FFMPEG installation instructions by FakeOutdoorsman (which were really good) but for whatever reason I've not been able to convert videos to a format that'll play completely, successfully with no problem on my iPod 160 G Classic.

Does anyone;

- have complete instructions for installing a current and up-to-date version of FFMPEG for Ubuntu 10.04 that'll include all of the fancy codes like h.264 etc, etc?

- have a good FFMPEG code line for converting videos from mp4 to a format iPod will play?

Please don't reply unless you done the above successfully and know how to do it.  I've read too many posts of people who "know about it but haven't tried it".

Also, I've tried using Handbrake.....but my guess is something is missing from my current installation of FFMPEG that causes Handbrake to convert videos to mp4 (or m4v) but they won't play on my iPod.


Here's the current stuff I have on my machine from FFMPEG- 

Quick@Quick-desktop:~$ ffmpeg -v
ffmpeg version N-34938-g7cdfce4, Copyright (c) 2000-2011 the FFmpeg developers
  built on Nov 17 2011 12:24:48 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-x11grab --enable-libvpx
  libavutil    51. 26. 0 / 51. 26. 0
  libavcodec   53. 34. 0 / 53. 34. 0
  libavformat  53. 20. 0 / 53. 20. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 48. 1 /  2. 48. 1
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Missing argument for option 'v'

---

### Post by ajgreeny on 2011-11-23
I am not certain about how you get the right format for an iPod as I refuse to use any apple gadgets;  far too pricey and locked down for my liking.

However, I use ffmpeg from the ubuntu repos, v 4:0.5.1-1ubuntu1.2, along with the unstripped, or -extra versions of the libav* packages from medibuntu, and can encode to just about anything, as far as I'm aware.  If you are using the standard libav* versions, I think that may be your problem.  Certainly worth looking into.

---

### Post by PDA1 on 2011-11-23
'Couldn't agree with you more about Apple be "locked down".  For all of the worship of the St. Jobs his company sure didn't/doesn't provide much open-source and I simply despise iTunes.  All of the adulation about "iTunes Store" and the trash you can BUY from them is sickening.  Slobbering over Apple stuff is sad.  Now the cult of the iPad is making many disciples!  hat'

Would you also recommend an excellent media player (music, podcasts, videos) that's more flexible than iPod?


But, I really wish Linux would come up with something other than Banshee.....and something that works- the first time.  Gtk-Pod was fun to try and use but did me no good.


Would you please explain to me what you mean about the Libav stuff?  Specifically what you're referring to as the standard Libav codec....or whatever it's called?

Thank you

---

### Post by ajgreeny on 2011-11-24
> **PDA1 said:**
> 'Couldn't agree with you more about Apple be "locked down".  For all of the worship of the St. Jobs his company sure didn't/doesn't provide much open-source and I simply despise iTunes.  All of the adulation about "iTunes Store" and the trash you can BUY from them is sickening.  Slobbering over Apple stuff is sad.  Now the cult of the iPad is making many disciples!  hat'

Would you also recommend an excellent media player (music, podcasts, videos) that's more flexible than iPod?


But, I really wish Linux would come up with something other than Banshee.....and something that works- the first time.  Gtk-Pod was fun to try and use but did me no good.


Would you please explain to me what you mean about the Libav stuff?  Specifically what you're referring to as the standard Libav codec....or whatever it's called?

Thank you
I can't help with recommendations for a media player iPod alternative;  I have only a very cheap, mp3-only mp3 player which is seen as a USB mass storage machine, so I just drag and drop with nautilus, no messing around with syncing for me between my music folder in /home and the player.

I quite like banshee, and also use rhythmbox, but I don't use either for my portable mp3 player, so can't tell you any more about their abilities in that manner.

For the "extra" versions of the libav* packages you will need to enable [medibuntu]("http://www.medibuntu.org/repository.php") repos, if you haven't already done so by copying and running the command shown on that page, then in synaptic do a search, name only, for **libav extra** and 5 packages will show:-

libavcodec-extra-52,  libavdevice-extra-52,  libavfilter-extra-0,  libavformat-extra-52,  and  libavutil-extra-49.

Mark these for installation;  the standard libav* versions will be removed, and you will find that ffmpeg can now encode many things it could not before.

---

### Post by inobe on 2011-11-24
[http://www.clementine-player.org/](http://www.clementine-player.org/)

my kids get ipods and other junk like that from relatives.

they claim they got this working with that player, i also over heard them saying ipod updates break the whole thing, and is just a gimmick to do so, especially when the device is working fine.

their just kids, i really don't know, however we can learn a lot from them.

---

### Post by FakeOutdoorsman on 2011-11-24
> **PDA1 said:**
> have a good FFMPEG code line for converting videos from mp4 to a format iPod will play?

Please don't reply unless you done the above successfully and know how to do it.  I've read too many posts of people who "know about it but haven't tried it".

There was some flux over the last 3-6 months (I'm guessing here) dealing with the libx264 presets which at times did not have working iPod presets. Things should be working now. If you follow the compile guide then you can try:
```
ffmpeg -i input -vcodec libx264 -preset medium -vpre ipod640 -crf 24 -acodec libfaac -aq 100 output.mp4
```
I believe some iDevices have a max width of 640 pixels wide, so you may have to resize your output. You can automatically do that by adding this output option:
```
-vf scale="640:trunc(ow/a/2)*2"
```
There is also an ipod320 preset for older iDevices that require a video of 320 pixels max width.

No, I didn't try this as I don't own one of these devices, but this is the current "official" iPod command for FFmpeg. I am interested if it works for you. If it doesn't it should be fixed.

If, for some reason, you use ffmpeg from the repository instead of your compiled one then the syntax will probably be different, but I don't really keep up with the repository version(s) anymore.

---

### Post by PDA1 on 2011-11-24
Thank you.

Tomorrow I'll let you know the results of using;

```

ffmpeg -i cba.mp4 -vcodec libx264 -preset medium -vpre ipod640 -crf 24 -acodec libfaac -aq 100 FAKEOUTD.mp4


```


Oh...one other thing- ffmpeg converted the video above into a loadable and playable version on my iPod.  I simply used the code;

```

ffmpeg -i cba.mp4 OUTPUT.mp4


```

---

