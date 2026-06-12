---
title: "Smplayer playlist file &quot;open with&quot; problem"
date: 2018-12-05
forum: Multimedia Software
---

### Post by ra7411 on 2018-12-05
Smplayer (video player) creates xx.m3u playlist files. 

These xx.m3u stubbornly refuse to change the default "open with". On my setup, Audacious (audio player) somehow got assigned as default "open with" and I can't change it in properties to reset as the default opener.

Any ideas? Maybe a file edit somewhere?

Thanks

---

### Post by mc4man on 2018-12-06
Post the contents of ~/.config/mimeapps.list, preferably in a code box

---

### Post by ra7411 on 2018-12-08
> **mc4man said:**
> Post the contents of ~/.config/mimeapps.list, preferably in a code box

Here's mimeapps.list (I don't know how to do a code box).


```
[Added Associations]
application/x-partial-download=audacity.desktop;
application/x-matroska=avidemux2.7-qt5.desktop;smplayer.desktop;
audio/midi=audacious.desktop;
audio/mp3=audacious.desktop;
audio/mp4=audacious.desktop;
audio/mpegurl=audacious.desktop;
audio/ogg=audacious.desktop;
audio/prs.sid=audacious.desktop;
audio/x-flac=audacious.desktop;
audio/x-it=audacious.desktop;
audio/x-mod=audacious.desktop;
audio/x-mp3=audacious.desktop;
audio/x-mpeg=audacious.desktop;
audio/x-ms-asx=audacious.desktop;
audio/x-ms-wma=audacious.desktop;
audio/x-musepack=audacious.desktop;
audio/x-s3m=audacious.desktop;
audio/x-scpls=audacious.desktop;
audio/x-stm=audacious.desktop;
audio/x-wav=audacious.desktop;
audio/x-xm=audacious.desktop;
video/ogg=smplayer.desktop;
video/x-theora+ogg=smplayer.desktop;
video/x-theora=smplayer.desktop;
video/x-ms-asf=smplayer.desktop;
video/x-ms-asf-plugin=smplayer.desktop;
video/x-ms-asx=smplayer.desktop;
video/x-ms-wm=smplayer.desktop;
video/x-ms-wmv=smplayer.desktop;
video/x-ms-wmx=smplayer.desktop;
video/x-ms-wvx=smplayer.desktop;
video/divx=smplayer.desktop;
video/msvideo=smplayer.desktop;
video/vnd.divx=smplayer.desktop;
video/x-avi=smplayer.desktop;
video/vnd.rn-realvideo=smplayer.desktop;
video/mp2t=smplayer.desktop;
video/mpeg=smplayer.desktop;
video/mpeg-system=smplayer.desktop;
video/x-mpeg=smplayer.desktop;
video/x-mpeg2=smplayer.desktop;
video/x-mpeg-system=smplayer.desktop;
video/mp4v-es=smplayer.desktop;
video/x-m4v=smplayer.desktop;
video/quicktime=smplayer.desktop;
video/webm=smplayer.desktop;
video/3gp=smplayer.desktop;
video/3gpp=smplayer.desktop;
video/3gpp2=smplayer.desktop;
video/vnd.mpegurl=smplayer.desktop;
video/dv=smplayer.desktop;
video/x-anim=smplayer.desktop;
video/x-nsv=smplayer.desktop;
video/fli=smplayer.desktop;
video/flv=smplayer.desktop;
video/x-flc=smplayer.desktop;
video/x-fli=smplayer.desktop;
video/x-flv=smplayer.desktop;
video/mp4=org.gnome.Totem.desktop;avidemux2.7-qt5.desktop;smplayer_enqueue.desktop;audacity.desktop;mpv.desktop;
audio/x-ape=smplayer.desktop;
image/jpeg=viewnior.desktop;
audio/x-mpegurl=smplayer.desktop;org.gnome.Totem.desktop;rhythmbox.desktop;
audio/mpeg=audacity.desktop;

```
```
[Default Applications]
audio/mpeg=audacious.desktop
video/mp4=smplayer.desktop
video/x-msvideo=smplayer.desktop
application/x-matroska=smplayer.desktop
video/x-matroska=smplayer.desktop
audio/x-vorbis+ogg=audacious.desktop
audio/midi=audacious.desktop
audio/mp3=audacious.desktop
audio/mp4=audacious.desktop
audio/mpegurl=audacious.desktop
audio/ogg=audacious.desktop
audio/prs.sid=audacious.desktop
audio/x-flac=audacious.desktop
audio/x-it=audacious.desktop
audio/x-mod=audacious.desktop
audio/x-mp3=audacious.desktop
audio/x-mpeg=audacious.desktop
audio/x-ms-asx=audacious.desktop
audio/x-ms-wma=audacious.desktop
audio/x-musepack=audacious.desktop
audio/x-s3m=audacious.desktop
audio/x-scpls=audacious.desktop
audio/x-stm=audacious.desktop
audio/x-wav=audacious.desktop
audio/x-xm=audacious.desktop
video/x-ogm+ogg=smplayer.desktop
video/ogg=smplayer.desktop
video/x-theora+ogg=smplayer.desktop
video/x-theora=smplayer.desktop
video/x-ms-asf=smplayer.desktop
video/x-ms-asf-plugin=smplayer.desktop
video/x-ms-asx=smplayer.desktop
video/x-ms-wm=smplayer.desktop
video/x-ms-wmv=smplayer.desktop
video/x-ms-wmx=smplayer.desktop
video/x-ms-wvx=smplayer.desktop
video/divx=smplayer.desktop
video/msvideo=smplayer.desktop
video/vnd.divx=smplayer.desktop
video/x-avi=smplayer.desktop
video/vnd.rn-realvideo=smplayer.desktop
video/mp2t=smplayer.desktop
video/mpeg=smplayer.desktop
video/mpeg-system=smplayer.desktop
video/x-mpeg=smplayer.desktop
video/x-mpeg2=smplayer.desktop
video/x-mpeg-system=smplayer.desktop
video/mp4v-es=smplayer.desktop
video/x-m4v=smplayer.desktop
video/quicktime=smplayer.desktop
video/webm=smplayer.desktop
video/3gp=smplayer.desktop
video/3gpp=smplayer.desktop
video/3gpp2=smplayer.desktop
video/vnd.mpegurl=smplayer.desktop
video/dv=smplayer.desktop
video/x-anim=smplayer.desktop
video/x-nsv=smplayer.desktop
video/fli=smplayer.desktop
video/flv=smplayer.desktop
video/x-flc=smplayer.desktop
video/x-fli=smplayer.desktop
video/x-flv=smplayer.desktop
image/jpeg=viewnior.desktop
audio/x-mpegurl=rhythmbox.desktop
```

---

### Post by mc4man on 2018-12-10
You have 2 lines each for mpegurl for both added & default. (audio/x-mpegurl= & audio/mpegurl=

Either all have to show smplayer.desktop or remove the unneeded lines
Easiest would be to delete this line, both in the [Added Associations] section & in the [Default Applications] section
```
audio/mpegurl=audacious.desktop;
```

Otherwise you'd need to add to those 2 lines like,
In the Added section -  (position doesn't matter
```
audio/mpegurl=audacious.desktop;smplayer.desktop;
```

In the Default section -  
```
audio/mpegurl=smplayer.desktop
audio/x-mpegurl=smplayer.desktop

```

I'd guess that at some point you used System Setting or Settings > Details > Default Applications to set Audacious as default music player. That has the flaw of creating multiple mimeapps.list lines for basically the same mimetype that aren't both overwritten from the context menu.

Your other option would be to delete mimeapps.list & start over just using the context menu > Properties > Open With  to set your default per mimetype.

---

### Post by slickymaster on 2018-12-10
[I]Thread moved to **Multimedia Software**.

[/I]@ra7411:
See [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168) on how to use code tags in your posts

---

### Post by mc4man on 2018-12-10
To add - 
If there are 2 lines in the Default section for the same mime then the 1st parsed is used, ex.

Like this audacious is the default
audio/mp3=audacious.desktop
audio/x-mp3=vlc.desktop

Like this vlc is the default
audio/x-mp3=vlc.desktop
audio/mp3=audacious.desktop

That's why better to just have 1 per mime, whether x- or not doesn't matter (some things are 1st added with x-, some aren't.

---

### Post by ra7411 on 2018-12-16
mc4man,

It looks like your solution worked - thanks.

---

