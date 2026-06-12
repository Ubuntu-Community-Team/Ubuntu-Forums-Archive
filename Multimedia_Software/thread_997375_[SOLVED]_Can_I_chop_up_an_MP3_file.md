---
title: "[SOLVED] Can I chop up an MP3 file?"
date: 2008-11-29
forum: Multimedia Software
---

### Post by Sealbhach on 2008-11-29
I have some MP3s that go on for over an hour and I would like to be able to split them up into smaller 20 minute segments. Is there some way I can do that?


.

---

### Post by night_fox on 2008-11-29
With audacity, yes with great ease! Get it from Add/Remove Programs.

---

### Post by FakeOutdoorsman on 2008-11-29
Try **mp3splt**.  It's in the Ubuntu universe repository and will split mp3 files without needing to re-encode.  This preserves the quiality of the file.  Another option is the package **poc-streamer** which contains the program mp3cut.  I'm not sure if mp3cut re-encodes.

---

### Post by binbash on 2008-11-29
easy way : 

[http://www.getdeb.net/app/Mp3splt](http://www.getdeb.net/app/Mp3splt)

---

### Post by cszikszoy on 2008-11-29
> **FakeOutdoorsman said:**
> Try **mp3splt**.  It's in the Ubuntu universe repository and will split mp3 files without needing to re-encode.  This preserves the quiality of the file.  Another option is the package **poc-streamer** which contains the program mp3cut.  I'm not sure if mp3cut re-encodes.

I'll second or third this.  Mp3splt is great.

Also, just a FYI: 
you can use cat to do the opposite of what you want.  If you ever need to combine mp3s try this:

```

cat file1.mp3 file2.mp3 > file3.mp3

```
****

---

### Post by Sealbhach on 2008-11-29
Wow!! That's brilliant. I used mp3splt. So simple!


.

---

