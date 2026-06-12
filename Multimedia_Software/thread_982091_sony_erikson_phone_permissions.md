---
title: "sony erikson phone permissions"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Jessimo on 2008-11-14
Hi, can anyone tell me how to change the name of my sony erikson 800i phone "PHONE CARD".  In the terminal, I can't change dir there because of the space between phone and card.  

What I really want to do is change the permissions on the card, transfer songs off and/or on, or just wipe the card to reload with new songs.

Since I installed ubuntu Hardy, I have not the permissions.  I was the author before with another linux distro, but now this is the problem.

Thanks...

---

### Post by Zob321 on 2008-11-23
you should either quote the whole path, or escape the spaces using backslash:

```

% cd "/media/PHONE CARD"

```

or

```

% cd /media/PHONE\ CARD

```


Hope that helps!

---

