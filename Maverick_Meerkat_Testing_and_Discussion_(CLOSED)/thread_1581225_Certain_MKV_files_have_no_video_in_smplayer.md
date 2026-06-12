---
title: "Certain MKV files have no video in smplayer"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by davrosuk on 2010-09-24
I have noticed an issue with smplayer on Maverick where I get sound but no video. What's particularly odd is that the file will play in mplayer (and VLC). I thought it must have been something I broke on my build, so I built a VirtualBox, installed smplayer and I got the same issue.

A summary of things I've ruled out: 

* its not just that particular build of smplayer as I've compiled from source the latest version and it still happens!

* its not specifically this machine as the same thing happens on a VirtualBox (fresh install of 10.10)

* Its not the location they're running from - the files react the same wherever they are run from

Why do I want to use smplayer over mplayer? I can't ever seem to get Dolby Digital to work over SP/DIF using mplayer. It works fine using smplayer

I'm aware that smplayer is only a wrapper around mplayer - so if there are any useful hints and tips, I'm all ears!

---

### Post by recluce on 2010-09-24
I have had many issues with smplayer (and mplayer) lately, some with basic things like mp3 playback. 

Rather than fight these problems all the time, I have moved to VLC for the most part. To get an up to date version of VLC (including VDPAU for NVidia), look for the cutting-edge-multimedia ppa on launchpad.

---

### Post by endotherm on 2010-09-24
for (s)Mplayer I recomend installing it from the RVM ppas
[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")
[https://launchpad.net/~rvm/+archive/smplayer]("https://launchpad.net/%7Ervm/+archive/smplayer")

that way your versions of mplayer and smplayer will be largely compatible. until recently the version of mplayer refered to by the gmplayer package (the default mplayer package in the repos) was horribly out of date. every once in a while the repo maintainers get caught up, but they fall behind again just as quickly.

a log of people have also had issues with the LibAVCodec5.2 update a few months ago. might be worthwhile to see if there are hints that your issue is related.

---

### Post by davrosuk on 2010-09-24
Cheers for the suggestions...

I've now confirmed that its a bug affecting Maverick's versions of mplayer+smplayer as exactly the same thing happens on another machine I've built (ati instead of nvidia gpu).

As for VLC: I have an issue with that too at the moment. Periodic audio "drop-outs" when playing anything over passthrough - I have optical SP/DIF for AC3 and DTS playback.

---

### Post by endotherm on 2010-09-24
I've always hated the low quality of VLCs dithering and that green color inversion it sometimes gets when the screen has too much action. is it any better these days? 
I've always liked that it will play anything, but I always use it as the last resort.

---

### Post by davrosuk on 2010-09-25
Its certainly a regression from Lucid as I've just checked that. Mplayer in Maverick is rc4 which is newer than Lucids. So my next step is going to be fiddling with downgrading my mplayer to rc3, unless there is a better idea that is :-)

---

### Post by davrosuk on 2010-09-25
Any idea how to install an older version of something (when the newer version is in the official repository)?

---

### Post by Starks on 2010-09-25
> **davrosuk said:**
> Any idea how to install an older version of something (when the newer version is in the official repository)?
That MPlayer/SMPlayer repo is really old.

This one is constantly updated: [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)
(feel free to ignore the instructions, they are superfluous)

---

### Post by davrosuk on 2010-09-25
I have the solution! 

It looks like the mplayer guys have being playing around with the demuxing of MKVs recently (in the last couple of months). The end result seems to be that certain files lose the video track in the process. To fix playback so that all your MKVs work, add the following to your ~/.mplayer/config file:

> [extension.mkv]
demuxer=mkv

---

### Post by endotherm on 2010-09-25
> **Starks said:**
> That MPlayer/SMPlayer repo is really old.

This one is constantly updated: [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")
(feel free to ignore the instructions, they are superfluous)
don't you need the commercial CoreAVC MKV codec to run that version?
as I understand it, RVM is the maintainer for Mplayer, so do you think this branch is "better" than the RVM PPAs? if so I may have to give it a try

---

