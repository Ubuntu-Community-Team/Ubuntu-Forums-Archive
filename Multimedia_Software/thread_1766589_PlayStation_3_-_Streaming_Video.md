---
title: "PlayStation 3 - Streaming Video"
date: 2011-05-24
forum: Multimedia Software
---

### Post by motermouth15 on 2011-05-24
Hey Guys-

So i've recently re-setup my linux server. After converting to a windows one, i slowly missed it more and more. Anyways my goal here is to set up something that will act as a media server for my playstation 3. I've tried PMS-linux and I believe I have it installed but I just can't get it to work and the 3tutorials that seem to be out there were of no help.

I guess i dont have my heart set on that program and at this point am looking for ANY program that will allow me to do this, but one that would have a detailed tutorial. The other thing i wanted to mention as well is I'm currently running a Ubuntu Server 10.04 (headless).

Any help that i can get from you guys would be great!!

Thanks-
Nate

---

### Post by coffeecat on 2011-05-24
Two thoughts for you and I stress these are thoughts only. I have little expertise in this area.

The first is, have a look at Mediatomb. Useful link:

[https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb)

I tried setting it up in Ubuntu about a year ago and my PS3 saw my media files when Ubuntu was running, and I was able to stream them. I didn't pursue it any further because my computer is usually switched off when I want to use my PS3 for watching videos or whatever.

The other thing I found by accident. I have a WD MyBookWorld NAS device on which I have set up my own smb share with password. But it also comes with a passwordless "Public" sbm share with "Shared Music", "Shared Videos" and "Shared Pictures" folders already created. When I put music, videos and jpegs in the respective folders, my PS3 picked them up automatically and I was able to stream them. My suggestion: create a "Public" passwordless smb share on your Ubuntu server and see if you can do the same. You will probably have to create the three folders named as I have quoted.

---

### Post by backu on 2011-05-24
I'm running PMS-Linux, it's not that hard really, just a matter of having all the proper stuff installed for transcoding Video files that are not natively supported on the PS3, other than that, it generally works OOB

---

### Post by motermouth15 on 2011-05-26
I understand that its not extremely hard, however, my PS3 wont even detect the pms-linux. I've also spent about a week looking into this and can't figure it out :/

Any ideas?

---

