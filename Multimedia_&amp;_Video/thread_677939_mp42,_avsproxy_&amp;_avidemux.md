---
title: "mp42, avsproxy &amp; avidemux"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Holonet on 2008-01-25
Anyone know how to get the mp42 codec to work under wine?  I've got avidemux 2.4 running, and I copied avsproxy/avsproxy_gui over from a windows install, and that all seems to work fine, except when I try to start the proxy, it says it can't locate a decompressor for mp42 fourcc, etc....  So I see the one lynch pin here is that avsproxy, being in wine, is looking for Windows codecs.

After some reading around, I managed to get xvid to show up in Virtualdub's menu by copying dlls over from Windows, and altering the system.ini file to point to the dll file.  I have the dlls from Windows...is there a way to do something similar for Microsoft's mp42?  If so, what exactly has to be put in the system.ini file?...or another way is certainly welcome.  I tried downloading the codec, but the mp42 all say to install by right-clicking on the .inf file and clicking install, which obviously isn't so easy in wine, that I'm aware of.

---

### Post by disturbed1 on 2008-01-25
Download and install the Xvid codec for windows. This installs just fine through wine. Set it to decode all mpeg4 streams. If there is still a problem with "mp42" use the fourcc changer that was installed with the Xvid codec to change the fourcc to divx. [http://www.free-codecs.com/Koepi_XviD_download.htm](http://www.free-codecs.com/Koepi_XviD_download.htm)

I don't do audio encoding through wine, but I've read that if you install ffdshow, this will enable mp3 playback and reading.

Avisynth installs and runs fine through wine. I use avs2yuv to pipe the avisynth script to theora for some luscious encoding :D

---

### Post by Holonet on 2008-01-25
Thanks for replying.  I don't know why, but Xvid does not install properly for me.  If I try, every file it tries to copy, I get an error--"External exception 6BA."  However, I just  hit ignore several times, and it finished the installation at least, and perhaps with the files I copied over, it's working.  It made xvid show up again in Virtualdub (a duplicate :-|), but avsproxy still can't find it.

Hmm, but the xvid is in the wine menu now...I checked configure and divx is selected.  Must be some other reason avsproxy isn't picking it up...

avsproxy is derived from avs2yuv, so I'm not clear on why it's not working.

The ffdshow seems to work.  Virtualdub has Mpeg3 listed.  But it gives the same mp42 error...root of the problem must be in whatever caused my xvid installation to foul up.

I actually have no desire to encode audio in wine...video either, really.  I just want to be able to use avisynth, which, of course, goes via Windows.  The encoding, I'd like to do with avidemux.  DEcoding it so it can get there, if I'm understanding this properly, is all I want to do.

---

### Post by eye208 on 2008-01-25
What exactly are you trying to do that requires Windows tools and cannot be done with FFMPEG and/or MEncoder instead?

---

### Post by Holonet on 2008-01-26
Use avisynth filters without booting into Windows; specifically, I'm interested in DeJitter, because I have some messy VHS rips that I need to re-encode anyway, and DeJitter is a big improvement on many of them.

---

### Post by eye208 on 2008-01-26
MEncoder has these filters too. And if you don't like MEncoder for some other reason, there is also AviSynth for Linux.

No need to use WINE and Windows tools here.

---

### Post by disturbed1 on 2008-01-26
> **eye208 said:**
> MEncoder has these filters too. And if you don't like MEncoder for some other reason, there is also AviSynth for Linux.

No need to use WINE and Windows tools here.

There is not an Avisynth for Linux............just yet. Yes there is heavy development on version 3.0 which uses GSTreamer, however it's more or less unusable for anyone but a developer, or tester. They've barely gotten the filter graph together to parse a file.

Read here for avsproxy and avidemux [http://avidemux.org/admWiki/index.php?title=Avsproxy](http://avidemux.org/admWiki/index.php?title=Avsproxy)


It could be that your wine installation is corrupt somehow. If you want to attempt to fix it, just delete the .wine folder in your home directory. For myself, I don't use any outside programs (winetools) to aid in the setup. After I do a basic configure wine, I set the OS to windows 2000, and things just seem to work fine.

---

### Post by eye208 on 2008-01-26
Well, I'm not familiar with AviSynth for Linux since I use MEncoder instead. It comes with a broad range of high quality filters.

---

### Post by disturbed1 on 2008-01-26
> **eye208 said:**
> Well, I'm not familiar with AviSynth for Linux since I use MEncoder instead. It comes with a broad range of high quality filters.


Some of the MEncoder filters are avisynth ports, some avisynth filters are MEncoder/FFMPEG ports.

The only time I use avisynth is when I need it's decrawl, dedup, deflicker, and/or RestoreFPS. 

Here's a list of avisynth filters [http://avisynth.org/warpenterprises/](http://avisynth.org/warpenterprises/)

Info on avisynth 3.0
[http://avisynth.org/AviSynth30](http://avisynth.org/AviSynth30)
[http://forum.doom9.org/showthread.php?t=118035](http://forum.doom9.org/showthread.php?t=118035)
^^ Hopefully it won't be too long before it's usable.

---

### Post by Holonet on 2008-01-26
Yes indeed, if avisynth 3.0 were ready, I'd be a happy camper, but I've got a drive fulla stuff and I need to do some encoding now hehe.  

Hmm, well I googled mencoder dejitter filter and the first thing that came up was this thread :lolflag: .  I'm assuming that it must be called something different...which would be welcome information.  Also, can mencoder (I've never actually used it, aside from a dependency) act a as a frameserver to avidemux?  Another reason for doing this is being able to re-encode in avidemux (or Virtualdub, but if this issue were solved, I'd like avidemux better for it's threading capacity and...in my personal opinion...better organized interface).  I don't mind a little CLI work (like avisynth lol), but in this case, being able to look at a preview and such, being video, is quite a time saver.  Also, what got me interested in avisynth the first time I used it...I don't want to be flip-flopping colorspaces with these videos.  They're in rough enough shape, and that won't help.

There's no need to go through all that CLI for avsproxy.  There's also avsproxy_gui, which sets it up in a nice little interface for starting the proxy.  It looks to me like it works fine...except for the fact that it "can't locate a decompresser for mp42..."...and I don't think that's a problem with the gui or a configuration problem, because if I directly try to open the video file in Virtualdub, I get the same message.

---

### Post by disturbed1 on 2008-01-26
If it's only the mp42 issue, then change the fourcc to divx or xvid ;)

---

### Post by Holonet on 2008-01-26
Hehe, yeah, that's a fine idea, and I might break down and just do that, but I'd still like to know the why...if xvid is supposed to install properly, then I'd like to figure out what's gone wrong.  But I haven't tried fixing the wine installation yet, I've been playing with a few other "issues" on my computer.  I'll post the results just for information's sake when I do.  Either way, thanks to all for the help.

---

### Post by disturbed1 on 2008-01-26
The why is because mp42 is a hacked microsoft mpeg4 v2 codec. Sometimes called low motion divx, 3ivx, or the smr codec. It was used exclusively for pirated movies maybe 4-5 years ago. And, to this day, is incorrectly distributed by some "codec" packs. It may also be used by some less than stellar video encoding applications.

Changing the fourcc is nothing more than opening the tool, browsing to the file, select new fourcc, and click apply. Takes 3-5 seconds, depending on how fast you can navigate a GUI with 3 options :D

---

### Post by Holonet on 2008-01-26
Oh fubar...  Yeah, I knew about divx low-motion and such, but I didn't think it was the same codec.  I'm partial to xvid because it's good and not proprietary...bah, all that gets confusing.

Anyway, yeah, I tried changing the fourcc to xvid, and got some interesting results.  I tried opening the avs script in the avsproxy gui, and it still said the same thing...mp42 and all :confused:...but when I tried opening it in virtualdub, it said can't locate a decompresser for xvid...yet xvid shows up in the video compression list.  I'm thinking this must have to do with the patchwork install of xvid I barely got through, and/or wine issues, as suggested.  I deleted my .wine directory (except drive_c, of course).  I'm configuring wine myself now.  Time will serve to determine if I actually successfully build that thing or go crawling back to a deb for reinstallation.

---

### Post by eye208 on 2008-01-26
MP42 is listed as a supported format in the MEncoder/FFMPEG docs.

---

### Post by Holonet on 2008-01-26
...I'm sure it is, but that doesn't mean I can use dejitter with it or explain why avsproxy doesn't seem to recognize that I changed the FourCC, while VIrtualDub does.  I'm not sure I see what you're getting at, is there a filter in Mencoder that does the same job as avisynth's dejitter?

---

### Post by Holonet on 2008-01-27
Ok little update here.  To alleviate doubt, I separated my home folder to a different partition and reinstalled Gutsy.  I deleted what traces of .wine I found in the home folder and reinstalled...and indeed, there must have been something wrong with my wine installation, because xvid installed just fine.  Now for the interesting part...

The mp42 message still comes up in both virtualdub and avsproxy.  Since xvid was supposed to decode all of those, and installed properly this time, this makes little sense.  However, this time, changing the FourCC worked, and avsproxy did its job without error.  Unfortunately, when I tried to connect avidemux to it, all I got was this odd blank green screen for every frame of the movie.  Opening the actual file in Virtualdub (with the xvid fourcc) worked as well, but with a similar weird caveat...it made the screen black...and moving the mouse about brought it back, but then switching to another frame did it again...and still, no picture.

---

