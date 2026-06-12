---
title: "[SOLVED] The familiar amarok/xine issue, except not"
date: 2008-06-15
forum: Multimedia Software
---

### Post by inci on 2008-06-15
Most of you will be familiar with the issue of Amarok not playing MP3 files unless you install some bunch of codecs. From 8.04 apparently that issue is resolved - everything worked froodily when I installed Amarok on my (originally Ubuntu, now pretty much Kubuntu) setup.

For a couple of weeks I had no issues, mostly love the player as I always have. Today I fire up my laptop, and Amarok tells me it "cannot play MP3 files". With some testing I managed to find out that it cannot play MP3 and OGG Vorbis but can play WMA and M4A, which thoroughly confused me.

By now I've reinstalled Amarok (including a complete wipe of all config files) and reinstalled libxine1-ffmpeg which supposedly holds the codecs for at least mp3. All to no avail, still get the same message.

Some have suggested that I install gstreamer, but I'll skip ahead of that mess and tell you that Amarok does not currently support gstreamer as an output engine, at least not through any packages in my repos. I've no clue where the actual issue lies, since I've reinstalled all packages I'd deem relevant.

Any suggestions? I can listen to music through other apps, but I'd like my favorite back <.<

(Edit: Might be of interest to know that the nightly build of Amarok 2 gives what looks like the same error, except it uses a different engine - phonon)

EDIT: Solved. Apparently this was an issue very much with xine - someone's had the same issue and fixed it by removing ~/.xine. Bit of a dirtyfix, and probably still a bug that needs fixing, but this helps.

---

