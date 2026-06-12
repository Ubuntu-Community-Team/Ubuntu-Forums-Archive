---
title: "is Gstreamer necessary for Ubuntu or for Ubuntu apps?"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by eeried on 2006-09-12
Hello,

I'm using Xubuntu at the moment and I've read users must install quite a batch of gstreamer stuff for the sound to work in Xfmedia. BTW, this was also the case in Ubuntu Breezy.

I also installed VLC.

My question is are the various gstreamer packages (the gstreamer framework) necessary only for multimedia apps already installed in Ubuntu or for certain multimedia apps, (xine, perhaps?)? Or is it necessary for any app you install in Ubuntu?

VLC seems to work fine without any gstreamer stuff, but perhaps this is mere chance. I installed VLC, the alsa plugin for VLC and ffmpeg, lame, faad, sox, mjpegtools. I only watched home-made video on CD and the Ubuntu experience.ogg video file included in Xubuntu (Examples). I now have sound which I didn't have with xfmedia on its own -- xfmedia is rather bare so I uninstalled it.

Many thanks in advance 8-)

---

### Post by JAwuku on 2006-09-13
Actually, you can use the xine library instead of gstreamer, as for example:

```
sudo apt-get install xine-ui
```

or

```
sudo apt-get install totem-xine
```

You need the w32codecs packages from the plf repositories as well.

Personally, I use gstreamer 0.10 in my dapper install, as I seem to be able to handle more file formats that way.

---

### Post by eeried on 2006-09-19
Many thanks for the information, JAwuku! I've learnt something

Now one point still isn't clear to me: is Gstreamer linked to Ubuntu or is it linked to any other Debian-based distro or is it linked to Gnome?

Sorry for being so ignorant!

:-({|=

---

### Post by TheMono on 2006-09-19
It's linked to Gnome predominantly. Gstreamer 0.8 was rubbish, but in picking between Gstreamer 0.10 and Xine it's really six one way half a dozen the other.

---

