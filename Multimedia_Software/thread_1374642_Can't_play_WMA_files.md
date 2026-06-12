---
title: "Can't play WMA files"
date: 2010-01-07
forum: Multimedia Software
---

### Post by jazzgossen on 2010-01-07
Since upgrading to 64-bit Karmic, I can't play any WMA files, neither in Rhythmox, Totem, VLC, or mplayer. It used to work well with 64-bit Intrepid.

I've added the medibuntu repos and installed ubuntu-restricted-extras (including w64codecs). Still, when rhythmbox or totem opens a WMA file, they search for an appropriate codec and don't find anything.

What else could I do?

---

### Post by Chronon on 2010-01-07
Is it only WMA that you're having problems with?  I tested a couple of WMAs on my system (64-bit Kubuntu 9.10) and found that both VLC and Amarok played them fine.  I only have a limited number of WMA tracks, however, so I am not able to broadly test compatibility with various versions of the codec.

---

### Post by Yellow Pasque on 2010-01-07
Use a 32-bit mplayer and install w32codecs.

---

### Post by mc4man on 2010-01-07
You may want to idenify what type of wma you have,- 

wma2 should playback with any player on 64 bit.

for wma3 as mentioned a 32 bit bit mplayer would do, though wma3 is available by other means

If you build a more recent or current mplayer than you'll get wma3 decoding thru the built-in libavcodec, how-to [here]("http://ubuntuforums.org/showthread.php?t=1305181")

For vlc on 64 bit it's a bit more involved - best way would be a current static [build of ffmpeg]("http://ubuntuforums.org/showthread.php?t=786095"), and then build vlc.  (wma3 decoding thru avcodec then will be enabled in your 64 bit vlc

wmal (lossless) is only possible in 64 bit with the aforementioned 32 bit mplayer build and install ( a bit of work, but certainly do-able.

or running a windows mplayer thru wine  (limited use, but does work well with audio files. gui only

edit:
actually I would think you should get wma3 thru installing a mplayer build from the [rvm ppa ]("https://launchpad.net/~rvm/+archive/mplayer")( dev of the mplayer frontend -[ smplayer]("https://launchpad.net/~rvm/+archive/smplayer")

---

