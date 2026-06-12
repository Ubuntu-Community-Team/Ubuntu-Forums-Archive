---
title: "BBC iPlayer"
date: 2010-04-02
forum: Multimedia Software
---

### Post by Trilby on 2010-04-02
I running Ubuntu 9.10 64 Bit in the UK and cannot get BBC iPlayer to work. The page loads but the video will not play. (Note: do not confuse this with BBC iPlayer Destop which I would rather not install)
Can anyone help?

Thanks

---

### Post by pabc on 2010-04-04
same problem for me. 10.04 64 bit. The page loads but I can't watch the video inthe browser.

---

### Post by pabc on 2010-04-04
I got it working....

I completely removed flash with this link;
[http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72)

then installed it via this link
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

If it works for you set this thread to solved.

P

---

### Post by howefield on 2010-04-04
Can't give you a solution other than say it does work, so worth trying to solve.

I downloaded the 64 bit flash plugin from the Adobe website, and placed the in the following directory.

```
/usr/lib/mozilla/plugins
```

---

### Post by Trilby on 2010-04-05
[pabc]("http://ubuntuforums.org/member.php?u=29635")'s solution worked a treat, although the [.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=146830&d=1265948591") file wouldn't extract (had to drag and drop its contents) which was a bit strange. No matter, though since it worked fine thereafter. I tried [howefield]("http://ubuntuforums.org/member.php?u=186490")'s solution first because it seemed simpler but I couldn't edit the  *//use/lib/mozila/plugins* folder. I will assume there is a way of doing this, although I don't know what it is.
Thanks your help guys :grin:.

Trilby

---

