---
title: "Can I use Ubuntu-based audio player to save my place in an audio book?"
date: 2020-01-23
forum: Multimedia Software
---

### Post by AbleTassie on 2020-01-23
I have been using Rhythmbox in Lubuntu to manage (add, delete, sync, etc,) the MP3 content in my older Apple iPod classic, model A1136 (circa 2005).  Rhythmbox has worked well enough, but one major frustration is that I cannot switch between audiobooks without losing my place in the audio book I am currently listening to. So, when I go back to that earlier audiobook I have to search for my place, which takes a lot of time. 

QUESTION: Is there any way to have an Apple iPod put a bookmark in place in an audiobook using Rhythmbox or another similar Ubuntu based audio player program, just as I can do with an actual physical paper book?

There appears to be a way to do this in iTunes, it involves checking a box in iTunes that says "remember playback position." See [https://discussions.apple.com/thread/846016](https://discussions.apple.com/thread/846016)

But there is no iTunes (I know of) that works in Linux. But perhaps there is an audio player that works in Linux/Ubuntu that can remember a reading place in an audio book.

This [post ]("https://superuser.com/questions/249565/music-player-for-linux-which-remembers-the-playback-position")from about 9 years ago, says that there is no Linux-based music player that can remember the place in an audio book. But that was a post from 9 years ago.

Thanks,

A.

---

### Post by TheFu on 2020-01-25
I haven't tried it, but google found this: [https://www.omgubuntu.co.uk/2017/10/cozy-audiobook-player-ubuntu-linux](https://www.omgubuntu.co.uk/2017/10/cozy-audiobook-player-ubuntu-linux) and  many other results.  The article says it won't work with DRM'd content or Apple file types. I only have mp3 and ogg files, so that won't be an issue here.  Cozy does keep track of playback location within 10 seconds automatically.
Another review: [https://itsfoss.com/cozy-audiobook-player/](https://itsfoss.com/cozy-audiobook-player/) - seems the project team added a sleep timer, speed control, library searching.
No PPA and not part of the repos, but there is a flatpak. I've not had good luck with flatpaks or snaps. Snap restrictions are too tight and previous flatpaks refused to run.  Trying again with cozi.  It wants 400+MB for a 1.1MB program.  I hate wasting space.
Success!  Importing books now. I'm not a fan of the interface.

I use a tablet to listen to audiobooks at home and my phone when travelling.  Astro Audio Player has bookmarks for Android platforms.

---

### Post by TheFu on 2020-01-26
So, I did install cozy (that's the correct spelling).  Played around with it for a little bit. Then moved on.

This morning my backup summary report had this:```

=== Time for Backups to posc === 
StartTime 1580015225.00 (Sun Jan 26 00:07:05 2020)
EndTime 1580023884.12 (Sun Jan 26 02:31:24 2020)
ElapsedTime 8659.12 (2 hours 24 minutes 19.12 seconds)
TotalDestinationSizeChange 3925838588 (**3.66 GB**)
```
3.66GB of backup changes?!!!  What?

I installed 2 flatpaks yesterday.  Cozy and VidCutter. Did those tools really need 3.6GB of storage?
```
~/.local/share/flatpak$ du -sh .
1.7G    .
```
No, but the flatpaks did use 1.7G!  Why?
```
$ flatpak list
Name                    Application ID             Version Branch Installation
Cozy                    com.github.geigi.cozy      0.6.12  stable user
VidCutter               com.ozmartians.VidCutter   6.0.0.6 stable user
default                 â¦sktop.Platform.GL.default         19.08  user
Intel                   â¦ktop.Platform.VAAPI.Intel         19.08  user
GNOME Application Platâ¦ org.gnome.Platform                 3.34   user
KDE Application Platfoâ¦ org.kde.Platform                   5.13   user

```
It installed both a new KDE and a new Gnome platform!?  Huh?
```
$ flatpak info org.kde.Platform

KDE Application Platform - Shared libraries used by KDE applications

          ID: org.kde.Platform
         Ref: runtime/org.kde.Platform/x86_64/5.13
        Arch: x86_64
      Branch: 5.13
     License: GPL-2.0+
      Origin: flathub
  Collection: org.flathub.Stable
Installation: user
   **Installed: 918.0 MB**

      Commit: 12f0bb3c2d986ecc95d6cd1e6b47e9bd4cf23a5aac69068c776b25cbb0741963
      Parent: d936484f7ddf87806d66f7e633238c0d6c85bf9806b4cfec1f01cd3b2b5a5966
     Subject: build of org.kde.Sdk, Sun Dec 15 19:30:04 UTC 2019 (3a8ee35ec2010530fb3509f7fd6b21caa57a51f1)
        Date: 2019-12-16 03:21:06 +0000
```
918MB ... just under 1GB for the KDE platform?  
```
$ flatpak info org.gnome.Platform

GNOME Application Platform version 3.34 - Shared libraries used by GNOME
applications

          ID: org.gnome.Platform
         Ref: runtime/org.gnome.Platform/x86_64/3.34
        Arch: x86_64
      Branch: 3.34
     License: GPL-2.0+
      Origin: flathub
  Collection: org.flathub.Stable
Installation: user
   **Installed: 912.3 MB**

      Commit: 12697f53c77f47b0a133001779d6520696825211c907123c3076b2b1bc2d4e75
      Parent: fbfe040ec34a07bf49e5d25db84b51ecb7e6e25402b4e54f864ccd5f5cede3ae
     Subject: Export org.gnome.Platform
        Date: 2020-01-24 14:25:27 +0000
```
And Gnome is just as bad.
I am not impressed.  Both programs are wiped from my systems now, but flatpak decided to leave the dependencies. 
```
flatpak uninstall --all
sudo apt purge flatpak
rm -rf ~/.local/share/flatpak

```
All better.

---

### Post by AbleTassie on 2020-01-27
Thanks for the suggestion and for looking into this for me, Fu.

Able

---

