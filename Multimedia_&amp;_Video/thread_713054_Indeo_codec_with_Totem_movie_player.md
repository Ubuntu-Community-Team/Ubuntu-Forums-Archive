---
title: "Indeo codec with Totem movie player?"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by BertP on 2008-03-02
I couldn't get an avi file using the Indeo 5 codec to play so I installed everything I could find that mentioned "codec"  including all the "avifile" components using synaptic package manager.

Totem still doesn't find the correct codec but MPlayer will play the file.   At this point it's only an annoyance, but does anyone know how to get Totem to use the correct codec as well?

---

### Post by stooshbunutu on 2008-03-02
try installing the complete set of gstreamer plugins from ADD/REMOVE

also try the "lame" codec

Hope this helps :)

---

### Post by BertP on 2008-03-03
Thanks.   I thought I had all the gstreamer playback-related files   but I didn't have gstreamer0.10-pitfdll installed.    Anyone installing this file will also need to download and copy binary codecs  to get this to work;  just read the instructions displayed by Synaptic Package Manager when you install gstreamer0.10-pitfdl.  It will direct you to a readme file which in turn will give instructions about where to download the codecs and  where to copy them on your computer.  After doing this, I can play files encoded with the Indeo 5 codec using Totem  :)

---

### Post by stooshbunutu on 2008-03-03
Your very welcome BertP, gad to hear you got it working

---

### Post by ubuntu-freak on 2008-03-03
Glad you got it working, but people, please don't just install lots of random packages after doing a keyword search like "codecs", as some packages will conflict with or disable others.
 
Nathan

---

### Post by Damanther on 2008-03-07
I'm using 64 bit Ubuntu. I can't seem to find this package. I'm trying to play Indeo 5 avi files as well.

The package mentioned doesn't show up in my Synaptic Package Manager.  Could I be missing a repo?

---

### Post by ubuntu-freak on 2008-03-07
> **Damanther said:**
> I'm using 64 bit Ubuntu. I can't seem to find this package. I'm trying to play Indeo 5 avi files as well.

The package mentioned doesn't show up in my Synaptic Package Manager.  Could I be missing a repo?

 
It's not available to 64-Bit users at present. You should be able to play them in VLC or MPlayer though. Do part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and make sure you have all the codecs you need, like w64codecs for example.
 
Nathan

---

### Post by Damanther on 2008-03-07
Your post is the main one I used setting up my system :)

Everything seems to work like a champ except these types.

VLC plays the audio portion, but no video.

And Mplayer give this error when I open it

xacodec: failed to dlopen /usr/lib/codecs/vid_iv50.xa while /usr/lib/codecs/vid_iv50.xa: cannot open shared object file: No such file or directory.

Sure enough, there is no vid_iv50.xa file in that directory.

---

### Post by ubuntu-freak on 2008-03-07
> **Damanther said:**
> Your post is the main one I used setting up my system :)

Everything seems to work like a champ except these types.

VLC plays the audio portion, but no video.

And Mplayer give this error when I open it

xacodec: failed to dlopen /usr/lib/codecs/vid_iv50.xa while /usr/lib/codecs/vid_iv50.xa: cannot open shared object file: No such file or directory.

Sure enough, there is no vid_iv50.xa file in that directory.

 
That's really strange. If you have w64codecs it should be there. Maybe you could change the backend of Totem to Xine and see if they play in Totem. Install totem-xine and libxine1-ffmpeg.
 
Nathan

---

### Post by Stevil on 2008-05-06
Hi, I've been having the same problem. I downloaded those things but I do not have any codec folder I can find. There is no /usr/local/lib/codecs, /usr/lib/codecs, /usr/local/lib/win32 or /usr/lib/win32 directory. Neither MPlayer, GNOME MPlayer nor Totem can play the video. 
I'm new to Linux so any help would be greatly appreciated. 
Thank you.

---

### Post by Stevil on 2008-05-06
I have the videos working on GNOME MPlayer and MPlayer now after following the directions on this site: [http://www.bgevolution.com/blog/index.php/ubuntu-gutsy-w32codecs-and-w64codecs/]("http://www.bgevolution.com/blog/index.php/ubuntu-gutsy-w32codecs-and-w64codecs/")
Although they still don't work on Totem.

---

### Post by Ferrat on 2008-06-19
Anyone solved this problem with the 64Bit version? =/

On Hardy I can't get them to play in mplayer or totem

---

