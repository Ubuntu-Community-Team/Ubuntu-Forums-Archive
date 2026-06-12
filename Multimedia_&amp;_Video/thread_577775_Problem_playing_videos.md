---
title: "Problem playing videos"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by Jonathan Métillon on 2007-10-16
Hi,

Maybe that's caused by a recent update. For sure it's not an hardware update or any new software installation.

Everything used to work fine until video playback broke. The symptoms vary with the type of movie and the weird behaviors vary with the software.

In all case, VLC does not open video output. I only have soundtrack. For some type of video I got:

```
VLC media player 0.8.6 Janus
[00000335] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000337] main video output error: no video filter module matched "scale"
[00000337] main video output error: no suitable vout module
[00000337] main video output error: cannot delete object (337, (null)) with children
[00000303] main decoder error: failed to create video output
No accelerated IMDCT transform found
[00000280] main playlist: stopping playback
```And for others:

```
VLC media player 0.8.6 Janus
[00000348] main video output error: no video filter module matched "scale"
[00000348] main video output error: no suitable vout module
[00000348] main video output error: cannot delete object (348, (null)) with children
[00000303] main decoder error: failed to create video output
[00000350] main video output error: no video filter module matched "scale"
[00000350] main video output error: no suitable vout module
[00000350] main video output error: cannot delete object (350, (null)) with children
[00000303] main decoder error: failed to create video output
[00000280] main playlist: stopping playback

```

With MPlayer, if from Nautilus I click right on the file and *Open with MPlayer*, any type of video plays correctly but when going fullscreen, the video does not expand to screen size, it just keep original size on a black screen.

If I launch it from command line, this time I get a correct fullscreen. But I don't like this software because I don't have the crop feature like VLC.

Then there's Totem, which plays everything correctly and fullscreen works, but for some kind of files I've got a weird green stripping on the video!

For this kind of videos, I can see this output from command line:

```
** (totem:30211): WARNING **: Size 348160 is not a multiple of unit size 345600
```

Any idea? :confused:

---

### Post by perixx on 2007-10-18
Hey there...

I'm having trouble in finding a capable multimedia player as well. Tried native Xubuntu's Gxine that didn't work at all. Then I tried some Audio players, which were mostly fine. Mplayer doesn't satisfy my needs, as doesn't yours - no decent window resizing options availible and to many formats that won't work + video drivers that seem to be half-baken.

Currently I'm messing around with VLC also; I'm not that experienced in the ways of Ubuntu or videos... but maybe you could try another video renderer in your VLC advanced settings - depending on your desktop version. Mine is Xfce, so 'X11' works pretty nice.

As your error messages are reading something about 'scale' - maybe your got your screen's aspect ratio or the screen scaling set wrong/too high?   

Also, you could try different video formats and change the codec in use by VLC for testing purposes.

Do you have the accelerated/restriced video drivers installed for your graphics card? Perhaps that's that problem...

If nothing else works, I'd uninstall all multimedia apps and just install VLC again, afer that the extended codecs.


greetz

perixx

---

