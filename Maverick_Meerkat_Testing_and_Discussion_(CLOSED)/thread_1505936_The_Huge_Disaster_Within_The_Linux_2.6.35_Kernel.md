---
title: "The Huge Disaster Within The Linux 2.6.35 Kernel"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2010-06-09
[http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1)

seems it is a failure, SLOW DOWN.
dont tell may 28 is old news!

> The performance of the Linux 2.6.35 kernel code right now is a disaster. There is no other way to put this situation. While, yes, there still is a number of weeks left before the Linux 2.6.35 kernel release, it's inexplicable that a regression like this or change in behavior can even be accepted into the mainline Git tree at any point in the development cycle for such a mature project. That it can not only enter the kernel tree, but it can live for a week or more without either being corrected or the problematic commit being reverted. This is such a glaring performance issue across so many different tests and differently configured systems that it calls to question the current development practices and test procedures of the Linux kernel. These performance problems are affecting systems from Atom desktops to multi-core, high-end notebooks in tests from media encoding to synthetic disk tests.

---

### Post by jfernyhough on 2010-06-09
1) As you've already noted, this is old news based on old code.
2) They are basing the tests on the git tree. Who knows what else was enabled at that point? In fact, wasn't that just before rc1 was released? Is it possible that extra debugging (or whatever) was enabled because of this?
3) Phoronix loves graphs. :D

---

### Post by ronacc on 2010-06-09
the Phoronix article only mentions the atom processor . Subjectively I am not seeing any slowdown on my AMD64x2 sys with the 35-1 kernel .

---

### Post by VMC on 2010-06-09
> **sdowney717 said:**
> [http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1)

seems it is a failure, SLOW DOWN.
dont tell may 28 is old news!
That article was discussed at length already [here]("http://ubuntuforums.org/showthread.php?t=1499181"). Read some of the negative comments at phoronix regarding the article.

---

### Post by Asraniel on 2010-06-10
and there was a follow up article i think on phoronix when the problems where solved.

---

### Post by forumache on 2010-06-10
Asraniel is right.

28th of May article *is* old news. 3rd of June article is new (same author):

The Big Linux 2.6.35 Kernel Problem Is Fixed
Posted by Michael Larabel on June 03, 2010

Last week we reported on a disastrous bug within the Linux 2.6.35 kernel that while this kernel is still months from being officially released, a major regression was introduced that slaughtered the Linux system's performance. This was experienced across multiple systems, architectures, and file-systems. Today we can officially report that this problem has been resolved.
 
[http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ](http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ)

Watch the new graphs. And don't worry, be happy ;)

---

### Post by questioning on 2010-06-10
how about you/we let that FUD die here and now.

**** "news" are ****.

---

### Post by ronacc on 2010-06-10
why ? a little panic and confusion is good for the soul :p

---

### Post by Mr. Picklesworth on 2010-06-11
The only disaster here is that Phoronix has transformed into the first Linux tabloid. They are intent on making constant noise, and now they've made it to this point it is near impossible for them to slow down. They can only get noisier and noisier and wronger and wronger.

[http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ](http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ)

Okay, I am exaggerating slightly. They have their moments, though&#8230;

---

### Post by wilee-nilee on 2010-06-11
> **Mr. Picklesworth said:**
> The only disaster here is that Phoronix has transformed into the first Linux tabloid. They are intent on making constant noise, and now they've made it to this point it is near impossible for them to slow down. They can only get noisier and noisier and wronger and wronger.

[http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ](http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ)

Okay, I am exaggerating slightly. They have their moments, though…

Atom processor here no problems yet except a slow wifi connect time until todays kernel upgrade. I had been able to speed up the connect time with plugging in the etho wired but it seemed to be more of a placebo effect.

---

### Post by VMC on 2010-06-11
> **Mr. Picklesworth said:**
> The only disaster here is that Phoronix has transformed into the first Linux tabloid. They are intent on making constant noise, and now they've made it to this point it is near impossible for them to slow down. They can only get noisier and noisier and wronger and wronger.

[http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ](http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ)

Okay, I am exaggerating slightly. They have their moments, though…

Actually your not exaggerating. On reading the comments, many are tired of this type of commentary. Specifically from that author. 

They love to confuse the issue by bring up tons of meaningless graphs.

---

### Post by ranch hand on 2010-06-11
Mean while I am enjoying this "diasaster" with the ...35 kernel quite a bit.  Seems to be running very well and very stable.

Maybe I should read more alarmist blogs.

---

### Post by wilee-nilee on 2010-06-11
> **ranch hand said:**
> Mean while I am enjoying this "disaster" with the ...35 kernel quite a bit.  Seems to be running very well and very stable.

Maybe I should read more alarmist blogs.

Ah the alarmist just fuel the bunching. ;)

Sort of like reading the forums and applying it to your own setup, and crying the sky is falling.

---

### Post by Starks on 2010-06-11
Linux tabloid.

Amazing label.

---

### Post by vkontakte on 2010-06-12
> **sdowney717 said:**
> [http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1)

seems it is a failure, SLOW DOWN.
dont tell may 28 is old news!
So slow, it has been fixed already.

---

