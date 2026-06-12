---
title: "Banshee Album Art Issues"
date: 2009-05-14
forum: Multimedia Software
---

### Post by Wa1k3rTXRang3r on 2009-05-14
i rebuilt my ipods database with banshee and now the album art is messed up on my ipod but only on the small previews, once i select the song it is fine.

any help would be greatly appreciated:D

---

### Post by Dan Again on 2009-05-15
Have this same problem...previews of album art on iPod are distorted on the diagonal.  Once song is playing art displays fine.

---

### Post by Wa1k3rTXRang3r on 2009-05-16
yea so i tried to fix it with a re-sync and now it still has the same problem plus the same 2 album covers show up on every album

---

### Post by Dan Again on 2009-11-11
Has anyone figured out a fix for distorted album art in Banshee?

Also, during playback some of my songs display art for the wrong album...any ideas?

---

### Post by Enverex on 2009-11-29
I'm having the same issue in Gentoo with the album artwork being displayed with a diagnal skew in "Albums" view so it's not specific to Ubuntu, I can't find a single fix anywhere though and a Google search only finds this thread with anyone having this issue.

---

### Post by cascade9 on 2009-11-29
First thing I thought was "thats an issue with the ID3 tags". So I did a little search, and found this- 

> Now, along the way, whenever I found an incorrect album cover embedded and tried to fix it by removing the previous album art and adding the new one, I started seeing the corrupted images in amarok that I’d been reading about. And it’s not just that amarok wasn’t able to read the images… they were truly corrupt. “eyeD3 –write-images=. $FILE” produced a corrupt image as well. And, every time I cleared the previous image and added a new one with eyeD3, I noticed that my filesize kept getting bigger and bigger. Even when I “removed” all images with eyeD3’s “–add-image=:FRONT_COVER”, the filesize of the mp3 just kept getting bigger. It was then that I tried setting the APIC frame to null (”") with id3v2, and that returned my mp3’s filesize back to where it should be. And after that, if I added the album art to the mp3, it added it cleanly, my filesize looked sane again, and Amarok was able to see the embedded album art again.


 So, my theory, [which is mine, and belongs to me and I own it, and what it is too]("http://www.jumpstation.ca/recroom/comedy/python/elk.html"), is that people who are seeing album art distortions/corruptions in amarok might possibly have files that either have more than one embedded picture, or have dirty APIC tags. If any of you, dear readers, is seeing embedded album art distortion in Amarok, would you please install id3v2 and eyeD3 onto your little Linux box and try running my mp3albumcover function against that mp3 with a new album image? I’d very much like to see if it fixes the problem for you.


[http://movingparts.net/2007/12/09/embedded-album-covers-your-psp-amarok-and-you/](http://movingparts.net/2007/12/09/embedded-album-covers-your-psp-amarok-and-you/)

Yeah, I know hes talking about amarok, not banshee, and I'm not saying its the ID3 tags for sure, but heck, its worth a try.

---

