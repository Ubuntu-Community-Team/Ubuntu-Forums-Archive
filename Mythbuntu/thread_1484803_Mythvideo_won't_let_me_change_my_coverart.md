---
title: "Mythvideo won't let me change my coverart"
date: 2010-05-16
forum: Mythbuntu
---

### Post by JamesNorris on 2010-05-16
I'm not sure if this is Jamu related or not, I disabled the cron job after it kept renaming my files, but the problem still persists...

The default coverart downloaded for some of my films is in another language, I have manually deleted the file and replaced it with an English language version. When I go back into myth, it still shows the deleted coverart... I'm using the /var/lib/mythtv/coverart storage group, is there somewhere else the coverart is stored that I need to replace, too?

Anyone any other ideas how I can fix this?

---

### Post by brian_hammerhead on 2010-05-16
I ran into this as well.  It turns out that you simply need to delete the cache after replacing the cover art.

   rm -rf ~/.mythtv/themecache/*

Give it a try.  It worked for me.

---

### Post by JamesNorris on 2010-05-17
> **brian_hammerhead said:**
> 
   rm -rf ~/.mythtv/themecache/*

Give it a try.  It worked for me.

Yep, that did the trick, thanks!

---

