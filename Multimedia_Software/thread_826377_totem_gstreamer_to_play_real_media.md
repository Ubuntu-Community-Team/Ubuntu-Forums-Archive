---
title: "totem gstreamer to play real media"
date: 2008-06-11
forum: Multimedia Software
---

### Post by peteron on 2008-06-11
Anyone knows how to set up the totem gstreamer to play real media under ubuntu 8.04lts? No audio and No video

I tried Mplayer, but doesnot work. Only has audio but no video.

thanks a million.

---

### Post by wolfen69 on 2008-06-11
uninstall mplayer. then
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
then re-install mplayer and throw in vlc for good luck. it should work now.

---

### Post by peteron on 2008-06-11
thanks, but still error occurs
error opening/initialing the selected video_out (-vo) device

by the way, what do you mean by 'throw in vlc'?

---

### Post by MmmmJoel on 2008-06-12
VLC is another media player you can try. You can install with:
```
sudo apt-get install vlc
```

---

### Post by instinctive on 2008-06-12
Well I don't know which real media file type you're trying to play, but I've managed to play all my .rmvb files using totem. If you're not trying to play a .rmvb file this may work, I'm not sure as I've only tested .rmvb files.

Enable the medibuntu repo. Open up Synaptic Package Manager. Search for w32codecs and install it. (At this stage I already had the gstreamer packages installed so I'm not sure if they are required, so if this doesn't work ensure they are installed)

Now go to Add/Remove and install Totem (xine backend). You should now be able to play the .rmvb file by right-clicking it and selecting 'Open With' and use the command totem-xine.

I hope this works, please let me know.

---

### Post by Pjotr123 on 2008-06-12
Apply this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

And then this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

100 % multimedia coverage in about 20 minutes (depending on the speed of your internet connection).  :-)

---

### Post by yosumi on 2008-06-18
> **Pjotr123 said:**
> Apply this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

And then this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

100 % multimedia coverage in about 20 minutes (depending on the speed of your internet connection).  :-)

nice guide. got rmvb working. it was the missing 1%... XD

---

