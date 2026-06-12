---
title: "Add tags v1 and v2 to an MP3 file"
date: 2012-09-10
forum: Multimedia Software
---

### Post by alfirdaous on 2012-09-10
Hello everybody,

Once adding tags to an MP3 file, how can we add these tags to both id3v1 and id3v2 on the same time **USING COMMAND LINE**, otherwise, how can we copy id3v2 tags into id3v1 tags.

Thanks in advance

---

### Post by Cheesemill on 2012-09-10
I use Puddletag.

---

### Post by alfirdaous on 2012-09-10
Thanks foe your response, I mean a command line

---

### Post by FakeOutdoorsman on 2012-09-11
Try **id3**. An example from *man id3* may give you what you're looking for:

```
id3 -2 -1u fs_song.mp3
    Copy ID3v2 tag to ID3v1 tag in selected file.
```

---

### Post by alfirdaous on 2012-09-11
well, thanks, this is the output:

```

$ sudo id3 -2 -1u 071C.mp3
id3: invalid option -- '2'

```

---

### Post by FakeOutdoorsman on 2012-09-11
Works for me, but it appears your id3 is a different program than my [id3](http://freecode.com/projects/id3) (I'm not using Ubuntu).

Also, why are you using sudo?

---

### Post by alfirdaous on 2012-09-11
> **FakeOutdoorsman said:**
> Works for me, but it appears your id3 is a different program than my [id3]("http://freecode.com/projects/id3") (I'm not using Ubuntu).

Also, why are you using sudo?

I am using Ubuntu

sudo is used, because I am not on the same username, only test username

---

