---
title: "[SOLVED] Playing FLV fies -- Another &amp;quot;Linux moment&amp;quot; (sigh...)"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by Phrawm48 on 2007-08-10
For five months I've tried hard to be a happy Ubuntu user (Dapper).  But sometimes, gosh darn it, Linux just keeps making apparently simple things so hard.

EXAMPLE -- Playing FLV (.flv filename extension) files.

Windows: Do simple Web search for "playing FLV files".  Quickly locate stand-alone player, download and install it, double-click on FLV file, begin playing.  Done.  Total time: 5 minutes.

Linux: Do iteratively refined Web search for "linux play (flv OR .flv) files linux".  Locate numerous threads and mention of text-based scripts but no stand-alone programs.  Try -- and fail -- to configure repositories to download needed components.  Search Ubuntu forums, find scripts(!) rather than solutions, try using VLC Media Player: result = video doesn't appear.  Try other players with identical non-result.  Abandon effort -- I if really need to view FLV files I'll boot into Windows.  Create this post, hopefully expressing my extreme frustration.

Bottom line: In Ubuntu Dapper, after about one hour of research, I still can't double-click or otherwise simply open a FLV file and play it as I can on Windows.  Is it even possible?  The evidence suggest it isn't.

I'm a Linux booster, an Ubuntu fan, but this kind of stupid "Linux moment" is, alas, all too illustrative of the reason Linux won't gain wider acceptance...

Cheers & thanks,
Ric
SFO

---

### Post by Gremlinzzz on 2007-08-10
What are you trying to view i have no problem watching flv. make a link to what your trying to watch.

---

### Post by bliffle on 2007-08-10
You can easily play FLV with vlc and other software. You can also convert to avi with ffmpeg. In fact, that conversion is etter and cheaper (than the $50 win pgm I bought) than on windows.

Are you running 7.04?

---

### Post by Phrawm48 on 2007-08-10
Hi:

Thanks for the responses:

> make a link to what your trying to watch.
It isn't links, it's files on disk.  Playable by double-clicking on Windows, but not Ubuntu.

> Are you running 7.04?
Dapper (6.04).  Not really gonna' upgrade, either, since for the most part Dapper does what I want it to, and I don't want to lose all my customizations and tweaks.

I did download ffmpeg and found it confusing.  Here again, it's a command-line tool with a huge list of options specific to it.  As I said, I'll just use Windows for view .flv files by double-clicking -- it's so much easier...

Cheers & thanks 'gain,
Ric
SFO

---

### Post by Gremlinzzz on 2007-08-10
[[Dapper (6.04). Not really gonna' upgrade]] are you still using windows 95 ? maybe its not a linux problem but a i cant change problem.

Cheers & no help 4 u
:guitar:

---

### Post by Lorenzo1449 on 2007-08-10
Haa ha, this sounds too familiar! I too am a frustrated Ubuntu fan...and ironically found this thread whilst hunting for a video player that works well. The Totem movie player, on the rare occasions it works, plays audio and video out of sync. Is it struggling with encrypted video files I wonder?

---

### Post by jabagawee on 2007-08-10
Here's what you do:

```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude install vlc mplayer

```

The update will ensure you get the latest version of vlc and mplayer. Do me a favor and perform a distro upgrade soon. Cheers!

---

### Post by john_rotten on 2007-08-30
I'm with you Phrawm48,
    glad to finally find someone with the same issue. I just want a standalone FLV player, to play downloaded flash video. Everyone says to use VLC or Mplayer.  I have them both installed and they will both play VLC files but neither will allow me to skip forward or back, all I can do is play the video from start to finish. Seems lame because I have used many windows standalone flv players that allow me to skip around the video no problem.  
    Is there no good standalone flash player out there for Linux ?  :confused:

---

### Post by jim_p on 2007-08-30
Well, you can play .flv files on mplayer and vlc, once you install them.
(this applies to me as well because it took me some time to find these players)

The thing that annoys me A LOT is that i cant use seeking! On any player!
That is a major drawback since ALL windows flv-related apps have seeking!

Of course there is some script out there that converts flv to avi using divx compression but the quality is horrible.Thats why I use these 2 "ready made" commands

```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 test.mpg

ffmpeg -i video.flv -ab 128 -ar 22050 song.mp3
```

I am sure you can figure out what each one does

---

### Post by Phrawm48 on 2007-08-30
Jim:

>  ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 test.mpg

ffmpeg -i video.flv -ab 128 -ar 22050 song.mp3Thanks for posting those commands -- they helped!

In the meantime, I run one of the various easily locatable free FLV players for Windows under my WMware Server virtualization partition. (Or boot into Windows...)

At some point I'll probably upgrade from Dapper to whatever Ubuntu release is current at the time. Perhaps that will help.  Having said that, I'm not eager to upgrade because I'll probably lose months worth of tweaks and adjustments to my Dapper system which works pretty well in most other regards...

Cheers & thanks 'gain,
Ric
SFO

---

### Post by Lord Illidan on 2007-08-30
I don't get it.. gmplayer seeks through flv files well...Try and upgrade to Feisty, at least.

---

### Post by Phrawm48 on 2007-08-30
LI:

*Try and upgrade to Feisty, at least.*

I don't want to go off-thread but...  The problem is I have a Dapper system that *reliably* does ninety-nine of the one-hundred of the things I want it to do.  Do I really want to "trash" that system simply to be able to play FLV files?  Especially when there are workarounds?

At some point I'll probably upgrade.  But that's a project that will undoubtedly require a whole day to complete, perhaps more.  Then there's the issue of what upgrading will break; it's sure to break something.  I'll then be obliged to troubleshoot one or more upgrade-induced problems far more consequential than merely being able to play FLV files directly under Ubuntu...

So for the time being, I'm gonna' sit happily here and play FLV files under Windows or Windows-via-VMware for a while longer...

Cheers, thanks, & take care,
Ric
SFO

---

### Post by Phrawm48 on 2007-09-16
Okay, I "fixed" this problem by upgrading to Feisty.

The good news is that FLV files can, after a few supplementary codec downloads, be played under Linux 7.04 (and presumably later versions as well...?)

The less good news is, as others have observed, that the files can be played serially in their entirety but not fastforwarded or rewound...

Cheers & hope this helps,
Ric
SFO

---

### Post by BryanFRitt on 2007-12-23
> At some point I'll probably upgrade from Dapper to whatever Ubuntu release is current at the time. Perhaps that will help. Having said that, I'm not eager to upgrade because I'll probably lose months worth of tweaks and adjustments to my Dapper system
You could wait for the next version that has LTS (long term support) and use that one.  
I think it will be 08.04

---

