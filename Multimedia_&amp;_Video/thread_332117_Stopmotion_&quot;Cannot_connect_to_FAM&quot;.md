---
title: "Stopmotion &quot;Cannot connect to FAM&quot;"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by muhkayoh on 2007-01-05
Hello,

I had used the package Stopmotion successfully under Dapper, but since upgrading to Edgy it won't run.  Running from the terminal I get:

```
Warning: Cannot connect to FAM
Segmentation fault (core dumped)
```

I've added my voice to a bug report on the matter [here]("https://launchpad.net/ubuntu/+source/stopmotion/+bug/72479"), but it looks like this one may not get confirmed, much less acted on, any time soon.  (I believe Stopmotion is maintaned by a single person, so that's certainly understandable.)

Anyway, I had been using Stopmotion as a decent "pencil test" program for my 2D animations.  I draw frames in Inkscape/GIMP, export png sequences, and stitch them together in Cinelerra for final output with sound, etc.  Cinelerra is overkill for the pencil testing stage, so I'd really like to get Stopmotion working again for that.  Anybody have any ideas?

As an aside, I do know about dedicated animation programs like Synfig and Ktoon, but neither of those is ready for production at the moment.  After much research and testing, I think the Inkscape/GIMP => Cinelerra route is the one that'll work best for me for now.  So I'm mostly interested in hearing about either 1)how to get Stopmotion working again under Edgy or 2)an alternative approach to simple pencil testing.

Thanks,

Matt

---

### Post by muhkayoh on 2007-01-05
Bump.  :D

---

### Post by muhkayoh on 2007-01-06
Good news/bad bews-

I contacted the developer of Stopmotion and learned that he had just updated the package to account for the bug.  That's the good news.

The bad news - for now - is that it isn't yet in the Edgy repositories.  The further bad news is that when I try to install the .deb package it says I have an unsatisfiable dependency with respect to libqt4-core.  But I have that installed, so I'm stuck for the moment.

Any suggestions would be appreciated.

Matt

---

### Post by Weevil on 2008-06-02
Well sort of a bug like mentioned here so I figured I'd just post it and my workaround here for the interested...

Using Feisty and the Stopmotion from repository I found that when adding more than say 16 images at a time made the program crash with a 'segmentation fault', sometimes accompanied by the 'Cannot connect to FAM' error.
 Looking at the developers site - [http://stopmotion.bjoernen.com/](http://stopmotion.bjoernen.com/) - there was a message that there's a source tar new version available so mailing them probably just gets me an 'upgrade to the new version' reply... which is probably what I should have done but anyway I didn't.

The bug occurs when Stopmotion copys & renames the 1015 jpg (or other number/format) files to tmp_0.jpg to tmp_1014.jpg and writes them in /home/user/.stopmotion/tmp.
Rename your files from tmp_0.jpg to tmp_1014.jpg, open stopmotion & copy the files to /home/user/.stopmotion/tmp and open the files from within stopmotion, it should open without any hassle now.

PS I renamed my files using Metamorphose

---

