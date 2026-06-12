---
title: "video(avi): sound but no image??"
date: 2010-09-20
forum: Multimedia Software
---

### Post by leonseifert on 2010-09-20
When I want to watch an avi file on my laptop I only hear the sound but do not see any Image(only black).
I have bought a new laptop([SIZE=1]Acer Aspire One 532) and as I was not so happy with windows 7 starter I installed Ubuntu[/SIZE] Destop Edition 10.04. The first time the Video-Player of ubuntu downloaded the avi codec(so I am sure it is not caused by this) and played the sound but just showed a back screen. 
I tried some players(vlc...) and downloaded a lot of thinks that looked as if they could be an avi codec(At that time I thought it was caused by this). Now I installed ubuntu again so that all that is off.
If I open a window over the black surface of the video and close it, the picture of the window remains on the screen.
I read some things in this forum but non did halp( I turned the contrast higher as it once was the problem but is is still the same)
I have no Idea what it can be, probably something stupid what I just don see, Any help is welcome.:confused:

---

### Post by cliffordstoll on 2010-09-20
first of all download all the codex and then try to watch .avi video with classic widows media player... once you install the codex the classic media player will be installed itself... try it might work... coz it worked for my compaq...

---

### Post by leonseifert on 2010-09-21
sorry but I did not get it totally. I have installed GStreamer-Plugin for FFMPEG Video(FFmpeg-Extension for GStreamer) And I have tried to install widows media player but I only got to download an exe file which I could not open.:(
I searched for another codec but did not find one. (do I have to download one from the internet (not shown in the packed list of ubuntu?))

---

### Post by Yellow Pasque on 2010-09-21
What video codec is it? (avi is just a container)
BTW, I'm pretty sure "cliffordstoll" is just a spambot ;)

---

### Post by SeijiSensei on 2010-09-21
Try installing [SMPlayer](http://smplayer.sourceforge.net) and see if that helps.  It's maintained in the Ubuntu repositories, so you can install it simply by typing 'sudo apt-get install smplayer' in a Terminal window.  If you're using a package manager like Synaptic or KPackageKit you can download it that way instead.

---

### Post by macem29 on 2010-09-21
trying to follow the order of what you've done, new netbook came with win7, trashed that and put 10.04 on it,
installed a pile of stuff and video doesn't work, installed ubuntu again...is that correct ?...I'd advise being
careful with codec installations, more is not better, more will cause grief, if you have a fresh ubuntu install I'd
ignore the default player and install VLC, comes with everything you need...tell us more about this media 
that won't play

---

### Post by leonseifert on 2010-09-21
ok to be sure it is not caused by other files I put ubuntu on my lap gain and deleted all the previus data.
then I installed vlc player and with this I could start vob, avi and divx files without downloading any codec.
With vlc I checked the codex and found this. mpgv(vob file), xvid(avi file) and DX50(divx file).
I have still a back screen and sound. Then I noticed that when I play a video a maybe two pixel high appears at the very top of my second screen. This moves similar as a very little piece of a video could do. So I thought that maybe the pictures are justed played too hight( and a bit too far left). But I did not find a way to change that.(by the way the installation of SMplayer by terminal worked perfect but did not change anything but still thanks for the advice)

---

### Post by leonseifert on 2010-09-21
I just found out that if I use only one screen everything works all right(no matter which)...only if both are turned on the pictures seem to be shown in the wrong place. Sorry I came out with that so late and thanks for all your help

---

### Post by macem29 on 2010-09-21
are you talking about an external monitor attached to the netbook?

---

### Post by leonseifert on 2010-09-22
yes exact that.
The monitor if my netbook is quite small so I connected it to a bigger one.

---

