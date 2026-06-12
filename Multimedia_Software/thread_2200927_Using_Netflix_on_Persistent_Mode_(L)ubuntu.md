---
title: "Using Netflix on Persistent Mode (L)ubuntu"
date: 2014-01-21
forum: Multimedia Software
---

### Post by lisatobari on 2014-01-21
Hello-

I am a beginner on lubuntu.

My first goal now is to get Netflix running on Firefox. I have completed all the steps including Wine, Pipelight, user agent switcher... when I try to play a video, Netflix loads up to 30-50% on the bar then gives me Error 8156-6205. I tried using Chrome and a user agent switcher and the same error happens.

I opted to try the Netflix Desktop utility but it fails to open because user_xattr is not active.

I have tried the route of editing /etc/fstab, but when I open it up, all it has is two lines:

overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

So I have nothing to edit in terms of users.

I get the impression that this is because I'm using LiveUSB persistent mode?

The USB was NOT formatted as FAT32.

Please help me figure out what I need to do differently!!

Many anticipated thanks...

---

