---
title: "ATI TV as only output"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by DrMega on 2007-12-08
Hi

I have recently upgraded from Dapper (6.06) to Gutsy (7.10) on my media centre PC.

My problem is that I can't get Gutsy to work with just the TV (ie no monitor attached).

* Dapper works fine directly on TV, with no monitor.
* Gutsy has TV out WITH monitor attached
* Gutsy - nothing happens if i try to boot with just tv (no  monitor).
* I have copied xorg.conf from Dapper build (works fine) to Gutsy build.

I'm kind of out of ideas, unless it is a bug between versions of the ATI driver.

I know ATI is pants  and I should get a nVideo card, but in the meantime, any ideas?

Thanks.

---

### Post by DrMega on 2007-12-09
Come on guys, I know there are many geniuses on here that could point me in the right direction.

---

### Post by DrMega on 2007-12-09
***UPDATE***

I have discovered that the problem is not with the ATI driver, but an issue with Ubuntu. It seems that booting with the 'SPLASH' option causes the graphics driver config to be somehow ignored. I edited menu.lst to remove the 'SPLASH' option, so I just get text on screen during boot up, and it now works.

---

