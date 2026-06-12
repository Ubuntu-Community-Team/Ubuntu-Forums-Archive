---
title: "Low Bitrate Audio conversion"
date: 2009-03-16
forum: Multimedia Software
---

### Post by rosenth on 2009-03-16
[MOVED TO MULTIMEDIA PRODUCTION]

I used to convert my .ogg fils to .wma with this command in ubuntu 8.04:
```
ffmpeg -i file.ogg -acodec wmav2 -ab 18k -ar 21000 -ac 1 file.wma 

``` 

but after installing a fresh ubuntu 8.10 ,**it doesnt accept Bitrate under 24k** (where id done in 18k).
i converted my ogg stories (about 20 minuts,3mb in size) and noticed wma is best for speeches that have music sometimes.

why it doesnt work now?

---

