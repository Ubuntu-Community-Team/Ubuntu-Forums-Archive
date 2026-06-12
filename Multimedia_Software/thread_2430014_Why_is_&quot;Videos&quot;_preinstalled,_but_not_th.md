---
title: "Why is &quot;Videos&quot; preinstalled, but not the needed codecs?"
date: 2019-10-26
forum: Multimedia Software
---

### Post by theuserbl on 2019-10-26
If I start the preinstalled program "Videos", the videos can't start, because of missing Video-codecs.

This helps to install the codecs:
[https://websiteforstudents.com/how-to-install-video-audio-codecs-on-ubuntu-18-10-18-04-16-04-lts/]("https://websiteforstudents.com/how-to-install-video-audio-codecs-on-ubuntu-18-10-18-04-16-04-lts/")
After that all works fine.

But if the codecs don't exists in a fresh installed Ubuntu, why is then an application preinstalled, which need it?

Or is it possible to write the needed codec download commands in an shell-script, which is then placed on the desktop, so that it can be easily done.

Greetings
theuserbl

---

### Post by Frogs Hair on 2019-10-26
There are legal issues connected with playing or especially recording protected content depending on your location so certain codec packages are not installed by default.

---

### Post by uRock on 2019-10-26
Selecting this box during install has prevented me from having those issues for years.

---

### Post by Yellow Pasque on 2019-10-26
> **theuserbl said:**
> But if the codecs don't exists in a fresh installed Ubuntu, why is then an application preinstalled, which need it?

The application only needs the codecs to play certain formats. It's not like it's completely useless without the extra codecs.

---

### Post by hk42 on 2019-10-31
My main critic is why this application is called "videos" ?
After installing timidity I discovered it plays midi files.
The same goes for "file manager" there are lots of them 
sometimes they even share the same icon.

---

### Post by TheFu on 2019-10-31
I tend to no use the default applications 95% of the time.  For videos, I simply add the VLC PPA and install that. Never any issues again.  If VLC can't play a video, then I don't actually want that video.  

There's a faster tool, mpv, that deals with videos well, but it uses a CLI interface, which I prefer.  It also handles audio files cleanly without hassle   **mpv *3** will play all the mp3 files in the current directory, for example. Simple, fast, effective.  To play all the ogg files from /music down, recursively, use 
```
mpv `find /music -type f -iname \*ogg`
```
fast, simple, effective.

---

### Post by uRock on 2019-10-31
Yup, VLC is on my install list. as least until Canonical blocks us from installing anything other than Snaps. VLC is already listed as a Snap in Software, but the deb is still working for now.

---

### Post by TheFu on 2019-10-31
> **uRock said:**
> Yup, VLC is on my install list. as least until Canonical blocks us from installing anything other than Snaps. VLC is already listed as a Snap in Software, but the deb is still working for now.

PPA, my friend.  PPA.

---

### Post by andrew.46 on 2019-11-01
> **TheFu said:**
> There's a faster tool, mpv, that deals with videos well, but it uses a CLI interface, which I prefer.

Another vote here for mpv which has taken off where the venerable MPlayer foundered. Extra bonus is a nice integration with SMPlayer so a gui is also possible...

---

### Post by SeijiSensei on 2019-11-01
mpv + SMPlayer has been my preferred video system since mpv replaced mplayer.

---

### Post by mc4man on 2019-11-02
> **TheFu said:**
> I tend to no use the default applications 95% of the time.  For videos, I simply add the VLC PPA and install that. Never any issues again.  If VLC can't play a video, then I don't actually want that video.  
.I'd say the vlc ppa's are either dead (stable) or useless (master
They've mainly moved to snaps, the 4.0-dev snap is a curious thing, atm pretty much unusable from what i've seen..

---

### Post by TheFu on 2019-11-02
For those people like me, still rockin' 16.04, [https://itsfoss.com/install-latest-vlc/](https://itsfoss.com/install-latest-vlc/) has a PPA. It installs: 
vlc/xenial,now 3.0.7.1-3~16.04.york0 amd64 [installed]

Last update was August.

---

