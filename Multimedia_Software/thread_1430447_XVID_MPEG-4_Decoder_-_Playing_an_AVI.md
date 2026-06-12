---
title: "XVID MPEG-4 Decoder - Playing an AVI"
date: 2010-03-15
forum: Multimedia Software
---

### Post by bobnutfield on 2010-03-15
Hello Everyone,

I thought the days of posting a question like this were well behind me.  I ran across a Blender tutorial video on the net and it is in the .avi format.  To my surprise, Firefox would not play it, I was asked if I wanted to search for a suitable plugin, and the needed plugin was XVID MPEG-4 Decoder, which I was sure I already had installed.  As a matter of fact I checked:

> libx264-67 is already the newest version.
libx264-67 set to manually installed.
libxvidcore4 is already the newest version.
libxvidcore4 set to manually installed.

Is this some sort of specially coded .avi, or am I missing something here?
Even VLC (which has never failed to play anything I could throw at it) would not play with the same error (XVID cannot be played, no way to fix this).

Anyone have any ideas?

Bob

---

### Post by mc4man on 2010-03-15
maybe start vlc from terminal with vlc -vv and try to play your .avi ( that is assuming it's local 

The output will be large - look at top for any plugins failing to load, otherwise anything of value will usually be about 90 lines in 

There's nothing special needed for xvid - vlc uses avcodec to decode (libavcodecXX

Check in synaptic and see what version of libavcodecXX you have (properties of package will show

Did you add any ppa's that may have installed a different libavcodecXX ? (or is install an upgrade from previous ubuntu release?

---

### Post by bobnutfield on 2010-03-15
> Did you add any ppa's that may have installed a different libavcodecXX ? (or is install an upgrade from previous ubuntu release?

Hello

Thank you for your reply.  I noted the above because I am on Karmic which was an upgrade (not a fresh install) from Jaunty. You may be on to something because Mplayer will not open, complaining about a missing libfaad.so.0 file, which is definitely installed.  The video I was trying to play is stream from the net, so I can't run it locally.

I have uninstalled and reinstalled libfaad and all the "ugly" gstreamer codecs, no luck.

---

### Post by mc4man on 2010-03-15
I've gotta go to work but..
There are numerous threads on the same deal for those that upped from jaunty to karmic - and just as many possible solutions 

If it were me I'd first ck. software sources and make sure no jaunty sources are enabled (inc. medibuntu), then just go into synaptic, search ffmpeg and remove all it's libs - libavcodecXX, libavformatXX, ect - up to 7 may be installed, ends with libswscale0

Some players and plugins would also be removed, no big deal, just re-install
(file - history in synaptic will show you.

Then I'd install libavcodec-extra-52, libavformat-extra-52 ect. and then the removed players, plugins.

With mplayer, if not removed when removing the current libavcodecXX then also remove and re-install after 

one of many
[http://ubuntuforums.org/showthread.php?t=1308235](http://ubuntuforums.org/showthread.php?t=1308235)

---

### Post by bobnutfield on 2010-03-15
Thank you, very much.  That will solve it.

EDIT:  With the info your provided, solved in 5 minutes.

Thanks again.

---

### Post by FrancoNero on 2010-05-05
don't have ffmpeg installed, still can't play xvid/mpeg4 files, as I've reported as a bug in launchpad (no reaction there).

my vlc of course plays the files... vlc plays everything. but i do have every coded known to man installed, I don't get why a) totem won't play it and b) why vlc isn't the default player on ubuntu


[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/573607](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/573607)

---

