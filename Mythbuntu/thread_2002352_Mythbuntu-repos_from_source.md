---
title: "Mythbuntu-repos from source?"
date: 2012-06-12
forum: Mythbuntu
---

### Post by melvin.udall on 2012-06-12
Hi all,

I am a happy user of Mythbuntu for a couple of years now and I also use the Mythbuntu-repos to stay up to date on two of my frontends.
On my third backend I need Jack audio support compiled in so what I did up to now was:

apt-get source mythtv
apt-get build-dep mythtv
cd mythtv-*
<edit debian/rules (e.g. add line to enable jack audio)>
debuild -i -us -uc -b

While this works fine it only pulls the sources from the usual Ubuntu (multiverse) repository. What is the proper way for doing the same thing from the Mythbuntu-repos?

---

### Post by tgm4883 on 2012-06-12
[http://mythbuntu.org/wiki/developer-cheatsheet#Building](http://mythbuntu.org/wiki/developer-cheatsheet#Building)

---

