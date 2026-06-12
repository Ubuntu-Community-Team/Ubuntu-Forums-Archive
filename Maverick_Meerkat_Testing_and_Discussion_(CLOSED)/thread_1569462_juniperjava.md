---
title: "juniper/java"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ppb1701 on 2010-09-06
Found one little hiccup since I bumped from lucid to maverick beta.  Went this evening to connect to works  juniper ssl vpn.  Page signs in fine, applet starts then spits out session timeout and kills the applet.  I had no trouble with it in lucid or karmic.  Everything else I've tried so far seems to work great.

---

### Post by kahumba on 2010-09-06
It looks like Sun/Oracle java isn't available in the Maverick repos so perhaps (in Maverick) you're using the openjdk version and hence perhaps that's the reason.

---

### Post by ktp on 2010-09-06
> **kahumba said:**
> It looks like Sun/Oracle java isn't available in the Maverick repos so perhaps (in Maverick) you're using the openjdk version and hence perhaps that's the reason.

sun/oracle java wasn't part of lucid repository also.  It was [moved to partner repository]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun Java moved to the Partner repository").

---

### Post by kahumba on 2010-09-06
> **ktp said:**
> sun/oracle java wasn't part of lucid repository also.  It was [moved to partner repository]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun%20Java%20moved%20to%20the%20Partner%20repository").
If you read between the lines you know what I mean. Sun/oracle java in Maverick isn't available even in the "partner" repos, or is it?

---

### Post by ppb1701 on 2010-09-06
nope only have sun java one installed, had some of the others but at one point they started fighting amongst themselves so I cleaned house.  Synaptic says it's still there but only has removal options available.  my first thought after trying both browsers i use and then a different pc was to attempt to reinstall it.

mostly seemed odd before if it had a problem with the jre it just didn't load the applet at all and spun its wheels on the loading page.  this time it actually starts up the applet but throws the time out and dies.

---

