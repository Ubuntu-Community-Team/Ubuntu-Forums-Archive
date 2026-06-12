---
title: "medibuntu packages key?"
date: 2008-04-24
forum: Multimedia Software
---

### Post by scradock on 2008-04-24
I am trying to add the medibuntu repo to my sources, but don't know how to get the public key. Can anyone tell me? And why isn't his done seamlessly when I add the repo?

---

### Post by overdrank on 2008-04-24
> **scradock said:**
> I am trying to add the medibuntu repo to my sources, but don't know how to get the public key. Can anyone tell me? And why isn't his done seamlessly when I add the repo?

HI and if gives you the key command on the page
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add - && sudo apt-get update

```
Page
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by scradock on 2008-04-24
Thanks - that was what I needed.

It doesn't seem to be working very well at the moment, probably because of the release, but at least I now have the key added.

I'm still curious why this isn't done automatically when the repo is added to the software sources, or at least an instruction message telling me where to get the key.

Are we afraid someone will sneak off with our packages??????

---

### Post by overdrank on 2008-04-24
> **scradock said:**
> Thanks - that was what I needed.

It doesn't seem to be working very well at the moment, probably because of the release, but at least I now have the key added.

I'm still curious why this isn't done automatically when the repo is added to the software sources, or at least an instruction message telling me where to get the key.

Are we afraid someone will sneak off with our packages??????

Hi and as explained on the link I posted
Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).

---

