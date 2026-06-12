---
title: "Firefox YouTube No Upload Widget"
date: 2009-06-07
forum: Multimedia Software
---

### Post by kihjin on 2009-06-07
So I went to upload a video onto YouTube... 

[http://www.youtube.com/my_videos_upload](http://www.youtube.com/my_videos_upload)

and, there's no upload widget! I thought for sure one of my add-ons (no-script, adblock, you pick) was preventing it from appearing. Safe-mode? Still no upload widget. I did a quick search and found a couple others having the same trouble as I was:

[http://www.google.com/support/forum/p/youtube/thread?tid=315546dfb82c7320&hl=en](http://www.google.com/support/forum/p/youtube/thread?tid=315546dfb82c7320&hl=en)

They are using ubuntu! So I wondered if maybe Youtube was doing maintenance and upload just wasn't available. I've got two laptops: one for work, one personal. Personal has ubuntu installed. Work has Windows installed. Guess what? Ubuntu laptop (version 8.04) does not have the upload form. The Windows XP laptop shows it just fine!

What I notice now is a blue bar on the page that displays "Loading..." which after a few moments disappears.

[edit]

Actually it turns out that even though the Upload button appears in Firefox in Windows, it does... absolutely nothing!

So I tested this out in Internet explorer. Form appears just fine and I can select a file...

[correction]

Firefox in safe-mode on my windows xp laptop is able to upload just fine.

---

### Post by ECas123 on 2009-06-07
Use the Bulk Upload uploader. It requires installing Google Gears but it works.

---

### Post by kihjin on 2009-06-07
Thanks for the response.

Gears only works under a 32bit system. "Unfortunately" I am running 64bit.

---

### Post by kihjin on 2009-06-07
Further research... note that I am running FireFox in safe-mode

It looks like this error is the culprit:

```
Error: [Exception... "Index or size is negative or greater than the allowed amount"  code: "1" nsresult: "0x80530001 (NS_ERROR_DOM_INDEX_SIZE_ERR)"  location: "http://s.ytimg.com/yt/jsbin/www-upload-vfl101026.js Line: 38"]
Source File: http://s.ytimg.com/yt/jsbin/www-upload-vfl101026.js
Line: 38
```

---

### Post by kihjin on 2009-06-07
Seems there are many like me...

[http://www.google.com/support/forum/p/youtube/thread?tid=09280ae7ff9c2d9e&hl=en&fid=09280ae7ff9c2d9e00046bc692f569d9](http://www.google.com/support/forum/p/youtube/thread?tid=09280ae7ff9c2d9e&hl=en&fid=09280ae7ff9c2d9e00046bc692f569d9)

---

