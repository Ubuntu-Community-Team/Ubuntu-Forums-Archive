---
title: "NTSC Player for ubuntu?"
date: 2012-03-30
forum: Multimedia Software
---

### Post by captainnoobing on 2012-03-30
I have some music dvds which are NTSC and i can't get them to play with VLC.

Any ideas of which DVD player will work for me?

These are genuine shop bought dvds by the way.

I have just tried 5 shop bought pal dvds and none of them play on ubuntu?

---

### Post by cyiucsy on 2012-03-30
Perhaps it has something to do with the DVD Region Code?
Although VLC appears to ignore the region code, I am not sure if the firmware of the disc drive will enforce the checking in the hardware level.

---

### Post by captainnoobing on 2012-03-30
> **cyiucsy said:**
> Perhaps it has something to do with the DVD Region Code?
Although VLC appears to ignore the region code, I am not sure if the firmware of the disc drive will enforce the checking in the hardware level.

I jumped the gun a bit saying it was just the NTSC DVDS its all of my DVDS?

I have tried VLC,SM player,GNOME player and XINE and none of these will play any type of DVD?

Do i need to install seperate firm ware for the DVD RW/R player?

---

### Post by captainnoobing on 2012-03-30
Ive solved the problem with the help of google and a fantastic website i found:p

Playback of DVDs is not enabled in ubuntu 11.? you have to download a file.:confused:

problem solved.

---

### Post by cyiucsy on 2012-04-24
> **captainnoobing said:**
> Ive solved the problem with the help of google and a fantastic website i found:p

Playback of DVDs is not enabled in ubuntu 11.? you have to download a file.:confused:

problem solved.

So it's actually the problem of codecs?

---

### Post by na5h on 2012-04-24
> **captainnoobing said:**
> 
Playback of DVDs is not enabled in ubuntu 11.? you have to download a file.:confused:


Yes...Ubuntu only includes completely free software by default. Therefore, you'll have to configure proprietary media formats yourself...but it's pretty easy, once you are aware of this.

Installing the "Ubuntu restricted extras" package from the Software Center tends to take care of most of these things (mp3, avi, Java, Flash, etc.)

Here's a little further reading regarding Ubuntu and restricted formats:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

A little on encrypted DVDs:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

