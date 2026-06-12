---
title: "Sound Mixing."
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by rck_hitokiri on 2006-08-10
Hey guys. I have recently found out that i cant use sound applications at the same time on my box like e.g. hydrogen & audacity together. does anyone know how i can use two at the same time without any errors? thanks!

---

### Post by BitTorrentBuddha on 2006-08-10
You'd have to buy a new sound card that supports hardware mixing. OSS (found in audacity) doesn't play well with Alsa (found in most applications.) You can try alsa-oss to try and get audacity to mix with software, but it doesn't work for me with audacity. ```
sudo apt-get install alsa-oss
aoss audacity
```

---

### Post by CVDpr on 2007-06-13
buy a new sound card that supports hardware mixing?
 and why i dont have to buy a new card in windows to do this?

---

