---
title: "Codecs not working properly"
date: 2009-03-21
forum: Multimedia Software
---

### Post by takutosuki on 2009-03-21
Hi there! I'm having some serious trouble with playing some files. It seems like it's mostly avi files, but i get the hunch that it's not just avi. Anyway, it's like I don't have the newest codecs, the video can play properly but sometimes it's lagging, and becoming unsynced with the sound. it's not that my computer is bad, because i can play .mp4 files just fine. or at least some of them. The file i'm trying to play is 1280×720 DivX611 120fps.
I have Ubuntu 8.10.
I already installed ubuntu restricted extras and non-free-codecs.
I tried in VLC, but the same result.
I know the file is properly downloaded - i tried another one with the same encoding, and had the same problem.

anyone have any recommendations? please! don't make me have to go back to windows again! >_<

---

### Post by takutosuki on 2009-04-01
bump....

---

### Post by wolfen69 on 2009-04-01
did you install the gstreamer bad and ugly codecs?

---

### Post by tinosa on 2009-04-02
Howdy,
I am a complete nube and this thread is exatly the help I need.

just installed ubuntu 8.04 Hardy Heron
and am using totem on gnome.

I am unable to play wmv. or avi files.

I need to know where and how to get the codecs I need, as well as
how to install them.

Please clue me in about the bad and ugly  

I want to drop windows and am working on learning enough to make
a permanent switch, gotta long way to go.

Thanks in advance for your willingness to help .

---

### Post by gandaran on 2009-04-02
> **tinosa said:**
> Howdy,
I am a complete nube and this thread is exatly the help I need.

just installed ubuntu 8.04 Hardy Heron
and am using totem on gnome.

I am unable to play wmv. or avi files.

I need to know where and how to get the codecs I need, as well as
how to install them.

Please clue me in about the bad and ugly  

I want to drop windows and am working on learning enough to make
a permanent switch, gotta long way to go.

Thanks in advance for your willingness to help .
open synaptic package manager, find the gstreamer-plugins and install them, the gstreamer codecs are for totem-gstreamer, totem-gstreamer doesn't play every media file type, it's best you have another player installed like mplayer or one of mplayer clones, mplayer uses windows codecs, to get these codecs add the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository then install the w32codecs package.
another very good player is vlc, vlc comes with it's own codecs, you don't have to install any.
then there is the xine package, probably the best for playing dvd's, theres totem-xine, xine-ui and gxine players, the xine players  use libxine1-ffmpeg codecs and the w32codecs too.

---

### Post by tinosa on 2009-04-03
thanks gandaran for the excellent info.
very much appreciated.

---

