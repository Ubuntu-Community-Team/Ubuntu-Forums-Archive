---
title: "using &quot;$f&quot; for bash script to encode? - help?"
date: 2012-04-16
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-16
I'm trying to fit the "$f" param into a mencoder bash script that encodes movies based on a simple Nautilus right click.

example - I have a copy of the movie "Holiday Inn" and I right click to run the script - 

so I'd have 

```
alex@uboontu:~/Videos$ mencoder originalmovienamehere.xxx -ovc xvid -xvidencopts bitrate=xxx:pass=2 -oac copy -o outputmoviehere.avi
```

I would like to also be able to set it for other extensions as well.

---

