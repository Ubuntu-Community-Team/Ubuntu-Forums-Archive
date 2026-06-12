---
title: "mplayer vs Instarnal player in 0.23"
date: 2010-05-03
forum: Mythbuntu
---

### Post by snop3 on 2010-05-03
Hi all,

I have upgraded from 9.10 to 10.04 and in default configuration is for all video extensions Internal player.

Why ? Mplayer is much better (by my point of view).

Why developers decide to use Internal player for all videos ?

Thank you for response.

---

### Post by kenni on 2010-05-03
> I have upgraded from 9.10 to 10.04 and in default configuration is for all video extensions Internal player.

Why ? Mplayer is much better (by my point of view).

Well, you have just installed MythTV not mplayer...why on earth should MythTV use some random external player by default, when it has got a very good integrated player?

If you have some special needs, configure frontend to use mplayer, xine or whatever player you prefer.

I've run with mplayer as an external player for years, but with the current player in 0.23-fixes I don't see any reason for running with an external player...what features are you missing in the internal player?

> Why developers decide to use Internal player for all videos ?

Because it's MythTV not mplayer....seriously...Why doesn't Microsoft use a Linux kernel, when it's much better???? :D Sorry, I couldn't help it...I really don't think the developers need a valid reason for using their own player in their application.

---

### Post by snop3 on 2010-05-03
Hi kenny,

you are right, I want simply some response ;).

My reason is, that internal player have very bad processing/settings/etc of the subtitles.

But yours response is sufficient.

---

### Post by dsauter on 2010-05-03
> **kenni said:**
> ...what features are you missing in the internal player?

I don't think the internal player supports iso files yet.

---

### Post by kenni on 2010-05-03
> **dsauter said:**
> I don't think the internal player supports iso files yet.

It does...just not with storage groups. Disable the video storage group and it works just fine.

---

### Post by tgm4883 on 2010-05-03
> **dsauter said:**
> I don't think the internal player supports iso files yet.

It most certainly does. Storage groups don't support ISO's

---

### Post by kenni on 2010-05-03
> **snop3 said:**
> My reason is, that internal player have very bad processing/settings/etc of the subtitles.

If you're talking about MythTV not finding subtitle files, when you write processing, then it's a well known bug which have been fixed in trunk but not in 0.23-fixes yet ([http://svn.mythtv.org/trac/ticket/8240](http://svn.mythtv.org/trac/ticket/8240)). It should be included in 0.23-fixes fairly soon, the fix is quite easy.

What kind of settings do you need? You can cycle between the available subtitles with T and I believe that Mythvideo follows the default MythTV OSD settings in terms of text size and automatic selection of prefered language.

---

### Post by snop3 on 2010-05-04
> **kenni said:**
> What kind of settings do you need? You can cycle between the available subtitles with T and I believe that Mythvideo follows the default MythTV OSD settings in terms of text size and automatic selection of prefered language.

I was accustomed to big white Arial font which are divided into more lines if there isn't more space, I try T key what is doing with subtitles and let you know if it's ok.

---

### Post by pauna on 2010-05-04
I just did my mythbox upgrade to 10.04.

I'm not sure whether it's the default internal player at fault, but the whole MythTV frontend to exit to desktop when I try to watch a DVD. 

VLC shows the DVD just fine.

The frontend logs doesn't say a lot.

```
2010-05-04 15:36:32.582 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//optical_menu.xml
mount: block device /dev/sr0 is write-protected, mounting read-only
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread

```

But dmesg has more:

```

[  701.503256] UDF-fs: Partition marked readonly; forcing readonly mount
[  701.552211] UDF-fs INFO UDF: Mounting volume 'NANCY_DREW', timestamp 2007/08/30 07:29 (10b4)
...
[  731.815030] VFS: busy inodes on changed media or resized disk sr0
[  731.857116] VFS: busy inodes on changed media or resized disk sr0
[  731.859368] VFS: busy inodes on changed media or resized disk sr0
[  731.861813] VFS: busy inodes on changed media or resized disk sr0
[  732.297307] VFS: busy inodes on changed media or resized disk sr0
[  732.671713] __ratelimit: 2 callbacks suppressed
[  732.671719] mythfrontend.re[2092]: segfault at 10 ip 00007fbd3995a710 sp 00007fbd232c9640 error 4 in libQtGui.so.4.6.2[7fbd396a7000+a50000]

```

---

### Post by iamlindoro on 2010-05-04
Enable the auto-builds repository and upgrade to current .23-fixes.  The issue you describe has been fixed.

---

### Post by Slate8 on 2010-05-04
I have to say I mostly use mplayer still although I should try the internal player on 0.23 and see if it works for me.

The reasons I have used mplayer in the past are better support of embedded and external subtitles, volume nomalisation and buffering seems to be better for slow / wireless frontends.

Anyhoo, would much rather have an integrated player so should I should really give the internal one another bash.

---

### Post by dibuntux on 2010-05-04
I'm still on 0.22, and have many problems with the internal player:
1) DTS stutter
2) No audio on S/PDIF on FLV : have to set audio to analog
3) some mkv x264/h264 files do not play correctly, bad video, bad audio, out of sync.

That does not happen with mplayer, but I cannot use it because I'm on storage groups...

see the thread:
[http://ubuntuforums.org/showthread.php?t=1344794](http://ubuntuforums.org/showthread.php?t=1344794)


Any help with the new 10.04 and .23 on those topics? TIA

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9500GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
HVR1110 DVB-t

---

### Post by snop3 on 2010-05-04
Mplayer is much better than Internal, there are many audio and video filters and many many useful options.

Better choice would be to implement Storage Groups with mplayer.

---

### Post by iamlindoro on 2010-05-04
> **snop3 said:**
> Mplayer is much better than Internal, there are many audio and video filters and many many useful options.

Better choice would be to implement Storage Groups with mplayer.

I wouldn't spend any time on that.  When Storage Group ISO/VIDEO_TS/BDMV playback is worked out, expect external player support to disappear.  If the internal player doesn't have a feature you desire, now is the time to add it, before you no longer have a choice.

Commence angry replies!

---

### Post by jmeads on 2010-05-24
> **dibuntux said:**
> 
That does not happen with mplayer, but I cannot use it because I'm on storage groups...


You can use storage groups and an external player, i'm doing it myself, 

Just require a simple shell script. If you set the external player to be a shell script, ie /usr/local/bin/externalplayer.sh

then just translate the files movie name to remove the myth stuff, ie

#!/bin/bash
MPLAYER=/usr/bin/mplayer
FILE="$1"
FF=$(echo $FILE | sed 's/myth:\/\/Videos@192.168.xx.xx:6543/\/local\/videos/')
$MPLAYER -fs -zoom -quiet ..etc..  "$FF"

where 192.168.xx.xx is the ip of the backend

---

### Post by nickrout on 2010-05-25
> **jmeads said:**
> You can use storage groups and an external player, i'm doing it myself, 

Just require a simple shell script. If you set the external player to be a shell script, ie /usr/local/bin/externalplayer.sh

then just translate the files movie name to remove the myth stuff, ie

#!/bin/bash
MPLAYER=/usr/bin/mplayer
FILE="$1"
FF=$(echo $FILE | sed 's/myth:\/\/Videos@192.168.xx.xx:6543/\/local\/videos/')
$MPLAYER -fs -zoom -quiet ..etc..  "$FF"

where 192.168.xx.xx is the ip of the backend

That is quite nifty. I can't quite follow the sed patterns but I assume that it converts from a myth protocol address to a file location.

I assume this means that you need to have the video directories mounted at the same point on each frontend, just like the pre storage group situation?

By the way the demise of the external player is greatly exaggerated, external player support is NOT being ditched:

[http://www.gossamer-threads.com/lists/mythtv/users/436989#436989](http://www.gossamer-threads.com/lists/mythtv/users/436989#436989)

---

### Post by iamlindoro on 2010-05-26
> **nickrout said:**
> That is quite nifty. I can't quite follow the sed patterns but I assume that it converts from a myth protocol address to a file location.

I assume this means that you need to have the video directories mounted at the same point on each frontend, just like the pre storage group situation?

By the way the demise of the external player is greatly exaggerated, external player support is NOT being ditched:

[http://www.gossamer-threads.com/lists/mythtv/users/436989#436989](http://www.gossamer-threads.com/lists/mythtv/users/436989#436989)

The above script won't support more than one directory in a storage group, and yes, you would need to have them locally mounted-- at which point there's no real  point in using Storage Groups at all, just use a local setup.

Note that the exact fate of external players is very much in the air.  I said that I would accept a compromise of allowing a "panic button" player if I am not the one to solve the ISO/Video_ts playback issue, but if it languishes any longer and I end up coming up with the solution, it's a very real possibility that I won't even leave that.  People who are unhappy with the internal player should be submitting samples and patches in tickets now to make it behave as they wish.  People who want to see the bare minimum "panic button" alternate player should be getting intimately familiar with the ringbuffer and remotefile code to interface the DVD and Blu ray ringbuffers with remotefile properly.

---

### Post by StarWarrior on 2010-06-25
> **iamlindoro said:**
> Enable the auto-builds repository and upgrade to current .23-fixes.  The issue you describe has been fixed.

how long does it usually take until this bugfix lands in the normal repositories? I'm a bit reluctant to activate these auto-builds on my regular Mythbox. Are they stable enough?

---

### Post by tgm4883 on 2010-06-25
> **StarWarrior said:**
> how long does it usually take until this bugfix lands in the normal repositories? I'm a bit reluctant to activate these auto-builds on my regular Mythbox. Are they stable enough?

The normal repositories don't get updates to mythtv. So it will hit the repos for 10.10, but not 10.04

---

### Post by Neon Dusk on 2010-06-25
So even although the standard repositories for 10.04 contain 0.23.0+fixes24158 which is pre-release version of mythtv (between rc2 & rc3) they will never be updated to at least the release version of mythtv 0.23?

---

### Post by tgm4883 on 2010-06-25
> **Neon Dusk said:**
> So even although the standard repositories for 10.04 contain 0.23.0+fixes24158 which is pre-release version of mythtv (between rc2 & rc3) they will never be updated to at least the release version of mythtv 0.23?

Not unless the Mythbuntu developers suddenly get more free time and the urge to backport the release to 10.04. Even then, it likely wouldn't get the release of 0.23, but a build from the fixes branch (which is what auto-builds is)

---

### Post by nickrout on 2010-06-25
the auto builds 0.23-fixes is very stable. trunk (0.24) won't always be. Besides on 0.23-fixes once you get your problems fixed you do not have to update again if you are scared of breaking things.

---

