---
title: "converting mp3 to wma"
date: 2008-09-23
forum: Multimedia Software
---

### Post by sonaural on 2008-09-23
i know you would never want to do this, but i have to.  my lg dare only plays wma.

what's a good user friendly linux mp3-wma converter.  i have the standard 'sound converter' program but they don't even offer conversion to wma.

---

### Post by jerome1232 on 2008-09-23
Well disclaimer converting lossy to lossy format can cause anywhere from slight to horrible quality loss depending on the song so keep your original mp3's do not delete them after conversion.

[http://www.media-convert.com/](http://www.media-convert.com/) can convert anything but you have upload the files then download them.

Other than that I think you would have to boot into windows to do this. I can't seem to find a native linux solution with just a quick google search.

---

### Post by sonaural on 2008-09-23
thanks for the tip.  like i said, no one would ever do this and so no converter i've found supports it.  i most certainly will preserve the originals, crossing my fingers that since most my song files are of very high quality (generally 320 but no less than 256) it'll be ok.

clearly verizon cut a deal with windows to only support wma, why else would they shun mp3s, the platform standard for the last ten years.  guess there's no escaping those bastards...

---

### Post by mc4man on 2008-09-23
You can convert *to* wma with ffmpeg
( commands assume .mp3 or .wav is in home folder
 .mp3 to wma
```
ffmpeg -i foo.mp3 -acodec wmav2 -ab [COLOR="Red"]128[/COLOR]k  foo.wma
```
.wav to wma
```
ffmpeg -i test.wav -acodec wmav2 -ab [COLOR="Red"]192[/COLOR]k  test.wma
```
you may alter what's in red to some extent, change foo to match input name , output name desired

(doesn't work with all versions of ffmpeg

---

### Post by seeker5528 on 2008-09-23
Is [this](http://lgdare.net/features) what you have?

Because according to that page it doess mp3 and aac, I don't see anything about wma.

Later, Seeker

---

### Post by thefirstone on 2008-09-30
This was solved in this tread: [http://ubuntuforums.org/showthread.php?t=823941](http://ubuntuforums.org/showthread.php?t=823941)
Look at the last post , (the first post also works).

---

### Post by mc4man on 2008-09-30
you can use this to do a batch convert of a folder, very easy, no typing except for command if you use r. click -> open in terminal

Can be adapted for other conversions.

[http://ubuntuforums.org/showthread.php?t=932627](http://ubuntuforums.org/showthread.php?t=932627)

---

