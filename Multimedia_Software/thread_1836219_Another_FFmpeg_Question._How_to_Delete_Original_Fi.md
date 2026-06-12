---
title: "Another FFmpeg Question. How to Delete Original File?"
date: 2011-08-30
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-08-30
Title pretty much says it all. How do I delete the original file after a successful conversion? I've googled and looked through several guides but haven't found the answer. I'm writing a Python script to combine various things and part of it entails conversion with FFmpeg. That's why I've been asking questions about it. If there is no way to remove it with FFmpeg, I'll do it another way. I just figured it be easier to do it as part of the conversion.

---

### Post by dniMretsaM on 2011-08-31
Bump.

---

### Post by dniMretsaM on 2011-09-01
So, um, yeah. I'm having fun waiting around.

---

### Post by andrew.46 on 2011-09-01
I am not sure about the exact nature of your conversion but if you are using the same container you could simply use the *-y* option and overwrite your original file? Obviously the output filename would need to be the same as the input...

---

### Post by dniMretsaM on 2011-09-01
No, its a different file type and most likely a different name. Good thought though.

---

### Post by shantiq on 2011-09-02
in this case do this (works with all supported ffmpeg formats)


```
ffmpeg -i file.flac   file.mp3   [COLOR="Red"]&& rm file.flac[/COLOR]
```


if you want to do it for a BATCH

```
for f in *.flac; do ffmpeg -i "$f"  "${f%.flac}.mp3"; done   && rm *.flac
```


**MAKE** really sure you do not want the original kept as this **really** deletes file not in the bin really gone ::)))

---

### Post by fdrake on 2011-09-02
```
for f in *.flac; do ffmpeg -i "$f"  "${f%.flac}.mp3"; rm $f; done  
```

eehh i am borrowing your code if you don't mind.... :P

---

### Post by shantiq on 2011-09-02
GO FOR IT    NOT mine   code is code

do not forget if you want this particular one use -ab too to fix your bitrate on the mp3


example

```

for f in *.flac; do ffmpeg -i "$f"   **[COLOR="Red"]-ab 320k [/COLOR]** "${f%.flac}.mp3"; done  && rm *.flac

```


otherwise you end up with a shi**y 64k    which is the default    but you probably know that ::))

---

### Post by dniMretsaM on 2011-09-02
Ok, I knew you could do that, I just didn't know if there was a way to do it within the FFmpeg command. I guess not. Thanks to all and thread solved!

---

