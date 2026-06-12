---
title: "mythtv user/group id problem"
date: 2007-10-27
forum: Mythbuntu
---

### Post by rhp on 2007-10-27
Hi all,

I just finished installing ubuntu 7.10 on a backend system and subsequently installed the mythbuntu as "add-on".
Also I installed mythbuntu directly onto a combined frontend/secondary backend system.
I am now running into file permission problems when accessing the recordings via nfs, since both systems use different user/group ids for mythtv. I corrected this by hand, but it seems to me that this should be correct by default.

Any thoughts?

Ronald.

---

### Post by superm1 on 2007-10-27
I have run into similar things on my setups.  The thing is that these sorts of items aren't standard across any linux system.  Its not like the group mythtv is gid 116 on any machines.  Even within one given distro it will be different depending on what users and groups were sequentially made.

I'd be interested to hear some ideas to work around this type of problem though.

---

