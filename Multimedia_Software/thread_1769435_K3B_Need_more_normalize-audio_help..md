---
title: "K3B Need more normalize-audio help."
date: 2011-05-28
forum: Multimedia Software
---

### Post by Lawrence Talbot on 2011-05-28
I read the posts on the Internet and the posts on this forum and I tried all the answers given and I still can't get normalize-audio in K3B to work.  I do use MP3GAIN but I would to use K3B again.  I had it working at one time and then after an upgrade of which I don't remember it no longer works.  I have no problem with anything else in K3B.  I hope someone has got it working.  Thanks for any help you can be.  :(

---

### Post by Swagman on 2011-05-28
You must've read one of my comments on this then ?

I still haven't got normalise working in K3B but to be fair I gave up with it and dragged my burn list into Brasero.

Shame as K3B is awesome.

---

### Post by mc4man on 2011-05-28
Don't use/know k3b but if it's issue is it can't find it then create a symlink for  normalize-audio named normalize (assumes /usr/local/bin exists
```


sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
```

---

### Post by Lawrence Talbot on 2011-05-28
> **mc4man said:**
> Don't use/know k3b but if it's issue is it can't find it then create a symlink for  normalize-audio named normalize (assumes /usr/local/bin exists
```


sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
```

I tried this and it didn't work. I will stick with Brasero or Nero.  Thanks for all your help.

---

### Post by mc4man on 2011-05-28
Went ahead and installed k3b - 
the problem isn't that it's looking for "normalize" - the issue is it's looking for a version.
So normalize-audio (which is actually called normalize, debian decided to rename to normalize-audio several years ago because debian is smart in this way) is returning a version of

> :~$ normalize-audio --version
normalize 0.7.7

K3b is expecting the version to be normalize-audio 0.7.7 - like this - (rebuilt source
> :~$ normalize-audio --version
normalize-audio 0.7.7
or as per script (comment 32 in link
> $ normalize-audio --version
Empty line
normalize-audio 0.7.7


So the best way to address (other than k3b and or debian getting their acts together) would be to rebuild the normalize source so it returned an expected -V. 

Otherwise you could try using a script - look in this bug report, maybe down around comments 30 or so - keep reading  - the whole thing is pure nonsense. 
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/45026](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/45026)

(the ln I posted before was for RubyRipper which oddly expects "normalize" to be called "normalize"

Screen shows k3b finding normalize once it returns expected -V, screen 1 w/ script, screen 2 w/ rebuilt source - I'd rebuild source, takes only a few min., is cleaner - will attach a dpatch if desired, then even easier

---

