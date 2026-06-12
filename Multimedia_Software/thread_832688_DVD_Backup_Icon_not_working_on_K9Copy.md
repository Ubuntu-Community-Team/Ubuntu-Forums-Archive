---
title: "DVD Backup Icon not working on K9Copy"
date: 2008-06-17
forum: Multimedia Software
---

### Post by artnz on 2008-06-17
Since upgrading to Hardy Heron the DVD Backup Icon is now greyed out.

The menu command is there but does not work.

Yes, I have installed all the necessaries from Medibuntu but still no joy.

Any ideas please?

---

### Post by xc3RnbFO8P on 2008-06-18
I would install (reinstall)this:
kdebase-bin, kdebase-bin-kde3, kdelibs4c2a,
kdelibs-data, kipi-plugins

Restart the computer

Install K9copy again in Synaptic Package Manager(if it doesnt work)
Still doesnt work:
libiso9660-5
mencoder

You can also install K3B from Synaptic Package Manager:
libmad0
libmad0-dev
python-pymad

k3b
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

---

### Post by artnz on 2008-06-19
Many thanks for your response.

I have now tried all your options but still no joy.

I think it is time to admit defeat.

Thanks again.

---

### Post by mc4man on 2008-06-19
> The menu command is there but does not work.
There is no menu command for dvd backup, it's a setting (should be checked)
There are 2 dvd icons, 1 for copy and 1 for create, are they both greyed out? The one on right should be greyed out.
Have you tried loading a dvd? (folder icon)

---

