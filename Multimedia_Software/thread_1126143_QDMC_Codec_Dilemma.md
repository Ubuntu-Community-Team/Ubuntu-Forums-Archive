---
title: "QDMC Codec Dilemma"
date: 2009-04-15
forum: Multimedia Software
---

### Post by highland_dreamweaver on 2009-04-15
Hi all,
I have a question driving me nuts! Simply... In Ubuntu Hardy... Where are the codecs (audio and video) stored?

I have a growing collection of Aviation clips, some in Quicktime's QDMC audio format. This applies to those clips that are of old aircraft. Most are QDM2 but all of these are .mov format files. The video for these files is fine but the audio on the selected few is non-existant. I have managed to isolate the problem and identify that the QDMC codec either isn't present or is not working.

In response to this problem (which affects all my video players, excepting Realplayer) I managed to identify the faulty codec then managed (from the Mplayer site) to download the codecs I require to correct the problem. Here is the issue though...

Having read the readme for Mplayer it lists a number of addresses in the system files where the codecs should be... Including the default location. But! Upon doing a search for them I found they don't exist! Not being very familiar with the file systems in Ubuntu! I'm now at a loss for what to do to correct it. I have the codecs... I know the problem (No QDMC or faulty operation)... but now I have no idea where to put them! 

Mplayer (least my instillation - A Medibuntu version) doesn't list a location either, which means that the codecs must be installed for all of my video and audio programs to use. I have searched high and low but I still have no idea where to find those little rascals! Hopefully before I lose the rest of my hair someone can point me in the right direction and tell me how to solve this dilemma.

Steve...

---

### Post by andrew.46 on 2009-04-16
Hi Steve,

I suspect that if you have the Medibuntu MPlayer all you have to do is to install the w32codecs from the same place and this should not only give you a full codec pack but will place then exactly where MPlayer can find them.

I was unable to find any of the older qdmc files in playable condition for testing but I found a couple of qdm2 files and tested this one:

[http://samples.mplayerhq.hu/A-codecs/QDM2/switzler084d_dl.mov](http://samples.mplayerhq.hu/A-codecs/QDM2/switzler084d_dl.mov)

with the svn MPlayer this played with success using libavcodec:

```

andrew@skamandros~/Desktop$ mplayer switzler084d_dl.mov 
MPlayer SVN-r29178-4.2.4 (C) 2000-2009 MPlayer Team

Playing switzler084d_dl.mov.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [SVQ3]  480x206  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Episode III Teaser Trailer
 author: starwars.com Hyperspace
 copyright: Copright (c) 2004 Lucasfilm Ltd.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsvq3] vfm: ffmpeg (FFmpeg Sorenson Video v3 (SVQ3))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 48.0 kbit/3.12% (ratio: 6000->192000)
**[COLOR="Red"]Selected audio codec: [ffqdm2] afm: ffmpeg (FFmpeg QDM2 audio)[/COLOR]**
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 206 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 480x206 => 480x206 Planar YV12 
A: 107.5 V: 107.7 A-V: -0.141 ct: -0.076   0/  0  2%  0%  3.1% 1 0 

Exiting... (End of file)

```

Mind you MPlayer should be able to play the older qdmc files as well by using the codec pack. A quick look at the available audio codecs shows:

```

andrew@skamandros~$ mplayer -ac help | grep 'qdm'
ffqdm2      ffmpeg    working   **[COLOR="Red"]FFmpeg QDM2 audio[/COLOR]**  [qdm2]
qdmc        qtaudio   working   **[COLOR="Red"]QuickTime QDMC/QDM2 audio[/COLOR]**  [QuickTime.qts]

```

Manually selecting the qdmc codec however seems to indicate that this particular codec performs a little poorly to say the least :-). So I suspect you may need a newer MPlayer, it depends on when FFmpeg implemented qdm2 decoding I guess.

Andrew

---

### Post by highland_dreamweaver on 2009-04-16
Hi Andrew,
Thanks for the tips. I'll check out Medibuntu's repository for the w32codecs you mentioned. Hopefully that will solve it for me! I don't have many QDMC files at the moment (phew!) but when one is collecting old movie and video clips you never know until you try to play it. I'm dying to uninstall the version of Quicktime I installed in Wine. I needed it only to check if it was the player or the codec, now that I know I can kiss it good bye.

Last time I checked with the Mplayer website my version was up to date and the update manager hasn't tried to complain that it is out of date but still worth checking. Once again many thanks!

Steve.

---

### Post by andrew.46 on 2009-04-16
Hi Steve,

> **highland_dreamweaver said:**
> Thanks for the tips. I'll check out Medibuntu's repository for the w32codecs you mentioned. Hopefully that will solve it for me!

The only problem might be that the required codec QuickTime.qts did no seem to work that well. The most effective codec was ffqdm2 which is part of libavcodec that comes with MPlayer itself (imported from FFmpeg). Thus the codec pack might not help you. Test your own copy:

```
mplayer -ac help | grep 'qdm'
```

> Last time I checked with the Mplayer website my version was up to date and the update manager hasn't tried to complain that it is out of date but still worth checking.

Unfortunately the Ubuntu repository carries a version (rc2) that has been declared outdated by the MPlayer website and there are no plans to update this by Ubuntu. This version is almost 2 year old. If you are using Hardy Heron you might be interested in updating your copy to a newer copy by following [this guide]("http://ubuntuforums.org/showthread.php?t=558538"). This is the version I am using to play the qdm2 files.

All the best,

Andrew

---

### Post by highland_dreamweaver on 2009-04-17
Thanks for the added info and links, but for the moment your tip paid off! I did a search in Synaptic for w32codecs and discovered that while it was there it hadn't been installed yet! Since i installed it though I have to say that that it was an outstanding success. 

Where as Mplayer couldn't play QDMC before, that problem was also true of Gnome Mplayer,Totem and Lives! After confirming the result I very happily gave my Wine installed Quicktime player the flick!
I did notice though that Totem is the only one that didn't benefit from the install... though with Mplayer working I am not too distressed about this problem. After all it also plays my .flv files. 

Maybe if I provide a link to the codecs it might take the hint though given its involvement with Xine library's maybe that is what I should concentrate on for the moment. Still I am very grateful Andrew! I would have expected that when Mplayer was updated to the Medibuntu version that it would have included the codecs to play files with but then I guess that may have been too obvious! 

Anyway, I owe my current joy to your solution... In hind sight I should have thought of it too. 

Steve

---

### Post by andrew.46 on 2009-04-17
Hi Steve,

I am enormously pleased that you have found a resolution to your problem! Not sure about Totem as I pretty much only use MPlayer, what more would you need after all :-).

All the very best,

Andrew

---

