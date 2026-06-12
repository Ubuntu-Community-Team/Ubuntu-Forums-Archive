---
title: "VLC installation issues"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by thomkirwan on 2007-12-23
Hi, I recently moved to Ubuntu (Gutsy) and I want to install VLC player. I've added all the dependencies apart from ttf-dejavu. When I try to install this I get the following:

```
dpkg: regarding .../tmp/ttf-dejavu_2.7-2_all-1.deb containing ttf-dejavu:
  ttf-dejavu-core conflicts with ttf-dejavu (<< 2,19-lubuntul)
    ttf-dejavu (version 2.7-2) is to be installed.
dpkg: error processing /tmp/ttf-dejavu_2.7-2_all-1.deb (--install):
  conflicting packages - not installing ttf-dejavu
```

I thought of removing ttf-dejavu-core via synaptic and replacing it with ttf-dejavu but to remove ...-core I also have to remove ubuntu-desktop, which I don't particularly want to do. Is there anybody who can help me?

---

### Post by mc4man on 2007-12-23
What is synaptic showing as installed - you could see 2 or 3 listings -  ttf-dejavu,  ...core, ..extra
all should be same ver.  Mine are all 2.19-......

---

### Post by thomkirwan on 2007-12-23
...core 2.19-lubuntu3
...extra 2.22-1

Would it help to remove that version of extra and install 2.19?

---

### Post by mc4man on 2007-12-23
_I_ would highlight the extra and then click package and see if you can force ver. back to 2.19.., if not then remove, and install 2.19 from synaptic along with ttf-dejavu ( from synaptic )
I wouldn't use an external .deb for this (if that.s what you did )
all the ver. need to be the same  (i think)
note: this is what I'd do from a logical standpoint not tech

---

### Post by thomkirwan on 2007-12-23
I rolled back extra to 2.19-1ubuntu3 and managed to find ttf-dejavu_2.19-1ubuntu3_all.deb which installed fine and now I have VLC working too. Thanks! I'll bear this fix in mind in the future too :)

---

