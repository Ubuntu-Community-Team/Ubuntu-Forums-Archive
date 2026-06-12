---
title: "Cant install lame"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by mxan on 2007-04-22
this is what I get

 sudo apt-get install lame
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate

Any Ideas? I upgraded to Feisty Fawn thinking it would help but it did not.

---

### Post by yabbadabbadont on 2007-04-22
Make sure that you have the universe and multiverse repositories enabled.

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by mxan on 2007-04-22
Yes that worked! Thanks!

---

