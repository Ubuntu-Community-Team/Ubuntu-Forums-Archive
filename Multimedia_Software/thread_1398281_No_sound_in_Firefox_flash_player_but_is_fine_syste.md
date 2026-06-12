---
title: "No sound in Firefox flash player but is fine system wide"
date: 2010-02-04
forum: Multimedia Software
---

### Post by Thierry Lam on 2010-02-04
I have upgraded to 9.10 from 9.04.  My sound is working perfectly for:
- My mp3s through Rhythmbox
- My avi movies
- Downloaded flv files

I can also run all three of the above simultaneously with no problems.

However, whenever I watch a flash movie through Firefox 3.5.7 or Chrome, the movie plays well but without sound.  What should I do to restore sound through flash players in my web browsers?

---

### Post by rashby3 on 2010-02-04
I too get no sound running Flash in FireFox 3.5.7 under Ubuntu 9.10, but can play MP3 files fine in Totem movie player 2.28.2.

Pretty sure this is a new problem since upgrading to 9.10, although I just noticed it recently since I mostly run with sound muted.

I found a lot of posts about Flash audio problems, but the ones I looked at were sometimes unsolved, and sometimes the solutions were irrelevant to my situation (like someone who had a problem because two sound cards were installed).

Is there one best, most general solution?

Thanks.





> **Thierry Lam said:**
> I have upgraded to 9.10 from 9.04.  My sound is working perfectly for:
- My mp3s through Rhythmbox
- My avi movies
- Downloaded flv files

However, whenever I watch a flash movie through Firefox 3.5.7 or Chrome, the movie plays well but without sound.  What should I do to restore sound through flash players in my web browsers?

---

### Post by rashby3 on 2010-02-04
Solved my FireFox Flash audio problem following these instructions:

[http://lovinglinux.megabyet.net/?page_id=220#No-sound-on-YouTube-or-Hulu-videos-2](http://lovinglinux.megabyet.net/?page_id=220#No-sound-on-YouTube-or-Hulu-videos-2)

---

### Post by Thierry Lam on 2010-02-05
I think it might be a permission issue. Just make sure root and your username(using jdoe as example) is associated with the following groups in /etc/group:

```

audio:x:29:jdoe,pulse
pulse:x:121:root,jdoe
pulse-access:x:122:root,jdoe

```

I guess you could also do the following from the Users and Groups GUI but I just can't find it on my OS(another issue to fix). I really can't see how Ubuntu can be mass marketed to the muggles with so many trivial issues. It's an OS for hobbyist with magic fingers.

---

