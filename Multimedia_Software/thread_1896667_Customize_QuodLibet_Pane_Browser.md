---
title: "Customize QuodLibet Pane Browser"
date: 2011-12-17
forum: Multimedia Software
---

### Post by infotron on 2011-12-17
Pity QL doesn't have support forum :(

I thought some one here might know some tricks and this is my question:

QL Pane Browser displays by default "genre/artist/album" where artist includes all possible artists which just makes this pane bloated with unwanted information if user has compilations and so on, like it usually is

I want to make it to list "album artist" (TPE2 MP3 frame or in QL vocabulary - performer) and if this field is not set then list regular artist field (TPE1). So I want to say to QL "performer OR artist" but everything I try fails in delivering wanted result.

According their documentation - [http://code.google.com/p/quodlibet/wiki/BrowsersGuide#Paned_Browser](http://code.google.com/p/quodlibet/wiki/BrowsersGuide#Paned_Browser)
> Besides normal tags, each pane also supports tied tags, tag patterns, and a per entry display pattern. so it should be possible perhaps.

Let me rephrase my question: How to set pane in QL Pane Browser that displays one tag field if present OR other field if previous is not present.

I guess this is basic, but I can't find my way in QL-fu
I run Quod Libet 2.2.1 if that matters

---

### Post by lazka on 2011-12-17
<performer|<performer>|<artist>>

<if this tag isn't empty|print everything here|else print this>

..you might want to update to 2.3, which supports multiple tag values for patterns like this.

[https://launchpad.net/~lazka/+archive/ppa](https://launchpad.net/~lazka/+archive/ppa)

[http://www.student.tugraz.at/christoph.reiter/ql-changelog/quodlibet-2.3/changelog.html](http://www.student.tugraz.at/christoph.reiter/ql-changelog/quodlibet-2.3/changelog.html)

---

### Post by infotron on 2011-12-17
Thanks **lazka**

I just couldn't get better answer ^_^

---

