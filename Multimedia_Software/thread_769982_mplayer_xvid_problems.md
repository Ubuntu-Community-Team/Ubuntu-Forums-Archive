---
title: "mplayer xvid problems"
date: 2008-04-27
forum: Multimedia Software
---

### Post by guitarj1d on 2008-04-27
After upgrading to Hardy I'm having trouble playing xvid movies in both vlc and mplayer,  when I full screen in VLC the video becomes all choppy and cuts out.  When I try opening with mplayer I get the following error:

[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.

if I change vo to x11 I can play the movies but can't fullscreen.  to solve this I added zoom="1" to my ~./mplayer/config file but then the video is choppy when I full screen.  can anyone help?

---

### Post by nkessler2000 on 2008-04-27
I'm having the exact same problem. Video performance is unacceptable in 8.04, but it worked okay in 7.10. I cannot use Xv for playback, either. If I do run xvinfo, I get the following

```

X-Video Extension version 2.2
screen #0
no adaptors present

```

I've got an ATI card, so maybe it has something to do with the new driver 8.04 uses. ATI are notorious for their crappy drivers.

---

### Post by guitarj1d on 2008-04-27
yep, I get the same output.  I'm downgrading to 7.10 for the time being.  I love the new firefox and file transfers feeds, but video playback is far more important

---

### Post by cor2y on 2008-04-27
it simply means no hardware xv for your particular video card.
There seems to be a bug with ubuntu and the built in closed source nvidia drivers if you didn't do a clean install, when you enable the hardware drivers they do not get used the system defaults to the open source drivers instead.
Note this only happens with the  -16 kernel update if you want hardware support while booting  theres the message to press the ESC key to see the grub menu do that and go to an earlier kernel the -12 one hardware closed drivers should in that.
Another way to get around this is to use the built in gnome media player totem with either the gstreamer or xine backend you won't get xv support but when you go fulllscreen at least the video will not be choppy.

---

