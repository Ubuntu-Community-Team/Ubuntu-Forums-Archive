---
title: "[SOLVED] VLC + XGL, Compiz-Fusion (+Emerald) --&amp;gt; Fullscreen movies are transparent"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by redhat24 on 2007-08-01
Everything is fine in VLC when it's windowed.
But when i would like to watch the movie in fullscreen, the movie turns transparent (just a lil bit, but it's annoying). If i change to normal - windowed - mode, the movie becomes good, no transparency.

I was looking for an option like "Trasparency", but i didn't find it.

Is somebody who had the same problem, and solved?
Or just suggestion, what should i check?

---

### Post by shavenlunatic on 2007-08-01
not used fusion that much, or XGL, but have you checked all your transparency settings in compiz?

---

### Post by redhat24 on 2007-08-01
Yep, I Think.
I turned off everything (in Control Panel), and still transparent. I'll try without Emerald, because if i'm moving a window, that window turns transparent, maybe fullscreen is connected to it.

---

### Post by tschneiter on 2007-08-04
See this thread: [http://ubuntuforums.org/showthread.php?t=514127&highlight=compiz+fusion+vlc+fullscreen](http://ubuntuforums.org/showthread.php?t=514127&highlight=compiz+fusion+vlc+fullscreen)

---

### Post by redhat24 on 2007-08-04
Thx! It helped me

---

### Post by transatlant1c on 2007-08-05
I'm currently using Compiz Fusion as well.. And I was wondering if I could use emerald as my 'window decorator' as well? I've installed it with Beryl before.. But I don't know if it will work with Compiz Fusion.. Any help?

---

### Post by redhat24 on 2007-08-05
Use this command to start compiz-fusion (ALT+F2, and then type it):
```
compiz --replace -c emerald &
```

---

### Post by nibbles on 2007-08-05
Hi,

for me the name=vlc and state=fullscreen didn't work, I had to remove the DropdownMenu opacity. Isn't there any real solution?

Thanks.

---

### Post by redhat24 on 2007-08-06
Atm, i'm not using Compiz-fusion, because it makes my ubuntu instable and slower

> **Lapino said:**
> Something I noticed with the latest compiz versions from Trevino's repository was that the state=fullscreen didn't work anymore for me. The solution, oddly enough, was to use emerald instead of metacity as window manager. So maybe some of you might try that out too.

But maybe this post helps, and for further helps, I think you should post to the other thread: [http://ubuntuforums.org/showthread.php?t=514127&highlight=compiz+fusion+vlc+fullscreen](http://ubuntuforums.org/showthread.php?t=514127&highlight=compiz+fusion+vlc+fullscreen)

---

