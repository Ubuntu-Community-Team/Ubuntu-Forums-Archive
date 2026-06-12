---
title: "MTP Issue - Unable to write"
date: 2009-12-07
forum: Multimedia Software
---

### Post by thealmightyone on 2009-12-07
I currently use a jaunty remix - eeebuntu.

I have a Samsung YP-U3, and it mounts fine, and I can read files from it. The problem is when trying to write to the device. Either the file transfer gets stuck at 64K, or it completes and the device doesn't detect the file (ie, turn it on and it's not in music list).

I have installed countless libraries (libmtp8, mtp-tools) and software (amarok, qlix), and I am still unable to fix my write issue.

---

### Post by lavinog on 2009-12-07
It could be the device.
My creative zen can be a pain to write to sometimes...usually when I have problems like this I can do a cleanup on the device and everything will work fine.
I don't know about your device, but the cleanup option is part of a system recovery menu on the device.  It repairs the internal database.

---

### Post by thealmightyone on 2009-12-07
> **lavinog said:**
> It could be the device.
My creative zen can be a pain to write to sometimes...usually when I have problems like this I can do a cleanup on the device and everything will work fine.
I don't know about your device, but the cleanup option is part of a system recovery menu on the device.  It repairs the internal database.

I can write to the device fine under Windows, should have said that.

---

### Post by thealmightyone on 2009-12-09
Bump.

---

### Post by lavinog on 2009-12-09
I should mention that mtp support has improved on karmic, you could give it a try.

---

### Post by thealmightyone on 2009-12-11
> **lavinog said:**
> I should mention that mtp support has improved on karmic, you could give it a try.

Gave Karmic a try, same issue.

Just noticed, if I write an mp3 to the player, then try to copy it to my laptop, I get the error:

> 
Error getting file: -6: Not Supported


Does seem like the issue is definitely with Ubuntu writing to the device.

---

### Post by lavinog on 2009-12-11
Try using the mtp-tools package.

First unmount your device, but don't disconnect it.
open a terminal.
do
```

mtp-detect

```
it should spit out a bunch of information about your device.
It might help to post that.

then try sending a file
```

mtp-sendfile somesong.mp3 somesong.mp3

```
note the second filename is the destination name on the device.

Post any errors you may get.

---

### Post by thealmightyone on 2009-12-11
Thanks, sending the file via mtp-sendfile worked.

Rhythmbox also detects it, which is great. Just had to unmount it.

---

### Post by thealmightyone on 2009-12-11
EDIT: Ignore. Error messages are useless.

---

### Post by thealmightyone on 2009-12-11
How do I send a track to a subdirectory within the device? I have a Music\Artist\Album structure, and no matter what I try, mtp-sendfile drops the file in Music.

---

### Post by lavinog on 2009-12-12
> **thealmightyone said:**
> How do I send a track to a subdirectory within the device? I have a Music\Artist\Album structure, and no matter what I try, mtp-sendfile drops the file in Music.

mtp devices don't have a folder structure.
It organizes everything by the mp3id tag.
One problem I have found is that there are different versions of the mp3id and different devices use different versions.

---

