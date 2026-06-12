---
title: "Problems using an older version of Ubuntu"
date: 2009-01-18
forum: Multimedia Software
---

### Post by Spoot89 on 2009-01-18
Before I say anything else, I'm running an older version of Ubuntu. 7.04, to be exact. For some reason (I have an older laptop im running it on), the newest version doesn't...look right on my computer. ANYWAYS...

When I go to Applications -> Add/Remove, and search for some new applications, many of them give me the following error message: 

"Banshee Music Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

Now, I find this very strange, because maybe a year ago, I had this same computer running this same version of Ubuntu, and these applications ran just fine.

Any ideas for possible solutions?

---

### Post by hikaricore on 2009-01-18
It sounds like somehow you're trying to install the wrong package like a 64bit or ppc package.

What happens when you do the following from a terminal:

> sudo apt-get clean
sudo apt-get update
sudo apt-get install banshee

---

### Post by mcduck on 2009-01-18
The support for 7.04 ended on October 19th, 2008. So the software servers have already been closed.

You should install more up-to-date version of Ubuntu.

---

### Post by hikaricore on 2009-01-18
Woops didn't read his version number correctly.

I think if you look around you'll find archived versions of the repos for that build but yea, upgrading is probably your best bet like the duck said.

---

