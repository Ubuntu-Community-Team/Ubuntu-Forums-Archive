---
title: "Troubles in maverick after natty downgrade"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Rackstar on 2011-01-22
Hey,

Yesterday I was about to do a fresh install of my maverick laptop, but I accidently installed Natty (which I'm testing on a different laptop). 

When I realized I installed Natty, I did a clean install of Maverick. However, I do have my /home on a different partition, and it seems the install of natty changed some of those settings, leaving me with a rather annoying problem.

When I start up, I do not have a WM, I only get my desktop (with files), no gnome-panels.

I already deleted all my .gconf.gconf2 .gconfd ... files once. But I'm still having this problem.

Any ideas?

Thanks!

---

### Post by Rackstar on 2011-01-22
I think I solved it.

I needed to remove the gnome entries under .local/share/applications as well. Don't know what it did, but it fixed it

---

