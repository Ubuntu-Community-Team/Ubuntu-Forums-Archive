---
title: "Network camera"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by tomcio on 2006-09-05
Hi!

I have succesfully installed my camera in Ubuntu 6.06. It works with Ekiga fine, but I have no idea how can I save "movie" recorded with it on my dusk? I have no expirinece with it, can someone helpe? :]

---

### Post by reclusivemonkey on 2006-09-05
> **tomcio said:**
> Hi!

I have succesfully installed my camera in Ubuntu 6.06. It works with Ekiga fine, but I have no idea how can I save "movie" recorded with it on my dusk? I have no expirinece with it, can someone helpe? :]

The streamer program is a simple CLI program you can use to record from a V4L device. Its in the repos, just 

```

sudo apt-get install streamer

```

then

```

man streamer

```

and you should be good to go!

---

