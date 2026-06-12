---
title: "[SOLVED] Toggen .ogv to avi"
date: 2008-12-19
forum: Multimedia Software
---

### Post by ClarkePeters on 2008-12-19
I use Thoggen to rip my dvds for backup (with .ogv extension). It's great in that I can rip a whole two hour dvd down to just over 300mb file size and it still plays great on the computer (although for files I might burn back to a Dvd I save them around 695mb).

Now I need to burn them and I'm having a time of it because the files convert back at too large a size.  I tried using mencoder converting from ogv to avi, but the avi is 840mb so by the time I get it in iso form, it's over five or six gigs.

```
mencoder -o out.avi -noidx -oac copy -ovc copy SpongeBob.avi
```

I need it to be around 650 -700mb as I have always had success at this size going from avi to iso (Using ffmpeg, dvdauthor, then mkisofs). Is there something I can add to the above code to reduce the resulting output, say reduce the bitrate or something?

The other option I used was using VLC to convert the .ogv to .mpg (mpeg-ps) and then using ffmpeg to get it dvd ready, then dvdauthor, then mkisofs, but that iso was too large too.  I also used avidmux to try converting the avi and also the mpg (each individually converted from the ogv) but again too large. 

Any advice would be appreciated.

---

### Post by ClarkePeters on 2008-12-19
I didn't realize we have a Multimedia production forum. 
I'm marking this post as solved and reposting in the other forum (since I don't know how to move a post to a different forum.)

cheers

---

