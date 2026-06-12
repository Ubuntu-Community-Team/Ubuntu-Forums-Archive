---
title: "Stop totem from starting up automatically"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-05-01
Hi,

Does anyone know how to make it so that when I put a dvd in to play totem doesn't automatically start up.  Also is there a way to change the default player for dvds and pretty much every other tye of video to vlc?

Thanks

---

### Post by tgm4883 on 2007-05-01
system>preferences>removable drives and media

---

### Post by stchman on 2007-05-01
> **djrobthaman said:**
> Hi,

Does anyone know how to make it so that when I put a dvd in to play totem doesn't automatically start up.  Also is there a way to change the default player for dvds and pretty much every other tye of video to vlc?

Thanks

Do what tgm4883 says but do the following before going to the preferences:

sudo apt-get install vlc

VLC is a much better media player than totem.  Once that is up and running do the following in the preferences window:

vlc /media/cdrom0

This will tell Ubuntu to launch the DVD using VLC in cdrom0.

Hope this helps.

---

### Post by ronocdh on 2007-05-01
> **stchman said:**
> Do what tgm4883 says but do the following before going to the preferences:

sudo apt-get install vlc

VLC is a much better media player than totem.  Once that is up and running do the following in the preferences window:

vlc /media/cdrom0

This will tell Ubuntu to launch the DVD using VLC in cdrom0.

Hope this helps.
Dude, I don't mean to be a jerk, but djrobthaman (OP) specifically asked how to set VLC as the default. You didn't even read the second sentence he wrote. [-X :p

---

### Post by stchman on 2007-05-01
> **ronocdh said:**
> Dude, I don't mean to be a jerk, but djrobthaman (OP) specifically asked how to set VLC as the default. You didn't even read the second sentence he wrote. [-X :p

Excuse me, I guess I mis-read it.

I guess you just want to point out my errors instead of contributing.

To make vlc the default for media types: .mp3, .ogg, flac, .wmv, .wma, .mpg, etc. do the following:

When in Nautilus right mouse click on the media file and select properties.  Select Open With and then select VLC.  Next time you double click on that particular media type VLC will be launched.

 I have already answered the default DVD question.

That is it.

I have not been able to get VLC to play an audio CD, but I use Sound Juicer for CD playing.  has anyone been able to get VLC to play audio CDs?

---

### Post by djrobthaman on 2007-05-01
Nice, thanks for the help.

By the way stchman, why don't you try amarok for CDs.  I've never actually used it for CDs myself but it's a great mp3 player/organizer.  And I'm pretty sure it shold play CDs (and probably even rip them) too.

Love vlc for the video but it's no good for music files.  Really need something better made for organization of files into playlists for that.

---

### Post by stchman on 2007-05-01
> **djrobthaman said:**
> Nice, thanks for the help.

By the way stchman, why don't you try amarok for CDs.  I've never actually used it for CDs myself but it's a great mp3 player/organizer.  And I'm pretty sure it shold play CDs (and probably even rip them) too.

Love vlc for the video but it's no good for music files.  Really need something better made for organization of files into playlists for that.

I have never tried amarok.

VLC is an excellent player for music files, it does not have the organizational stuff that other players do.  I will give amarok a try.

I have not found a way for VLC to play audio CDs.

I like the fact that VLC will play other region DVDs without firmware changes.

---

### Post by djrobthaman on 2007-07-06
Whoa... tgm4883 had it right the whole time.

System--->Preferences--->Removable Drives and Media--->Multimedia

Then you can choose what you want it to do.

Somehow I didn't see that post til now.

---

