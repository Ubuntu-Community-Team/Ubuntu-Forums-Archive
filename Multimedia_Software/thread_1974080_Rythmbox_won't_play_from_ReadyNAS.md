---
title: "Rythmbox won't play from ReadyNAS"
date: 2012-05-05
forum: Multimedia Software
---

### Post by anyusername on 2012-05-05
Hi,

When trying to play any music tracks from my ReadyNAS Duo, using Rhythmbox on Ubuntu 12.04, there is no audio output. The track name shows in libnotify and the play progress bar moves in Rhythmbox, as if it is playing - but no audio. If I move the same track to the local drive, then it plays fine. Also, the track will play from the ReadyNAS using Banshee.

Anyone have any idea what the issue with Rhythmbox is?

---

### Post by lowprofileabc on 2012-05-24
I am having the same issue. All i know is it has something to do with "SMB shares" not being ACTUALLY mounted, but some sort of "fake" mount (sorry, i am not an expert, and I don't see anyone chiming in here).  Supposedly, even though the file explorer says the drive is mounted, it is not ACTUALLY mounted, and there is some arcane command a person could type to make this drive TRULY mounted so that songs can play.  Can someone please help?

---

### Post by anyusername on 2012-05-24
My NAS is mounted under QVFS (hidden .qvfs folder in &HOME). None of the other music players from the Ubuntu repositories that I have tried, including Banshee, Clementine and Audacious have any problems with playing from the NAS drive. In addition, Movie Player(Totem) and VLC can access the files ok too.

I have submitted a bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=675526]("https://bugzilla.gnome.org/show_bug.cgi?id=675526")

---

### Post by volido on 2012-06-01
I have exactly the same problem...the curious thing is that when Im connected to the LAN by wire  the songs have sound but when I'm connected  wireless not ...not idea

---

### Post by cdt1975 on 2012-08-21
I have a similar problem with NAS. I have two Netgear Storas. The older one operates correctly, the newer one will not let me write to it and I cannot log in most of the time. I am getting a message saying the drive is not mounted. The other stora is obviously mounted and regognised ok. Both network settings are the same. Both have static IP addresses. I also get asked for the windows workgroup password.

---

