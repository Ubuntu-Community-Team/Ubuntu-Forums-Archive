---
title: "wget failed to download image from URL"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by Mavericklsd on 2011-01-20
I tried to download some images from google using wget:

where wget cbk0.google.com/cbk?output=tile&panoid=2dAJGQJisD1hxp_U0xlokA&zoom=5&x=0&y=0

However, I get the following erros:

--2011-01-21 04:39:05--  [http://cbk0.google.com/cbk?output=tile](http://cbk0.google.com/cbk?output=tile)
Resolving cbk0.google.com... 209.85.143.100, 209.85.143.101
Connecting to cbk0.google.com|209.85.143.100|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-01-21 04:39:05 ERROR 404: Not Found.

I'm very sure the image is there by paste the URL on my browser and the image pop up correctly. 

I need to download a sequence of tiles on google panorama for my project, but each panorama view containing up to 338 pictures. I simply can not do by hand...

---

### Post by andrewc6l on 2011-01-21
Try:
```

wget "cbk0.google.com/cbk?output=tile&panoid=2dAJGQJisD1hxp_U0xlokA&zoom=5&x=0&y=0"

```

(Note the quotation marks.) The shell is interpreting the first & as "put this process in the background".

---

### Post by andrewc6l on 2011-01-21
Try:
```

wget "cbk0.google.com/cbk?output=tile&panoid=2dAJGQJisD1hxp_U0xlokA&zoom=5&x=0&y=0"

```

(Note the quotation marks.) The shell is interpreting the first & as "put this process in the background".

(oops - multipost)

---

### Post by Mavericklsd on 2011-01-23
It solved thank you very much!

---

