---
title: "Video Playback very laggy"
date: 2011-10-07
forum: Multimedia Software
---

### Post by mkbolivian1 on 2011-10-07
Hey all, really new in ubuntu land, I'll respond later with more details about my system, I'm on the latest update, and my issue is I'm trying to watch a [video]("http://vimeo.com/29950141") on vimeo. 
I let the video buffer bar finish, and the video playback is still very choppy, laggy.. Makes watching videos pointless. Any help would be handy. I don't think it's a hardware issue.

---

### Post by mkbolivian1 on 2011-10-09
is this thing on?

---

### Post by beew on 2011-10-10
Probably a flash problem. Install the flashvideoreplacer addon for Firefox and gecko-media player from the repo. I am using fvr to watch the movie you linked to on an old laptop (1g of ram 1.6 GH cpu)  in high resolution with no lag at all, with flash the system would have crashed.

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

Very nice movie by the way, thanks for the link.

---

### Post by mkbolivian1 on 2011-10-13
> **beew said:**
> Probably a flash problem. Install the flashvideoreplacer addon for Firefox and gecko-media player from the repo. I am using fvr to watch the movie you linked to on an old laptop (1g of ram 1.6 GH cpu)  in high resolution with no lag at all, with flash the system would have crashed.

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

Very nice movie by the way, thanks for the link.

That is a great video. 
So i installed flashvideoreplacer, and tried to play the video, and it acted like it was going to work, but the video just sits on black. I also installed gecko-mediaplayer but no change. Any suggestions?

---

### Post by beew on 2011-10-14
Don't know if it is a graphic card problem or the streaming. Can you download the video and play it locally say with vlc or mplayer? Maybe that would give some hints fo what might be wrong.

You can download it by right clicking the flashvideoreplacer icon on Firefox's addon bar.

EDIT: Oh, I forgot the obvious, did you install Ubunty-restricted-extras? You should also install the packages non-free condecs and w32codecs from medibuntu
[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)

---

