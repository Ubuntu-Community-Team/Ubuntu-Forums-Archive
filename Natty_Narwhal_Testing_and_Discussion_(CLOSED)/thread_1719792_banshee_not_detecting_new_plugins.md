---
title: "banshee not detecting new plugins"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nerdy_kid on 2011-04-02
Hi everyone, I have installed several new plugins for banshee but none  of them are showing up in the plugins list.  I have no idea why this is so, banshee --debug doesn't spit out anything enlightening.  Any ideas?

Thanks!

---

### Post by gnomeuser on 2011-04-02
Assuming you install plain extensions from the repos this should just work. Try running banshee --debug --debug-addins.

I suspect the problem is the recent renaming from banshee-1 to banshee. You may want to try enabling the Banshee daily ppa as well.

---

### Post by nerdy_kid on 2011-04-03
Great!  That fixed it.  The extensions were going in /usr/lib/banshee-1 instead of /usr/lib/banshee.  A simple simlink and a reinstall of the extensions fixed it :)

Thanks!

---

### Post by lidex on 2011-04-03
That threw an unhandled error at me. I deleted the banshee-1 folder and it completed successfully and all seems to be well.

---

