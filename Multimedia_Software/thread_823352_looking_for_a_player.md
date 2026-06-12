---
title: "looking for a player"
date: 2008-06-09
forum: Multimedia Software
---

### Post by aboren on 2008-06-09
i'm watching xvid or divx
and i'm looking for a player that can play those and remember the last movie position event if i close the player and open it later.
it also need to support subs
10x

---

### Post by Pjotr123 on 2008-06-09
You could apply this how-to and then find out which player suits you best:
First this:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and then this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by ceb0 on 2008-06-09
I reckon you're looking for smplayer:

[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

It's in the repos too.

---

### Post by shr2004 on 2008-06-09
A word of coution about SMplayer. I installed SMplayer just for a go. Guess what happened. Earlier I was able to play most video files and pitures were perfect. After installing SMplayer all videos become too contrasty..i.e. the contrast of the picture become too high and hard to watch. So i removed SMplayer as well as attached Mplayer, Now everything is just fine. Dont know what might be the reason.

---

### Post by pmlxuser on 2008-06-09
I would suggest Mplayer for that .. and then check the forumns on how to configure it according to your specification.

---

### Post by rvm4000 on 2008-06-09
> **shr2004 said:**
> A word of coution about SMplayer. I installed SMplayer just for a go. Guess what happened. Earlier I was able to play most video files and pitures were perfect. After installing SMplayer all videos become too contrasty..i.e. the contrast of the picture become too high and hard to watch. So i removed SMplayer as well as attached Mplayer, Now everything is just fine. Dont know what might be the reason.

That problem could be easily solved by editing ~/.smplayer/smplayer.ini and set dont_use_eq_options to true.

The problem happens because, by default, smplayer sets the brightness, contrast... to 0 every time a video starts to play. That should give a normal image, but it seems for some people the image is too bright or with high contrast.

---

