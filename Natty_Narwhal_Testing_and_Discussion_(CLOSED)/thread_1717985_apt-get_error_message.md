---
title: "apt-get error message"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-03-30
Anyone getting this message ```
update-initramfs: deferring update (trigger activated)
Setting up software-center (3.1.24.4) ...
Updating software catalog...this may take a moment.
2011-03-30 22:31:53,985 - softwarecenter.db.update - WARNING - The file: '/usr/share/app-install/desktop/gnome-do.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application

``` when running sudo apt-get update and upgrade in a terminal, its doesnt seem to affect performance as it is a gnome related file and im sticking with unity (for now). Is anyone else noticing it?

---

### Post by PaulW2U on 2011-03-30
Yes, plenty.

This bug - [https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/731002](https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/731002) - was reported on 8th March.

---

### Post by CaptainMark on 2011-03-30
ah i checked launchpad too, im rubbish at getting the keywords right though, ive marked as being affected then thanks

---

