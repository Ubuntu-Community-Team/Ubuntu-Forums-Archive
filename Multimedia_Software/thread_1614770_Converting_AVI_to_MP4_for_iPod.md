---
title: "Converting AVI to MP4 for iPod?"
date: 2010-11-06
forum: Multimedia Software
---

### Post by jfed on 2010-11-06
I've got a bunch of episodes of Psych, that I'd like to put on my iPod touch. The problem is the only video codec that iPod touches can playback is MP4. My Psych episodes are AVIs. I've heard of and used mencoder to change video codecs before, but I'd have no idea how to write my own script for it. What I was thinking of doing is using Avidemux to convert it? You know..
Open the AVI in adivemux
Switch the video to MP4 Mpeg-4
switch the audio to MP3 lame
and i'm pretty sure then i have to save it.

Honestly i'm not too firmiliar with codecs and containers but its telling me that rather than Xvid(which i think it was previously) the video codec is MP4 and the audio is MP3, and the container is AVI. First of all is this correct? Did i get the codec/container right?

Secondly will this work on my iTouch? I guess dealing with AVIs as a container is ok as long as the video codec is MP4? rather than like OGG or something? Ugh i'm so confused, i've just been rambling..

Ok. First of all do i have codecs/containers down? Am i correct with my assumptions?
Second, I am correct that the CODEC is the problem, it must be MP4 to play back on the iPod? the container being AVI has nothing to do with it? (i'm basing this off of the fact that i know the only "codec" iPods can playback is MP4)

If you actually read this loquacious thread i thank you, and i also thank you for any input you could contribute. Thanks.

Edit: are there any other possible ways to convert an AVI to an MP4?

---

### Post by shantiq on 2010-11-06
```

```probably the best tool for this is [handbrake]("https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots")   handbrake is very easy to use   

 to install read Technical details about this PPA on the linked page




=======================================================================================================
and of course ffmpeg but that is a little more involved although there is a gui let me have a look


yes it is Winff  AND maybe that is the quickest option for you here 

so first  ```
sudo apt-get install ffmpeg winff
```



then simply go to applications/sound and video/winff

really easy to use and there are a zillion settings

---

