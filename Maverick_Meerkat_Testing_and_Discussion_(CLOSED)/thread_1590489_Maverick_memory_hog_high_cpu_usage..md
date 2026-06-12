---
title: "Maverick memory hog high cpu usage."
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-10-07
Hi,

I have been observing high cpu usage in maverick. Chromium has been running multiple instances. My cpu fan on most of the time. A couple of other software like uTorrent server have been hogging CPU.



Uploaded with [ImageShack.us](http://imageshack.us)



Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by cariboo on 2010-10-08
From your screenshots the only thing that sticks out is that system monitor is using 92% of your cpu cycles. I would suggest you try:

```
free -m
```

and 

```
top
```

as system monitor add it's own overhead. See the screenshots for what the two commands result in on my system.

---

### Post by donniezazen on 2010-10-08
Man flash kills my system.



Uploaded with [ImageShack.us](http://imageshack.us)



Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by sendblink23 on 2010-10-08
> Chromium has been running multiple instances

That is how Chromium works, so ignore it - you can surf that question on google (same applies for Google Chrome).

---

### Post by ktp on 2010-10-08
> **soham_1207 said:**
> Man flash kills my system.



Uploaded with [ImageShack.us](http://imageshack.us)



Uploaded with [ImageShack.us](http://imageshack.us)

what flash plugin are you using?  I am also seeing ~30-50% CPU for flash playback.  It can get upto 100% CPU also depending on flash video.  It is the same in firefox also.  you can also check the "Task Manager" (shift+Escape) in chromium, which will show how much cpu each process is using.

---

