---
title: "ssh on boot?"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by timlardner on 2009-08-05
Hi, I am currently trying to set up a system so that it can be administered remotely. I've had no trouble with this and can use ssh, vnc and the like to connect to it...

But here's the problem. To be able to ssh into the machine, someone needs to log in. I can't just have it powered up and then left. Auto-login would solve this problem but I'm looking for alternatives.

I think the problem is that the system only connects to the wireless network once a user logs on, although it could be to do with the fact the ssh daemon hasn't started yet.

Any thoughts/suggestions/comments would really be greatly appreciated!

Thanks very much,
Tim

---

### Post by jerome1232 on 2009-08-05
I believe wicd can be setup to connect to wifi during the boot process. It can be installed from the repos.

---

### Post by slakkie on 2009-08-05
You could do it like this: [http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwiki.fok.nl%2Findex.php%3Ftitle%3DDig%2Flinux%2Fwireless&sl=nl&tl=en&history_state0=](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwiki.fok.nl%2Findex.php%3Ftitle%3DDig%2Flinux%2Fwireless&sl=nl&tl=en&history_state0=)

(open original page also because google translate messes up formating), or have a look here:
[http://ubuntuforums.org/showpost.php?p=5752871&postcount=2](http://ubuntuforums.org/showpost.php?p=5752871&postcount=2)

---

