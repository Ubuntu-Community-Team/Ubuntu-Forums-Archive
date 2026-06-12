---
title: "Missing codecs; don't know which"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by maniacmusician on 2007-07-18
This is indescribably infuriating. I've installed every codec that I could think of or find, and yet, these files refuse to play. 

The files in question are AVI files, meaning they could be practically anything, really. I've got ffmpeg installed, all the xine plugins and codecs I could find, some divx/xvid plugins, and even the much hated w32codecs. Yet, I can't get any video from these files. What's even worse; I had them working in a previous installation.

Also, though the video doesn't play, the audio does, which is really not much help at all. But keep in mind that it **was** working on a previous installation of Ubuntu (probably Edgy). 

So, what are your suggestions? are there any file analysis tools that can look at the file and tell what type it is, and thus tell me what type of codec I need? Is there any feasible solution other than installing every codec under the sun?

Thanks

---

### Post by Gremlinzzz on 2007-07-18
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by maniacmusician on 2007-07-18
thanks, but this is not what I'm looking for. If you read my post carefully, you'll see that I've already got all the conventional codecs installed. Not to mention that you're talking about the gstreamer codecs and I'm using xine.

---

### Post by RomeReactor on 2007-07-18
Hi. Does this happen only with those particular avi files? do other avi files play fine? have you tried playing them with mplayer, and if so (and have the same results), have you tried changing its video driver?

If you have Beryl, try disabling it and see if it makes any difference (if you *do* have Beryl running, it may be related to a bug; see this entry in [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback")).  Another possible solution would be to convert them using AviDemux (it's in the repositories).

That's all I can think of at the moment.

---

### Post by Gremlinzzz on 2007-07-18
I have np playing avi files.
[http://video.google.com/videosearch?q=avi](http://video.google.com/videosearch?q=avi)
:guitar:

---

### Post by maniacmusician on 2007-07-18
> **RomeReactor said:**
> Hi. Does this happen only with those particular avi files? do other avi files play fine? have you tried playing them with mplayer, and if so (and have the same results), have you tried changing its video driver?

If you have Beryl, try disabling it and see if it makes any difference (if you *do* have Beryl running, it may be related to a bug; see this entry in [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback")).  Another possible solution would be to convert them using AviDemux (it's in the repositories).

That's all I can think of at the moment.
yes, it only happens with these particular .avi files. See, AVI is just a container; it can contain any type of video inside it, be it mpeg or wmv. So the problem is with these specific files.

It doesn't work in mplayer; mplayer doesn't even play the sound, it just throws out an error about not being able to initialize the video output.

I tried it without Compzi fusion running, and it didn't make a difference; still no video, just sound. 

i tried to open it with avidemux, and the error it gave me said "Error opening CODEC_ID_WMV3". So I'm assuming the codec I need is for WMV3...I'll search again, but I think that was supposed to be in w32codecs....

---

### Post by maniacmusician on 2007-07-20
<bump> help?

---

### Post by Gremlinzzz on 2007-07-20
Have you tried smplayer it plays alot of files normal mplayer doesn't and these codecs are different than the package in repositories.
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
hey if it don't work just uninstalll
sudo apt-get autoremove smplayer
:guitar:

---

### Post by Gremlinzzz on 2007-07-20
> **Gremlinzzz said:**
> Have you tried smplayer it plays alot of files normal mplayer doesn't and these codecs are different than the package in repositories.
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
hey if it don't work just uninstalll
sudo apt-get autoremove smplayer
:guitar:

and change the mpllayer and smplayer video too X11

---

### Post by maniacmusician on 2007-07-20
Holy crap, SMPlayer works! I didn't install any additional codecs, so the question is WHY? I will not rest until I get an answer.

Why does SMPlayer work and other things like Kaffeine, VLC, etc, don't work with this wmv3 class file? 

To clarify again, this is just the video stream. Audio works fine on VLC and kaffeine.

---

### Post by JJNova on 2007-07-22
> **Gremlinzzz said:**
> and change the mpllayer and smplayer video too X11

BEST, PIECE OF INFORMATION, EVAR!

---

### Post by dustrho on 2007-07-26
Just tried the last suggestion and SMplayer works for me! I'm not able to play my AVI videos! Thanks a ton.

---

### Post by mr_biggie on 2007-07-26
just go to synaptic and install the gstreamer plugins, dvix works with out a problem in totem gstreamer

---

