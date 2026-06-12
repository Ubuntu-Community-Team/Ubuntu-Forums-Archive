---
title: "mp3 length not detected"
date: 2009-02-08
forum: Multimedia Software
---

### Post by yuppienet on 2009-02-08
Hello all,

I am a new user to ubuntu. Just recently I moved from archlinux because it seems that ubuntu is the right distro to get _everything_ to work ok and/or out-of-the-box.

However, I am having some trouble with my mp3 files. They worked just fine in other distros, but with ubuntu 8.10, my music player (rhythmbox) doesn't recognize their length. Nautilus doesn't either. This is starting to bug me a lot because rhythmbox will not submit my played files because it thinks they have a length < 30 secs.

I have been looking for this in the forums and google, but none of the post have helped me. I have tried "fixing" the files with vbrfix and mp3val but it doesn't quite solve it.

Any ideas on this?

Cheers

---

### Post by RedRat on 2009-02-08
> **yuppienet said:**
> Hello all,

I am a new user to ubuntu. Just recently I moved from archlinux because it seems that ubuntu is the right distro to get _everything_ to work ok and/or out-of-the-box.

However, I am having some trouble with my mp3 files. They worked just fine in other distros, but with ubuntu 8.10, my music player (rhythmbox) doesn't recognize their length. Nautilus doesn't either. This is starting to bug me a lot because rhythmbox will not submit my played files because it thinks they have a length < 30 secs.

I have been looking for this in the forums and google, but none of the post have helped me. I have tried "fixing" the files with vbrfix and mp3val but it doesn't quite solve it.

Any ideas on this?

Cheers

Well I am running 8.04LTS and both Nautilus (2.22.5.1) and Thunar (Thunar 0.9.0) both yield the length of all my MP3s. When I import a folder into Rhythymbox it clearly shows the length of each song. 

In Nautilus, when you right click on an mp3 track, and go to "Properties" then go the the Audio tab, it should show you the length of the file in minutes and seconds. Can you play each song in, say and application like, Audacious or Amorok? What happens if you just double click on a track? Does it play completely through, i.e., greater than 30sec.

---

### Post by yuppienet on 2009-02-08
Hi RedRat,

Well, to answer to your follow up, nautilus displays the mp3 file duration as 0:00 (I checked the file properties for this).

I have not tried other players since my problem is now solved.

I was watching some videos on the internet I came across a video that I could not watch because some codecs were missing. It then directed me to install gstreamer0.10-plugins-ugly. I did install it and I could finally see all mp3 file duration with nautilus. After that I erased my rhythmbox configuration and rebuilt my music collection.

Everything is working fine now :D

---

