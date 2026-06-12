---
title: "Unable to play wma files"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Ant01 on 2008-12-27
I am using Rythymbox Music Player and it seems I can't add wma files to my playlists it gives me a error "The GStreamer plugins to decode "unknown" files cannot be found.

---

### Post by howefield on 2008-12-27
Try here

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by raptorpenguin on 2008-12-27
I think to play files like wma, mp3, wav, and the like, you have to download a special codec package that you can find in the software repositories. The reason for these not being included with the Ubuntu operating system itself are because these formats are incompatible with the goals of Free Software, which Ubuntu is based upon. To get these codecs, go to the Synaptic Package Manager (if that it is still what it's called,I use Breezy Badger), and search for "gstreamer". From the results, mark these plugins for instalation (substitute x.x for the latest version number):

gstreamerx.x-plugins
gstreamerx.x-plugins-multiverse
gstreamerx.x-ffmpeg

After marking these and confirming download of all the dependencies that it asks you about, you should be set to go.

Alternatively, you could install Windows Media Player under Wine.

I am not sure if this method works, I haven't tried it. This was loosely derived from my "Beginning Ubuntu Linux" book that I checked out from the library.

---

### Post by raptorpenguin on 2008-12-27
Oh, and if you choose to install Media Player under Wine, you have to already have an activated Windows liscense to legally use Media Player under Wine.

---

### Post by Ant01 on 2008-12-28
There were a number  of plugins and files to choose so I loaded them all. Please explain how I load windows media player under wine?

---

### Post by gandaran on 2008-12-28
you can play any wma format (except wma DRM protected ones) with a xine based player or mplayer, rhythmbox or any gstreamer player can play wma files except wma lossless format
> Please explain how I load windows media player under wine?
you mean install? just run the wmp .exe package and follow the same install procedure just like in windows
if you want a perfect working windows media player under wine, install wmp 9 and DCOM98 and set wine to windows 98, 
install the k-lite codecs package too.
wmp 10 under wine can play the files but thats just about all it'll do, doesn't work perfectly, not worth installing.

---

### Post by cariboo on 2008-12-28
Instead of using a proprietary media player, why not just install the ubuntu-restriced-extras package, as well as the w32codecs and libdvdcss2 from the Medibuntu repositories. Installing the above packages will allow you to play almost all available audio/video files. THe ubnuntu-restricted-extras meta package will also install flash, java and the mscorefonts package.

To enable the Medibuntu repositories go [here]("http://help.ubuntu.com/community/Medibuntu"), be sure to scroll down and add the gpg key.

Jim

---

### Post by Ant01 on 2008-12-28
> **cariboo907 said:**
> Instead of using a proprietary media player, why not just install the ubuntu-restriced-extras package, as well as the w32codecs and libdvdcss2 from the Medibuntu repositories. Installing the above packages will allow you to play almost all available audio/video files. THe ubnuntu-restricted-extras meta package will also install flash, java and the mscorefonts package.

To enable the Medibuntu repositories go [here]("http://help.ubuntu.com/community/Medibuntu"), be sure to scroll down and add the gpg key.

Jim

Excuse me but I'm still learning my way around Abuntu. Not sure what I've done but it seems that the Rythym player is reading most of my wma files. I am a bit concerned about the Rythum player as it seems unstable. (closes by itself and looses playlists) I like the interphase of Rythum so am persuing with it.

I followed the above link and ran the following code as I am using Ubuntu 7.10
Ubuntu 7.10 "Gutsy Gibbon":
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Not sure what I must do now and don't know what you mean by "be sure to scroll down and add the gpg key."

---

