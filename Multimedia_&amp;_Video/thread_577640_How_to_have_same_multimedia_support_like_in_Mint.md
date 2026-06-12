---
title: "How to have same multimedia support like in Mint?"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by perixx on 2007-10-16
Hello again!


Has somebody any idea on how to provide exactly the same Multimedia support in Xubuntu 7.04 / 7.10 then under 'Mint'?

thanks for hints...

perixx

---

### Post by floke on 2007-10-16
Grasshopper,

Seek for 'medibuntu' and you shall find multimedia enlightenment awaits...

---

### Post by wolfen69 on 2007-10-16
go here: [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)  enter those 2 lines into terminal.

then in terminal:
```
gksudo gedit /etc/apt/sources.list
```

copy and paste the following lines into the list:

deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

save file.

in terminal:
```
sudo apt-get update
```

open add/remove applications.
from pull down menu at top right, choose all available applications.
then search for ubuntu restricted.
install.

the deb files you put into your sources.list will enable you to download pretty much anything from synaptic. have fun.

---

### Post by perixx on 2007-10-16
Thank you!

Unfortunately, I'm rather ignorant about codec support. I've heard about Mint having practically everything needed, that's why I'm looking for 'exactly the same codecs + players' like in Mint; don't want to change to Mint, though, for I assume the support in Ubuntu is better overall and with software-vendors in the long run in particular....

perixx

---

### Post by perixx on 2007-10-16
Say, 


isn't everything contained in the medibuntu repositories ? Currently, I use 
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)
for free and non-free packages.

Those aren't sufficient?
I'm just asking, because I don't want to add too much repositories...
Just did a
 
sudo apt-get install ubuntu-restricted-extras

but that didn't work for the playback...


are the repositories here trustable and needed?
 
[http://repoubuntusoftware.info/](http://repoubuntusoftware.info/)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)


perixx

---

### Post by rsambuca on 2007-10-16
Those repos should be fine.  Mint is perfectly compatible with ubuntu by the way, so you could just install Mint if you are having this much trouble.

---

### Post by perixx on 2007-10-16
allright, I've followed the procedure as you said, wolfen69....
shouldn't I now be able to play simlpe .wav files with gxine??

do I have to restart the PC?

perixx

---

### Post by perixx on 2007-10-16
thanks for you support so far, wolfen69 and rsambuca...


unfortunately there's obviously no go with Gxine at all - though it says there are no demultiplexers or some such, which is strange, because it really should've installed the necessary codecs by now. I can't make sense out of this :(

Seems I'm down to trying another player ....


perixx

---

### Post by wolfen69 on 2007-10-16
try VLC. it always works great for me.

---

### Post by perixx on 2007-10-17
I tried VLC under windows and it was OK, but I liked mpc better... since that's not an option here:

what integrates better into Firefox, VLC or Mplayer? And which has better support/features in your opinion?

P.S.: I still have all codecs installed - these wouldn't be needed at all with VLC, right? Can VLC also do DVD's and .mov files?

greetz


perixx

---

### Post by perixx on 2008-01-09
I've been using SMPlayer (based on Mplayer) for a few months now, but I'm dissatisfied with it's instability and inconsistent behaviour; I'm experiences crashes frequently, Audio tracks and Subtitles change all of a sudden and can't be reset without re-starting the app, Vsync is not possible (unless enabled for everything in the 'amdCCCle' settings menu),  rewinding/forwarding feature is a real mess, playing back audio-CD's doesn't work unless specified as autoplay-event but autoplay doesn't respond half-of-the-time, etc.... 

The positive thing about it: nearly all (video) media files from internet are being played back, though not everything as embedded Firefox-window.

So I'm up to try another player again now...

perixx

---

### Post by rvm4000 on 2008-01-10
Have you tried the [latest version of smplayer](http://smplayer.wiki.sourceforge.net/Unstable+releases) AND the latest version of mplayer from svn?

Many problems that users report (like seeking issues) are because they're using an old mplayer.

---

### Post by perixx on 2008-01-27
@rvm4000:

I compiled the latest smplayer version, also mplayer. While the first one proved to be at least no harm, the mplayer-SVN version didn't work in any way - no GUI, no codecs linked to it... I removed that one again.

As for smplayer, I can't tell if it made a change to the better yet.

perixx

---

### Post by rvm4000 on 2008-01-28
I recently created a deb package from mplayer from svn, maybe you can try it: 

[http://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588](http://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588)

---

### Post by perixx on 2008-01-28
Thank you for providing a .deb package, rvm4000!

I'll try it soon, currently I'll have to fix my ATI's OpenGL again. Somehow checking out SVN and compilation seemed to work, but all i got was the pure CLI thing without any codec support... 
Btw., SMPlayer is definitely a step into the right direction, so as to say! If you can get it more stable, enhance its features and make the GUI a little more ergonomically, this baby rocks!!

If you're interested in any suggestions, just say so.

perixx

---

### Post by rvm4000 on 2008-01-28
Yes, suggestions (and bug reports) are always welcome :)

By the way, [in this post](http://smplayer.sourceforge.net/forums/viewtopic.php?id=208) you can read the steps to create a deb package for mplayer (actually based from two posts in this forum).

---

### Post by perixx on 2008-01-28
Thanks for the info!


Here some suggestions / experiences for SMPlayer, as promised :)

1) a simple 'Repeat'-Button on the GUI for the currently playing video/song (I'd often need that one) would be greatly appreciated..!

2) I don't know if SMPlayer/Mplayer is responsible for it, but under Xfce, when trying to add CD/DVD-autoplay, that won't just work reliably. At first, I have to create a mini-script that invokes some slowdown-app like 'setcd':```
#! /bin/bash
setcd /dev/dvd -x 2
/usr/local/bin/smplayer dvd://1
``` then starting SMPlayer which starts MPlayer, in order to have a decently silent playback... this takes long to come up and sometimes involves several speed-up/slow-down cycles in the drive (I'm using a Samsung SH-S182 btw.). You would do a magnificient job by implementing some small fader that can directly control the drive's speed. 

3) pressing 'play CD button' in the menu sometimes will not work for me (perhaps because I have two drives, have to check again). There's no 'play CD' button on the GUI.

4) As told, last time I checked, (std. feisty version) SMPlayer would often start with the wrong language and/or subtitle (English) and wouldn't apply changes made in the menu. Only quitting and re-starting the player would play back the right audio track (if selected before quitting or so), but not always. It will definitely mess up when changing the audio one or two times while playing a video. I'll check again with the new mplayer package installed soon.

5) Audio playback would require a different, short'n'sweet approach, I feel (Play-CD-button on GUI, that invokes title-list on media on rightclick, perhaps).

6) for my TFT's native resolution (1280x1024), the standard GTK-font is by far too small and narrow (I got Xfce4 - Feisty). And most people tend to have even bigger widescreen monitors as of today...

7) I know that might be beyond your 'responsibility', but - video-playback is ALWAYS crippled by tearing problems (I always read of many other ppl. having this problem with mplayer, so...) - perhaps you can do sth. about this greatly grieving issue... I got an ATI X1950 GT btw., and the ONLY way to have tearing-less videos is with 'amdcccle' having 'Vsync' enabled for everything, which will put down 3D-performance too drastically.

8] for me, using the 'amplifier' mode with 'normalization' will cause unpredictable results, with mostly really booming sound which can't be controlled from the GUI's main fader - going back into the menu all time is rather cumbersome. And without amplifying, the sound's too quiet. I used 'Alsa' with an ADI 1986A onboard chip. I tried 'OSSv4' with my old Envy24-chip-based PCI card lately. But it won't work yet, apart from the 'osstest' playback.

So far for now - I hope you can make use of the information :)


greetz,
perixx

---

### Post by rvm4000 on 2008-01-28
> **perixx said:**
> 
1) a simple 'Repeat'-Button on the GUI for the currently playing video/song (I'd often need that one) would be greatly appreciated..!

Play -> Repeat.

If you mean a button in the toolbar... well it's planned for the next version (0.7.0) a toolbar editor, so the user can choose the actions that should appear in the toolbars.

> **perixx said:**
> 2) I don't know if SMPlayer/Mplayer is responsible for it, but under Xfce, when trying to add CD/DVD-autoplay, that won't just work reliably. At first, I have to create a mini-script that invokes some slowdown-app like 'setcd':```
#! /bin/bash
setcd /dev/dvd -x 2
/usr/local/bin/smplayer dvd://1
``` then starting SMPlayer which starts MPlayer, in order to have a decently silent playback... this takes long to come up and sometimes involves several speed-up/slow-down cycles in the drive (I'm using a Samsung SH-S182 btw.). You would do a magnificient job by implementing some small fader that can directly control the drive's speed. 

Not tested myself, but it seems mplayer provides some options to set the CD (and DVD) speed:
```

       -cdda <option1:option2> (CDDA only)
              This option can be used to tune the CD Audio reading feature  of
              MPlayer.

              Available options are:

                 speed=<value>
                      Set CD spin speed.

```

So I guess you can add something like **-cdda speed=2** in Preferences->Advanced->Options for MPlayer.

> **perixx said:**
> 
4) As told, last time I checked, (std. feisty version) SMPlayer would often start with the wrong language and/or subtitle (English) and wouldn't apply changes made in the menu. Only quitting and re-starting the player would play back the right audio track (if selected before quitting or so), but not always. It will definitely mess up when changing the audio one or two times while playing a video. I'll check again with the new mplayer package installed soon.

Please test with the latest versions of smplayer and mplayer.

> **perixx said:**
> 
6) for my TFT's native resolution (1280x1024), the standard GTK-font is by far too small and narrow (I got Xfce4 - Feisty). And most people tend to have even bigger widescreen monitors as of today...

Preferences->Interface. There's an option to select the default font (including the size) for smplayer.

> **perixx said:**
> 
7) I know that might be beyond your 'responsibility', but - video-playback is ALWAYS crippled by tearing problems (I always read of many other ppl. having this problem with mplayer, so...) - perhaps you can do sth. about this greatly grieving issue... I got an ATI X1950 GT btw., and the ONLY way to have tearing-less videos is with 'amdcccle' having 'Vsync' enabled for everything, which will put down 3D-performance too drastically.

Be sure you're using xv as video driver.

> **perixx said:**
> 
8] for me, using the 'amplifier' mode with 'normalization' will cause unpredictable results, with mostly really booming sound which can't be controlled from the GUI's main fader - going back into the menu all time is rather cumbersome. And without amplifying, the sound's too quiet. I used 'Alsa' with an ADI 1986A onboard chip. I tried 'OSSv4' with my old Envy24-chip-based PCI card lately. But it won't work yet, apart from the 'osstest' playback.

I can't see any problem with those two options enabled (well, the volume is too high for my taste).

---

### Post by perixx on 2008-01-29
Hi!

> If you mean a button in the toolbar...  Yes, that's what I had in mind :) Often used and every CD-Player has a button for this on the front panel...

> It seems mplayer provides some options to set the CD (and DVD) speed: Nope, that doesn't work - I've tested it. And it's maybe really just for the Audio-CD's (CDDA). Anyway, even this doesn't function properly.

> Be sure you're using xv as video driver. I'm using it. Doesn't make any difference...

I just wanted to suggest to use another, little more seasonable font by default :)
I'll try out the new Mplayer backend soon...

best regards,

perixx

---

### Post by andrew.46 on 2008-01-30
Hi,

 Saw your trouble with mplayer:

> **perixx said:**
> @rvm4000:

I compiled the latest smplayer version, also mplayer. While the first one proved to be at least no harm, the mplayer-SVN version didn't work in any way - no GUI, no codecs linked to it... I removed that one again.

As for smplayer, I can't tell if it made a change to the better yet.

perixx

You have simply missed out a few vital steps. You could do worse that follow this tutorial on the Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

which will give you a modern codec pack as well as the gui gmplayer. If you are keen to get a debian package you will need a few *extra* files:

```
$ sudo apt-get fakeroot dpkg-dev libconfhelper-perl liblogfile-rotate-perl
```

and instead of the whole ./configure process documented in this walkthrough, change to the source directory and run:

```
$ sed -i_bak 's/1\.0svn/3\:1\.0svn/' debian/changelog
$ DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary
```

The 'sed' line changes the packaging identification slightly so there will be no conflict with the Ubuntu repository. Dont't forget to clean the code after the compile process has finished with the following command:
```

$ sudo fakeroot debian/rules clean
```

And now you should have an authentic debian package, not a checkinstall imitation, sitting there ready to install, a great codec pack *and* a gui player.

          Andrew

---

### Post by rvm4000 on 2008-01-30
> **andrew.46 said:**
> ```
$ sed -i_bak 's/1\.0svn/3\:1\.0svn/' debian/changelog
$ DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary
```

The 'sed' line changes the packaging identification slightly so there will be no conflict with the Ubuntu repository.

I gave to [my package](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn25873_i386.deb) the version 2:1.0rc2svn25873. The packaging system considers it newer than the version in the repositories (which is true), but if in the future they add to the repository a version named 2:1.0rc3, that will replace the svn one (which is correct). With a version which starts with 3:... it would never be replaced, and so you'll end up with an old version installed.

Also I made some changes in debian/control, so my package cleanly replaces mplayer-doc, mencoder and mplayer-nogui, in case the user had any of them installed ([details](http://smplayer.sourceforge.net/forums/viewtopic.php?pid=873#p873)).

---

### Post by andrew.46 on 2008-01-30
Hi,

 Good to finally 'meet' the smplayer developer!

> **rvm4000 said:**
> I gave to [my package](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn25873_i386.deb) the version 2:1.0rc2svn25873. The packaging system considers it newer than the version in the repositories (which is true), but if in the future they add to the repository a version named 2:1.0rc3, that will replace the svn one (which is correct). With a version which starts with 3:... it would never be replaced, and so you'll end up with an old version installed.


My logic though is that the release version will *always* be behind the svn version,* if *the svn version is kept updated. It is all more than a little unsatisfactory though and I suspect will remain so until the debian/changelog file of the svn mplayer and the naming system adopted by Ubuntu correlate a little better.

   Andrew

---

### Post by perixx on 2008-01-31
Andrew.46, rvm4000,

many thanks for the helpful info you posted here! I'll try out those steps as soon as I managed to recover my alsa sound system and video accelleration again... I've maneuvered myself into a little trouble by experimenting too much lately :]

perixx

---

### Post by jpennin5 on 2008-01-31
This guide might answer some of your questions

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

