---
title: "[SOLVED] Mediatomb daemon missing"
date: 2008-12-24
forum: Multimedia Software
---

### Post by chrisbaume on 2008-12-24
Hi everyone, merry christmas. I'm trying to get mediatomb installed on my headless ubuntu server so the PS3 under the tree will be able to use it.

I installed mediatomb a while back, but then got rid of it after something went wrong with the daemon. I'm afraid I don't remember exactly what I did, but the apt-get remove function didn't work as one of the files was corrupt. I had to remove some things manually before apt-get remove worked. Now, when I install mediatomb, the daemon doesn't appear in /etc/init.d.

I ran the following (to make sure everything's gone, it just says that it's not installed)
[FONT="Courier New"]sudo apt-get autoremove mediatomb mediatomb-common mediatomb-daemon[/FONT]

...then I run
[FONT="Courier New"]sudo apt-get install mediatomb-common mediatomb-daemon[/FONT]

I can't run [FONT="Courier New"]/etc/init.d/mediatomb[/FONT] as it doesn't exist, so I have to run [FONT="Courier New"]mediatomb [/FONT]every time the server is turned on.

Can anybody think of a reason the daemon wouldn't get installed in /etc/init.d? Thank you and I hope you're enjoying the holidays! :P

---

### Post by chrisbaume on 2008-12-24
Fixed it!

Used the following command:
[FONT="Courier New"]sudo dpkg --purge mediatomb-daemon[/FONT]
to remove the package including the configuration files, then installed again using:
[FONT="Courier New"]sudo apt-get install mediatomb-daemon[/FONT]

---

