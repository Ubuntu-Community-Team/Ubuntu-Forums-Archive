---
title: "MP4 Codec for Ubuntu?"
date: 2012-12-12
forum: Multimedia Software
---

### Post by Malsasa on 2012-12-12
But after installing ubuntu-restricted-extras, my totem still don't play .mp4 file yet. Now what should I do?

---

### Post by oldos2er on 2012-12-12
Post moved to its own thread.

---

### Post by BicyclerBoy on 2012-12-12
Depends what you mean by mp4..
DivX/XVif mpeg4-asp
apple Qtime mov m4v 
H264AVC mpeg4 layer10

Totem uses gstreamer backend..
Depending on what you have installed then totem should have popped up a request to search/install required parser/codecs..
There is a heap of gstreamer packages you can try to install
- plugins good
- plugins bad
- plugins ugly
- ffmpeg (AFAIK broken in 12.04)

Use synaptic package manager search "gstreamer"

Bad news:
But even after compiling gstreamer-ffmpeg from source "totem" still can not play H264.

Could just give up on "totem" & try SMplayer.

---

### Post by SeijiSensei on 2012-12-12
> **BicyclerBoy said:**
> Could just give up on "totem" & try SMplayer.

+1 for SMPlayer.  

```
sudo apt-get install smplayer
```

will install SMPlayer and the mplayer program it uses.

---

### Post by andrew.46 on 2012-12-13
If you would also like to stay up to date with the latest SMPlayer you can also add a PPA that the SMPlayer developer runs:

```

sudo add-apt-repository ppa:rvm/smplayer && \
sudo apt-get update && \
sudo apt-get -y install smplayer smtube smplayer-themes

```

Great frontend for the commandline MPlayer!

---

### Post by evilsoup on 2012-12-13
There's no need for an average user to need to keep up with the latest version, the one in the repos should suit most people's needs. So the OP should only use the PPA if there's something in the repository version that isn't working for them.

---

### Post by FakeOutdoorsman on 2012-12-13
That's boring.

---

### Post by mc4man on 2012-12-13
> **Malsasa said:**
> But after installing ubuntu-restricted-extras, my totem still don't play .mp4 file yet. Now what should I do?
You haven't said what release of Ubuntu or provided any info on your non-playing file(s)

If you're on 12.04 or 12.10 then there is a gstreamer bug affecting many AVC vid's that will prevent playback thru a gstreamer player such as totem
(mainly AVC 1 Baseline - L2.1, Baseline - L1.1 & some others

it's been fixed for some time but not yet in 12.10 repos, there is a testing ppa that contains the patched plugin, noted in "Current workaround:" in bug description
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

---

### Post by andrew.46 on 2012-12-13
> **evilsoup said:**
> There's no need for an average user to need to keep up with the latest version, the one in the repos should suit most people's needs. So the OP should only use the PPA if there's something in the repository version that isn't working for them.

I guess the issue with that is not so much missing out on new features but also not benefiting from improvements and bugfixes to security problems. These fixes are not backported to older versions.

---

### Post by monkeybrain2012 on 2012-12-13
> **andrew.46 said:**
> I guess the issue with that is not so much missing out on new features but also not benefiting from improvements and bugfixes to security problems. These fixes are not backported to older versions.

+1. Never understand the "stick to the repo version" advice especially for multi-media stuffs, though missing out new features is also important to me.

As a general point, ppa is one of the killer features of UBuntu IMO. If not for it I would be using Debian by now (I do compile from source some times but can't beat ppas for convenience)

---

