---
title: "True gapless-seamless playback with Amarock"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by lsutiger on 2007-03-30
I just got Amarok working, and I must say I am impressed. But there is one slight problem that iTunes fixed in the release before last. True gapless payback.
I have the setting in playback for no cross fading, but it seems to have a slight 'bump' of nothing between tracks. This can be aggravating when trying to listen to music that is supposed to be seamless. Is there a way to make this happen in Amarok?
If not, is there a program out there that has this functionality?
Thanx in advance!
Jude
chown -R us ./base :D

---

### Post by lsutiger on 2007-04-02
Hoppity, hoppity, hoppity....BUMP

---

### Post by vanadium on 2007-04-16
Probably, Amarok does gapless playback for file formats that are gapless, such as uncompressed WAV or OGG vorbis. Gapless mp3 playback depends on a trick implemented by lame. Tags that mark the start and the end of the actual audio are inserted into the file. it is then up to the player to recognize these tags and strip off the encoder padding at the start and at the end. As far as I know (I switched to Ubuntu one week ago, so beware), Amarok does not support that. The gapless solution I am using now is XMMS with the XMMS Crossfade Plugin. Both are easily installed from the Synaptic Package Manager.

---

### Post by WebDrake on 2007-11-03
What about gapless CD playback?

During a discussion on the KDE bug tracker
[http://bugs.kde.org/show_bug.cgi?id=127652](http://bugs.kde.org/show_bug.cgi?id=127652)

.... it was claimed that the bug is "not valid with proper hardware and a proper current software set".  Unfortunately no hints were offered as to how to GET a proper hardware and software set.

---

### Post by ssam on 2007-11-03
can amarok do a zero second cross fade? that should be equivilent to gapless

---

### Post by WebDrake on 2007-11-04
> **ssam said:**
> can amarok do a zero second cross fade? that should be equivilent to gapless

I tried that.  It always wants a minimum of 400ms for the cross-fade. :-(

---

