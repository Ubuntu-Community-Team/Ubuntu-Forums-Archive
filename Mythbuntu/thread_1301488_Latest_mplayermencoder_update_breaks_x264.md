---
title: "Latest mplayer/mencoder update breaks x264"
date: 2009-10-26
forum: Mythbuntu
---

### Post by laffinet on 2009-10-26
Hi all!

I'm running the avenard release repos. The recent (version 2:1.0-svn29794-0ubuntu2)
mplayer/mencoder update seems to break x264 encoding. 
This is the error I got from mythnuv2mkv:

[4259] ERROR mencoder may not support libx264.so.

Just thought I let people know. I downgraded to 2:1.0-svn29770-0ubuntu2 and everything's fine again.

---

### Post by bcg30506 on 2009-10-27
Thanks for the notice.  This will save me time from not upgrading yet.

---

### Post by jyavenard on 2009-10-27
I'll have a look ...

mplayer relies on a newer version of libx264 than what's normally available with ubuntu, so I have to package those as well..

I recently update libx264, I'm surprise it would need another update.

Will see what's going on and fix it shortly

---

### Post by jyavenard on 2009-10-28
Yep, mplayer now requires libx264-78 ...

damn, -77 didn't even last a month

---

### Post by jyavenard on 2009-10-28
new x264 package and mplayer svn #29799 should fix the problem...

---

### Post by laffinet on 2009-10-28
Thanks for looking into this.

---

