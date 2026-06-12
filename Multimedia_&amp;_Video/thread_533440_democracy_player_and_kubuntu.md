---
title: "democracy player and kubuntu"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by ticstah on 2007-08-23
I've been running feisty fawn on my clunker laptop since it was released, so I decided to try kubuntu on my desktop. so far I like it, I think kde's interface is slick. I've been getting all of my codecs and programs in order (avoiding automatix as per suggested) but I don't seem to have much luck with democracy player.. and I NEED it to get my video podcasts.

so I tried installing it using adept. after it installed it would just sit and do nothing. so I uninstalled it through adept and attempted to install it through apt-get.

after it was finished I tried running it in the terminal and got this:
> Traceback (most recent call last):
  File "/usr/bin/democracyplayer.real", line 21, in <module>
    import gtcache
  File "/var/lib/python-support/python2.5/democracy/gtcache.py", line 5, in <module>
    import config
  File "/var/lib/python-support/python2.5/democracy/config.py", line 9, in <module>
    import platformcfg
  File "/var/lib/python-support/python2.5/democracy/platformcfg.py", line 20, in <module>
    import gconf
ImportError: No module named gconf

now I noticed that it said there was no module named gconf, so I went ahead and did an apt-get on gconf. it seemed to install fine, I rebooted X and I get the same result when trying to run democracy player.

any ideas? will this program just not run in kubuntu?:confused:

---

### Post by ticstah on 2007-08-24
bummmpppp:guitar:

---

