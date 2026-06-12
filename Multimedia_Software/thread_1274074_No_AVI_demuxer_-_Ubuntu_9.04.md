---
title: "No AVI demuxer - Ubuntu 9.04"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Dontknowwhat on 2009-09-24
Hi. This is my first post here.

I have a big problem. When i try to open any kind of .avi file in VLC player it says that there is no proper decoding unit and that VLC player doesn't support xvid format.

When i try to open videos in Gnome Subtitles, it says:
*A AVI demuxer plugin is required to play this stream, but not installed*
*You do not have a decoder installed to handle this file. You might need to install the necessary plugins.*

When i try to play these video files, only sound plays, but not the video. Only in MPlayer do both play, but i need that everything would work in all programs.
Can anyone help me and tell me where can i find these plugins to decode avi files? I have all gstreamer plugins installed, at least i think so.

Can anybody help me?

---

### Post by Jose Catre-Vandis on 2009-09-24
Look [here]("http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=6&url=http%3A%2F%2Fubuntuforums.org%2Farchive%2Findex.php%2Ft-725034.html&ei=BEK7Ssj9LMa5jAfc_tW7Cw&rct=j&q=vlc+requires+avi+demuxer&usg=AFQjCNFif2wrwZohxnbiD55EWk74BbGRAw&sig2=JPb49PRvD1oZQp4Tewezng") for possible solutions?

---

### Post by Dontknowwhat on 2009-09-24
No, it doesn't work.

Which gstreamer plugins do i need?

---

### Post by Jose Catre-Vandis on 2009-09-24
You "shouldn't" need any, as VLC comes fully stocked with codecs.

Try installing:
```
sudo apt-get install ubuntu-restricted-extras
```
and see if that helps

---

### Post by Dontknowwhat on 2009-09-24
I already have that - it doesn't work. Something must be wrong with gstreamer plugins.

---

### Post by Jose Catre-Vandis on 2009-09-24
OK, open up Synaptic and search on gstreamer, check if you have the following installed, if not install them:

They all start with gstreamer0.10-
alsa
ffmpeg
gnomevfs
pitfdll
plugins-bad
plugins-bad-universe
plugins-good
plugins-base
plugins-ugly
plugins-ugly-universe
pulseaudio
x

and also
libgstreamer0.10-0
libgstreamer-plugins-base0.10-0

If still no success, uninstall vlc and reinstall, uninstall all the above and reinstall.

or

Use mplayer :)

---

