---
title: "Adding community repositories."
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by TWFJR on 2006-11-05
I am using 6.10, Kubuntu, attemping to load restricted multimedia apps. Following directions to enable community multiuniverse and universe repositories:  System-Administration- Synaptic Manager-Settings-Repositories and then click add.  I find no add button to click.  I checked the boxes, actually all the boxes are checked.  But no add button.  What does one do to find this add button. Or has it been removed with US distributions?

---

### Post by John.Michael.Kane on 2006-11-05
Your best bet is you config your souces.list this way

Run:
```
kdesu kwrite /etc/apt/sources.list
```

Add the lines or uncomment the lines you need to.

---

### Post by TWFJR on 2006-11-12
Thanks, close this post.

---

