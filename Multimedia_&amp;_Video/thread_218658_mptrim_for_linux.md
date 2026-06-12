---
title: "mptrim for linux?"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by lonelypauly on 2006-07-18
Back when I used windows, I used this wonderful little app called mptrim to trim the fat from streamrips.  All I know about audio editing in Linux is well... Audacity.  While this is a great program, i would much prefer a simpler app to trim my mp3 files.  any suggestions?

---

### Post by pdxsam on 2006-07-23
I'm looking for the same.

While Audacity rules, if you want to drop 20 seconds off a 1 hour mp3, you've got to wait for Audacity to re-encode the entire mp3. 

Something that can literally chop the mp3 would be excellent.

---

### Post by andrewk8 on 2008-05-09
I'm also looking for the same thing. MPTrim for Windows is great.  It can automatically delete silence at beginning / end of file and increase / decrease / normalize volume.  You can drag & drop multiple files / folders to run in "batch" mode.  The sheer beauty of MPTrim is that the changes are lossless.  It doesn't re-encode the file, so the sound isn't degraded with multiple edits.

This would be very easy for someone who knows the details of MP3 files to implement.  The MPTrim Windows .exe is only a couple of hundred KB.

---

### Post by olejorgen on 2008-05-09
```

apt-get install quelcom
# or
apt-get install mpgtx

```
PS: I don't think it is as easy as you think though (implementation)

---

### Post by olejorgen on 2008-05-09
BTW: It seems like mpTrim works in wine

---

### Post by kahlil88 on 2008-07-06
mpTrim gives me errors when opening certain MP3s:
> acmStreamOpen failed
Try (re)installing the Fraunhofer IIS MPEG Layer-3 Audio Decoder ACM Component
Is there a GNU/Linux equivalent that supports formats *besides* MP3?

---

