---
title: "Difference between gstreamer-plugins-xxxx and gstreamer-plugins-xxxx multiverse"
date: 2010-01-17
forum: Multimedia Software
---

### Post by CoreyB. on 2010-01-17
What is the difference between the gstreamer plugins from the universe and the gstreamer plugins from multiverse?

Thanks.

---

### Post by byStanderone on 2010-01-17
...universe/multiverse 
:[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

---

### Post by ubudog on 2010-01-17
The universe plugins are community maintained.  The multiverse plugins are restriced by copyright/legal issues.

---

### Post by CoreyB. on 2010-01-18
So does the gstreamer0.10-plugins-bad multiverse supersede the universe or are they both completely different?

---

### Post by mc4man on 2010-01-18
they are different, the multiverse plugins mainly add encoding support for restricted/non-free codecs.

 Search gstreamer in synaptic and click on one of the multi... plugins -> properties -> dependencies.

You'll get an idea of what it enables, for instance a dep. on libfaac means it provides aac encoding thru libfaac, ect. ect.

---

### Post by 00czar00 on 2011-03-15
Do they create any conflicts? I downloaded both for the bad and ugly sets...

---

