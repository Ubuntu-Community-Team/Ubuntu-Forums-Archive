---
title: "vlc + subtitle = problem"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by dragobr on 2007-04-22
Its just me or is there a problem with subtitles on VLC / feisty?

I can get then shown, but not all of them.. it shows only some of them, at random times... :(

---

### Post by ShadowZ on 2007-05-21
happens here aswell... i have searched this and other forums but no answer yet... :S

---

### Post by Blackcape on 2007-05-27
I had the same problem too.

To solve the problem you have to change the subtitle encoding mode. Go to Settings, Preferences, Input / Codecs, Other codecs, Subtitles and then change the Subtitle text encoding field. ISO-8859-1 worked for me. (Here you find the different ISO standards: [http://alis.isoc.org/codage/iso8859/jeuxiso.en.htm](http://alis.isoc.org/codage/iso8859/jeuxiso.en.htm)). Then save and restart the player.

---

### Post by alexef on 2007-05-28
Brilliant solution! Same problem for me, Ubuntu Feisty+VLC+East European ISO-8859-2 .srt file.

Tried ISO-8859-2, but didn't work, so I set ISO-8859-1 and also unchecked 'UTF-8 Auto Detection'.

Thanks dragobr

---

