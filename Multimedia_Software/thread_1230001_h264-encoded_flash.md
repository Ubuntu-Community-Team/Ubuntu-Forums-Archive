---
title: "h264-encoded flash"
date: 2009-08-02
forum: Multimedia Software
---

### Post by stoppage on 2009-08-02
Hi, I've got an flv file here, its decoded with H264 codec...the vlc player (0.8.6e) wont play it (plays other flash no problem) although vlc in Windows has no problem. Mplayer also doesnt recognise it. Is there another version of vlc I can download? Running Ubuntu Hardy, any help appreciated

---

### Post by EmmGeeImage on 2009-08-02
The windows version should run under WINE, which is in the "add/Remove" section of "applications." WINE lets you use the Windows versions of the programs, which may work easier.

When in that secion, do a search for "WINE," it is easier to find it, than to scroll all the way down to get to it.

---

### Post by vinutux on 2009-08-03
disable all unofficial repos in tour system like mediubuntu...

install vlc 1.0 from this ppa **[https://launchpad.net/~c-korn/+archive/vlc]("https://launchpad.net/~c-korn/+archive/vlc")**

---

### Post by andrew.46 on 2009-08-03
Hi stoppage,

> **stoppage said:**
> Hi, I've got an flv file here, its decoded with H264 codec...the vlc player (0.8.6e) wont play it (plays other flash no problem) although vlc in Windows has no problem. Mplayer also doesnt recognise it.

If you are interested in trying something different you could build your own copy of MPlayer that would easily this file:

[Howto] Successfully install the svn MPlayer under Hardy Heron 
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

This will play almost anything except amr which I have not yet added in :-).

Andrew

---

### Post by mc4man on 2009-08-03
If you follow Andrew's guide you should be set up quite well for mplayer, the current versions use  'self contained' ffmpeg libraries for most decoding (with win or w32codecs providing some more

For other players that depend on the shared ffmpeg libs, (like vlc), you would want to **add** the hardy medibuntu repo as a source (if you haven't already), after which, (running sudo apt-get update first), you'll find updates for the ffmpeg shared libraires that are more capable than the default hardy ones (libavcodec1d, libavformat1d, ect. (run update manager

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


As far as vlc you may benefit from and like the the newer version available from the korn ppa, note that the highest version available from there for hardy is 0.9.9a 
((the odds of getting a vlc 1.0.1 0r 1.1 for hardy from a ppa are slim, though atm, depending on your usage, 0.9.9a is a 'better' build


The other mplayer option, if not inclined to build, is getting a build from the rvm mplayer ppa, and maybe a smplayer frontend in either case

---

### Post by stoppage on 2009-08-04
Thanks for the help, I dont really want "Wine" in my system. ...so I went for vlc option and now have version "0.9.9.a". When I feed flv in I get...


No suitable decoder module:
VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.
No suitable decoder module:
VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.

And mplayer also doesn't recognise it....hmmmmm...

---

### Post by mc4man on 2009-08-04
While I use hardy it is not a 'stock' install by any means so I can't install libavcodec1d, (the repo or medibuntu version), nor the 0.8.6 vlc player to test. (without building them, which isn't worth it

All vlc versions and both the ubuntu and medibuntu mplayers will use the shared ffmpeg libraries (libavcodecxx, libavformatxx, ect.

Possibly the medibuntu libavcodec1d, ect aren't built to decode your video

Why don't you search ffmpeg in synaptic, scroll down and make sure your libavcodec1d, ect say medibuntu at the end of the version 

Maybe also play back your video with mplayer from the command line, open a terminal and go (post output

mplayer /path/to/filename

(( if having trouble with path/name then just copy your video, drop in home folder and rename 1.flv
Then use 
mplayer 1.flv


(( if you install a recent mplayer, either built or from smplayer ppa's, you'll be fine
if you wish to do so and need some instr.'s, just ask

---

### Post by stoppage on 2009-08-04
o.k., I downloaded &#8222;PPA named mplayer for rvm&#8220; from [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
and now the file plays fine,one last question, what's the difference between both mplayers....deb [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) hardy main
and
deb-src [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) hardy main?
I installed the first version, it worked, I'm shooting in the dark here!
And obliged for your patience and help

---

