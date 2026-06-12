---
title: "Cannot get Mediatomb running again"
date: 2016-11-29
forum: Multimedia Software
---

### Post by MorneDJ on 2016-11-29
Hi All. I had Mediatomb installed for the past year on Ubuntu server 14.04, chucking along happily. I then noticed that it is not updating the database as I like, and after following a few pages on the net, changing the config file, it stopped working. This is where I made my first error, I did not backup my old config file (/etc/mediatomb/config.xml). Second mistake, I did not look at /var/log/mediatomb to see what was the problem.

No problem I thought. I did an uninstall and reinstall. Nope. Nothing. Dit a remove and autoremove. Reinstalled. Nothing. Did a remove --purge and autoremove. Reinstalled. Nothing. I noticed that my config file remains under /etc/mediatomb/, so I deleted that but after the install mediatomb did not reinstall the config file (neither the /etc/default/mediatomb which I also deleted). I guess it is because there is a setting somewhere where Ubuntu logged that mediatomb was previously installed and that it is assuming that the config files are present. 

Anyone know where I can remove that setting, or how I can do that. The purge, remove and autoremove commands does not reset this.

---

