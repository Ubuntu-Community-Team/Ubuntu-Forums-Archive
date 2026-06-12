---
title: "I cannot play sound if firefox and amarok are open together..."
date: 2008-04-24
forum: Multimedia Software
---

### Post by jtreach on 2008-04-24
One of them just simply won't play anything involving sound when the other is open, sometimes it's firefox that won't and other times it's amarok. I think this is a sound driver issue but I can't find out how to solve it. As far I know amarok is using xine and i tried changing firefox to oss to try and solve the problem, to no avail....

Any idea?

Thanks in advance.

---

### Post by mister_pink on 2008-04-24
I think this is a known bug. Basically I think it was introduced knowingly to make firefox more stable as there was an issue with flash. It probably wont be undone until there's a new version of flash out. It is really quite annoying though...

---

### Post by jtreach on 2008-04-24
Really.... that, sucks.

I'll just have to wait then.

---

### Post by mister_pink on 2008-04-24
I'm pleased to tell you I was lying. You need to install libflashsupport to fix it. I thought it wasn't fixable because of what I'd read in one of the updates (I've been running hardy since beta)

---

### Post by CFBauer on 2008-04-24
> **mister_pink said:**
> I'm pleased to tell you I was lying. You need to install libflashsupport to fix it. I thought it wasn't fixable because of what I'd read in one of the updates (I've been running hardy since beta)
This fixes it for me.  Cheers!

---

### Post by johnmc on 2008-04-28
Had the same problem but libflashsupport fixed it for me aswell. Thanks!

---

### Post by jtreach on 2008-04-28
Fixes it for me too! Thanks alot for that was getting really annoyed with it....

:D

---

### Post by mister_pink on 2008-04-30
Out of interest, has anyone had stability issues since installing it? Its not actually recommended to install libflashsupport because its meant to make firefox crash when viewing flash content sometimes. However I installed it because the sound thing was too annoying, and I've had no trouble whatsoever, even when trying to make it crash (browsing round youtube loads, clicking back and forwards etc)

---

### Post by jtreach on 2008-04-30
I have definitely had at least one crash (firefox just closed itself with no other effects on anything on my system), but I think compared to having the sound problem it's a small price to pay.

---

### Post by pete-the-meat on 2008-08-08
Brilliant - works for me too - thanks so much!

---

### Post by pete-the-meat on 2008-08-11
Thanks for the result Mr Pink - it worksw brilliantly for me :D

(asweomse scruff art btw :D )

---

### Post by scrapile on 2008-08-27
works for me, and a makes keeping 8.04 a definite.  Thank You!!

---

### Post by jumonge on 2008-09-02
Thanks Mister_Pink, it worked for me as well.

I haven't had firefox crash so far.  If it becomes an issue though, I've found that if I start Amarok first, I can open Firefox without any problems.  Amarok only freezes if Firefox is open first, at least on my computer.

---

### Post by jaydoc on 2008-12-29
To someone who has "been there and done it", please tell me what the best way is to get this issue resolved..? Installing libflashsupport is only making things worse. I get no sound if i am running firefox, and at the same time Firefox just keeps crashing.

Is there no way to fix this issue on Ibex Kubuntu which is what I am running...?

---

### Post by 1awesomeguy on 2009-06-20
```
christopher@emily:~$ sudo apt-get install libflashsupport
[sudo] password for christopher:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libflashsupport has no installation candidate
```

This is on the newest Ubuntu version: Ubuntu 9.04 Jaunty Jackalope - released in April 2009.

---

