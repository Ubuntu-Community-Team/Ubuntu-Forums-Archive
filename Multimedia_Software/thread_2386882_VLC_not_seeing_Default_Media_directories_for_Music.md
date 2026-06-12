---
title: "VLC not seeing Default Media directories for Music, Videos and pictures"
date: 2018-03-11
forum: Multimedia Software
---

### Post by mdgeist on 2018-03-11
I just installed VLC on Ubuntu Studio 17.10 64bit and it doesn't see anything in the My Music, My Videos and My Pictures folders.
I searched through the Setting to see if I could set it manually, but found nothing.

Am I missing something blatant or is this a bug of some sort.

---

### Post by monkeybrain20122 on 2018-03-12
How did you install vlc?

---

### Post by mdgeist on 2018-03-12
I installed it through the "Software" Program.
I also, just tried it on my Desktop as well, using the same method, and it doesn't see the Songs in my Music folder either.

---

### Post by monkeybrain20122 on 2018-03-12
Did you install ubuntu-restricted-extras?

---

### Post by mdgeist on 2018-03-12
Nope, I am not aware of what those are.

---

### Post by monkeybrain20122 on 2018-03-12
Those are codecs and such. If your songs are in formats like mp3 you need to install ubuntu-restricted-extras first before media players can play them. Now I don't know about "detecting them", maybe vlc doesn't recognize the formats without restricted extras. Anyway try install that first.

---

### Post by deadflowr on 2018-03-12
Since *My Folder-name-here* is a Windows naming scheme, you seem to be trying to access the folders on a Windows Drive.
Perhaps this is a similar issue:
[https://ubuntuforums.org/showthread.php?t=2350316]("https://ubuntuforums.org/showthread.php?t=2350316")

---

### Post by mdgeist on 2018-03-12
> **deadflowr said:**
> Since *My Folder-name-here* is a Windows naming scheme, you seem to be trying to access the folders on a Windows Drive.
Perhaps this is a similar issue:
[https://ubuntuforums.org/showthread.php?t=2350316](https://ubuntuforums.org/showthread.php?t=2350316)

The "My Music" & "My..." etc. designation is in VLC not the Hard Drive or OS.

---

### Post by mdgeist on 2018-03-12
> **monkeybrain20122 said:**
> Those are codecs and such. If your songs are in formats like mp3 you need to install ubuntu-restricted-extras first before media players can play them. Now I don't know about "detecting them", maybe vlc doesn't recognize the formats without restricted extras. Anyway try install that first.

This might explain individual songs not showing up, but not even folders under the "Music" folder in File Manager are showing up in VLC.

---

### Post by mc4man on 2018-03-12
It's possible you installed the snap vlc package. In that case the Playlist items you mentioned are useless. 
You can however use Media Library to add folders and or files.

Otherwise you'd need to remove the snap version & install the .deb version

---

### Post by mdgeist on 2018-03-13
> **mc4man said:**
> It's possible you installed the snap vlc package. In that case the Playlist items you mentioned are useless. 
You can however use Media Library to add folders and or files.

Otherwise you'd need to remove the snap version & install the .deb version

Yes, the version in the app "Software" is a Snap version, quite annoying.
I installed via the CLI and it version 2.2.6, but at least I can see my media folders now.

Thank you.

---

### Post by ank2 on 2018-03-17
> **mdgeist said:**
> I just installed VLC on Ubuntu Studio 17.10 64bit and it doesn't see anything in the My Music, My Videos and My Pictures folders.
I searched through the Setting to see if I could set it manually, but found nothing.

Am I missing something blatant or is this a bug of some sort.

Here (Debian) when I use the File/Open from the pulldown menu VLC and navigate to a directory and play a file from there will next time remember that I used that directory.

---

