---
title: "lubuntu ipod woes"
date: 2012-06-26
forum: Multimedia Software
---

### Post by ronwell on 2012-06-26
i just switched to lubuntu because the newer versions of ubuntu were making my laptop overheat. so far, I really like it. the issue that's making things difficult, though, is that I can't get my ipod to sync with anything.

the crux of it seems to be that if I install gtkpod, then banshee, rhythmbox, and the gtkpod manager all crash the instant i connect my ipod.  if I uninstall it, they don't crash, but won't sync either, because apparently without the gtkpod libraries the ipod will only mount as read-only.

any ideas?  i'm thinking it could possibly help to just straight up reformat my ipod, because it's been synced to so many different programs on so many different operating systems that the file system is probably a little wonky. i don't know how to do that on linux, though, and am scared of bricking it.

---

### Post by TenPlus1 on 2012-06-26
Pop into Terminal and type:

   sudo apt-get install ifuse

This should allow Lubuntu to detect iPhones and iPods without having to jailbreak them...

---

### Post by ronwell on 2012-07-25
sorry for a super delayed response! my entire laptop was out of commission for a while (hardware issues).

Anyway, I'm still having these issues.  Lubuntu only recognizes my iPod as a read-only external device, so I can't use it as an external hard drive. Also, Banshee and Rythmbox both crash when I connect it, so I can't add any music.  Ifuse didn't seem to do anything.  I never had these issues with regular Ubuntu.  Are there any packages missing from Lubuntu that I should install?  I've already got gtkpod.

---

