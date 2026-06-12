---
title: "Default Volume Level"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by matthen on 2007-01-28
Hi,
Quick question-
When I login, my volume is set to maybe 80%, and I alway have to load it up to 100%. Is there a way to have it automatically at 100%?

Thanks,
Matt

---

### Post by matthen on 2007-01-29
I found a solution, in case anyone is interested:

install aumix:
sudo apt-get install aumix

then create a file "/home/username/volume100.sh"
with the contents:

#! /bin/sh
aumix -v100

and make it executable. (right click, permissions, allow executing file as a program)

Then go to System->Preferences->Sessions, and in the Startup Programs tab, add '/home/username/volume100.sh'

That works for me

Matt

---

