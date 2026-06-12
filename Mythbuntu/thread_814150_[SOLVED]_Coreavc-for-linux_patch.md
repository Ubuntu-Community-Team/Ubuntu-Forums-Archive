---
title: "[SOLVED] Coreavc-for-linux patch"
date: 2008-05-31
forum: Mythbuntu
---

### Post by mjmos on 2008-05-31
I like how mythbuntu works on my system, i only use the mythtv-frontend to connect to a mythtv-server on a gentoo system ,there's only one problem (for me).
I have some HD h.264 MBAFF channels which don't play very nice.
I know coreavc can play them perfectly.

Is there a way to patch mythtv-frontend with the coreavc-for-linux patch and configure it the exact same way you guy's have done.

---

### Post by superm1 on 2008-06-01
There are a few posts on the forum about how to grab the source and build a nice package from say head, or to include your own patches.

The jist of it is:

apt-get source mythtv
apt-get build-dep mythtv
apt-get install devscripts
apply patch
dch -i, bump changelog entry
debuild

---

### Post by mjmos on 2008-06-02
debuild . . . the missing piece for me, thank you.

---

