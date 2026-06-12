---
title: "Totem DVD or WMV?"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by newman on 2007-09-18
HELP! This is frustrating me to no end. I've installed all the plugins , etc. for Totem-gstreamer and it plays encrypted DVD's and WMV files(not perfectly, but it plays them). However, if I try to skip to the next DVD chapter or forward it stops playing.  I re-open Totem and I get an error message that I don't have the proper plugins, and I have to eject and reload the DVD and restart Totem. If I install Totem-Xine I get DVD working fine, but no WMV (error message : Video codec 'Windows Media Video 9' is not handled. You might need to install additional plugins to be able to play some types of movies). VLC works, but when I open a new file it opens a new window - very frustrating, and I can't seem to find a setting for opening  the new file in the same open window.  I like to have just one media player that handles everything, and not a billion different players installed. I've also tried mplayer. I like Totem because it's simple and if I could get it to open all media files it would be nice. Also, does Totem-gstreamer play subtitles in DVD's?

---

### Post by linuxwizard on 2007-09-20
Suggestion i would check to make sure you have all codecs.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This shows Totem play DVDs with menus and subtitles
[https://help.ubuntu.com/community/MultimediaApplications](https://help.ubuntu.com/community/MultimediaApplications)

---

### Post by newman on 2007-09-20
I've got all the codes. I think it may be a problem with gstreamer and totem. I'm now using vlc to play DVDs and Totem-gstreamer to play other files. I wonder if has something to do with the fact that I'm using ubuntu64

---

### Post by newman on 2007-09-20
ahhh

I may have found something...


> Note : While Totem-gstreamer can play a DVD automatically when it is inserted into the DVD drive, it cannot navigate the DVD nor play it by selecting Movie &#8594; Play Disc 'DVD Name'. If u use vlc media player u can navigate through the menu, forward in the movie and select subtitles. Just select open disc, probe Disc(s) and click ok. 

---

