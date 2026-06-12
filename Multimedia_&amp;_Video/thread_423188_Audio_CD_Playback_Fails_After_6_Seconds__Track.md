---
title: "Audio CD Playback Fails After 6 Seconds / Track"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by JoelAV on 2007-04-25
Hey all,

I've just installed Xubuntu 7.04 on a PII-350 w/ 256M RAM, 6G HD.  I'm having problems playing plain old Audio CDs (remember those?).

Both GXine, and XFmedia will recognize the discs, grabbing the track info off CDDB (I guess).  When I try to play the disc, it will play exactly the first six seconds of each track before skipping on to the next track.

I've just determined that it is not playing through the audio cable hooked up to the sound card, but rather reading the digital audio over the IDE bus.  Audio still comes through the speakers with the audio cable unplugged.  The (24x) CD-ROM drive didn't work in DMA mode to install Xubuntu, so I disabled DMA for the install.  I just disabled it while running by doing "sudo hdparm -d0 /dev/cdrom" but this didn't seem to have any effect.  I assume that what's happening is that some combination of the drive/IDE interface isn't able to keep up with the audio tracks being ripped off the CD, so it's giving up and moving on to the next track.

But I don't want to do real-time audio ripping.  I just want it to play the CD's audio the old fashioned way, at 1x speed, through the audio cable.

1.  Why is this not the default behavior, or at least an easily configured option?
2.  How do I change this behavior?

To recap:  I just want a GUI player that will play audio CDs through the audio cable hooked up between the CD drive and the sound card.  I'm not afraid of using the command line to get it configured, but don't want to make the eventual user do so to play a CD.

Thanks in advance,
JCE

---

