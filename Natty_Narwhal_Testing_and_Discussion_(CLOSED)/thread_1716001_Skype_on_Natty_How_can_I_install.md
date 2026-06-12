---
title: "Skype on Natty? How can I install?"
date: 2011-03-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donalgodon on 2011-03-27
Can anyone please help me to install Skype on Natty? I've failed at the install so many times that I'm starting to get frustrated.

The .deb is useless in Software Center and fails with:

Lintian check results for /home/user/Downloads/skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb:
E: skype: description-starts-with-package-name
W: skype: extended-description-line-too-long
W: skype: extended-description-line-too-long
W: skype: possible-unindented-list-in-extended-description
W: skype: new-package-should-close-itp-bug
W: skype: binary-without-manpage usr/bin/skype

Everything I've tried so far has failed. :(

---

### Post by idef1x on 2011-03-27
If you're getting frustrated when trying to install something on an currently alpha release, then stick with the stable releases. Maverick is in this case the latest and installing skype from the depositories works like a charm...

Alpha releases are ment for people who don't mind if their system get's screwed up or if something is not working...

---

### Post by mc4man on 2011-03-27
you could go - 
dpkg -i /path/to/the_name_of_your_.deb

or install gdebi, then r. click on your .deb and choose gdebi
(or r. click on any .deb > properties > open with and switch default for packages to gdebi

or remove the lintian package
(there are some additional non lintian debian ck.'s that aptdaemon does but shouldn't affect skype
Software center can't run a lintian ck. if lintian isn't installed

---

