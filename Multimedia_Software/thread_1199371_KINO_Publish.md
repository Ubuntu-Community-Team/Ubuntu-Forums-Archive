---
title: "KINO Publish?"
date: 2009-06-28
forum: Multimedia Software
---

### Post by ZombiesNTea on 2009-06-28
What happens if I click "Publish SMIL" for a video file on Kino?  I don't have a blip.tv account.

---

### Post by ZombiesNTea on 2009-06-28
Does it publish it to my computer or something?

---

### Post by ZombiesNTea on 2009-06-28
Did I post this in the wrong forum section?

---

### Post by ZombiesNTea on 2009-06-28
And if it did publish somewhere, without an account, is there a way to delete it?  Or if its waiting for me to make an account, is there a way for me to delete it?

---

### Post by t4thfavor on 2009-06-29
publish/project.sh - defines File/Publish SMIL behaviour


Theres a better explanation of this here.
[https://bugs.launchpad.net/ubuntu/+source/kino/+bug/52169](https://bugs.launchpad.net/ubuntu/+source/kino/+bug/52169)


I bet you could decipher its contents, and find out where those naughty vids went that yu didn't mean to publish:)

---

### Post by ZombiesNTea on 2009-06-29
> **t4thfavor said:**
> publish/project.sh - defines File/Publish SMIL behaviour


Theres a better explanation of this here.
[https://bugs.launchpad.net/ubuntu/+source/kino/+bug/52169](https://bugs.launchpad.net/ubuntu/+source/kino/+bug/52169)


I bet you could decipher its contents, and find out where those naughty vids went that yu didn't mean to publish:)

Thanks!

I'm computer illiterate... I'm lost as to what that page tells me.

---

### Post by ZombiesNTea on 2009-06-29
I screwed around with it again, and then when I clicked the publish thing, the terminal came up asking my username and password for that video site.  I'm taking that it didn't upload anywhere then?

---

### Post by ZombiesNTea on 2009-06-29
> **ZombiesNTea said:**
> I screwed around with it again, and then when I clicked the publish thing, the terminal came up asking my username and password for that video site.  I'm taking that it didn't upload anywhere then?

?

---

### Post by bootdoc on 2010-08-22
publish smil is a to publish your video to blip.tv without having to export it to a specific format.  you need an account at blip to do this.  It helps to save space on your HD since you are publishing directly from the captured format (usually .avi).  Blip then transcodes your vid to flv and other formats you choose.  You must have mjpegtools installed for this option to work. To install just open your package manger and search for mjpegtools and mark for installation or run the following in terminal:
for debian systems
sudo apt-get install mjpegtools

don't know the command for rpm and yum based distros.

---

