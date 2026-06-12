---
title: "Upgrade to 0.25 without dist upgrade"
date: 2012-05-29
forum: Mythbuntu
---

### Post by CroccoS on 2012-05-29
Hi,

I'm running 0.24 on 11.10 and want to only upgrade Mythtv to 0.25. When reading the announcement of 0.25 I see:
"When upgrading to 0.25, you will need to use "apt-get dist-upgrade" as the following packages will need to be removed:*libmyth-0.24-0, mythtv-theme-childish, mythtv-theme-metallurgy, mythtv-themes, mythvideo"

I don't want to upgrade ubuntu. How do I upgrade mythtv without dist-upgrade? Can I manually remove the mentioned packages? 

Crocco

---

### Post by bance on 2012-05-29
I'm not an expert on this, but if I understand correctly "apt-get dist upgrade" only replaces the old packages, with those required for the new 'application' . It doesn't upgrade your OS.
See [[COLOR=Red]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1956611") thread, post #10

---

### Post by nickrout on 2012-05-29
bance is correct, the recommended dist-upgrade will NOT upgrade you to another version of ubuntu.

---

### Post by CroccoS on 2012-05-30
Oh...Should have checked that in detail.  Thanks!

---

