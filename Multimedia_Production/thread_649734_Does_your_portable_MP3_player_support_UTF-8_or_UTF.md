---
title: "Does your portable MP3 player support UTF-8 or UTF-16 characters in ID3 Tags?"
date: 2007-12-25
forum: Multimedia Production
---

### Post by clubsoda on 2007-12-25
Linux MP3 applications like **vlc** seem to be happy regardless of which ID3 version or character encoding used in the tag, however I've just discovered that a recent model portable MP3 player (MPIO MG200) doesn't handle UTF encoding at all, even though it claims to support ID3v2.3 and ID3v2.4.  Anything in UTF comes out looking like chinese.

In english, both ISO-8859-1 and Windows-1252 work so I'm not sure which is actually implemented in the player.

For japanese, EasyTag offers three different encodings but only Shift-JIS renders properly on the player.  [ISO-2022-JP shows mojibake and EUC-JP shows one question mark per character "????"].

UTF-8 would be nice if it worked but evidently we're not there yet.  Should EasyTag default to the more widely compatible code pages and pop up a warning if you select the others?

---

### Post by Rizado on 2007-12-25
NO! My W910i does not seem to handle utf-8 correctly, the names just get cut off after a few letters and the songs are in no order at all.

And easytag doesn't seem to convert the tags except you actually change what it says. Like changing a letter or removing a comment.

So how do you convert 40gbs of music into something it can read?

EDIT: I actually managed to do it :) ```
eyeD3 --set-encoding=latin1 --force-update [dir...]
```

---

### Post by ariel on 2008-07-11
> **Rizado said:**
> NO! My W910i does not seem to handle utf-8 correctly, the names just get cut off after a few letters and the songs are in no order at all.

And easytag doesn't seem to convert the tags except you actually change what it says. Like changing a letter or removing a comment.

So how do you convert 40gbs of music into something it can read?

EDIT: I actually managed to do it :) ```
eyeD3 --set-encoding=latin1 --force-update [dir...]
```


Exactly what I was needing... Thanks!!

UPDATE: eyeD3 worked but the order in which the album tracks are played was *not* fixed by the re-encoding... more on this here:

[http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=8650&jump=true#M8650](http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=8650&jump=true#M8650)

---

