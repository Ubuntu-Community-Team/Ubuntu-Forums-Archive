---
title: "AVI plays in Ubuntu but not in Windows XP"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by Habibi on 2008-03-31
Hi,

I have a couple of AVI files that play fine in Ubuntu using VLC but when I try to play them in Windows with any video player, including VLC, they will not play back.

Any ideas on what the problem may be?

---

### Post by linux phreak on 2008-03-31
Try putting extension ".avi"  to the file and try again.

---

### Post by Habibi on 2008-03-31
> **linux phreak said:**
> Try putting extension ".avi"  to the file and try again.

Just tried that and I still get the following error:

"Windows Media Player cannot play the file. The Player might not support the file type or might not support the codec that was used to compress the file."

Using GSpot Codec Information on the file shows that it is a not a valid AVI file

---

### Post by aeiah on 2008-03-31
it could be a codec issue. try downloading the cccp codec pack for windows

---

### Post by aeiah on 2008-03-31
nevermind. didnt see that gspot doesnt register it. well. where did you get this avi file from? chances are its a different file format (ubuntu doesnt rely on file extentions to determine what kind of video it is y'see)

---

### Post by Habibi on 2008-03-31
> **aeiah said:**
> nevermind. didnt see that gspot doesnt register it. well. where did you get this avi file from? chances are its a different file format (ubuntu doesnt rely on file extentions to determine what kind of video it is y'see)

I got it from a torrent site

Let me ask a more general question - if I download a video using my Ubuntu computer and then copy that video file and try to play it on Windows will it always not work? or should it? Just wondering.

I am new to Ubuntu so sorry for the ignorance.

---

### Post by aeiah on 2008-03-31
it should always work, providing a: it was copied correctly and b: you have the required codecs on your windows machine.

have you installed this windows codec pack? it should have everything you need:
[http://www.cccp-project.net/](http://www.cccp-project.net/)

---

### Post by Mohonri on 2008-03-31
> **Habibi said:**
> I got it from a torrent siteIf you picked it up off a torrent, then there's a good chance it's an .iso.  I don't remember if VLC will work with ISOs, but generally you need to mount an iso (Daemon Tools is what I use under windows) so it appears to be a disk in a CD or DVD drive.  Once you've done that, it should play just like a regular DVD.

---

