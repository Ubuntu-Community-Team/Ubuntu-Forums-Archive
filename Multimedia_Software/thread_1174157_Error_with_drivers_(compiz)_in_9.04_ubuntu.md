---
title: "Error with drivers (compiz) in 9.04 ubuntu"
date: 2009-05-30
forum: Multimedia Software
---

### Post by CynicalPsycho on 2009-05-30
So I recently installed ubuntu 9.04 (jaunty) 32bit.
I was going through and setting everything up the way i like and then I get to compiz.

First off I couldn't download it through synaptic so i had to get the repository and update my sources . Then once I get it up I try and install my drivers through:
**system>administration>hardware device **
and at first it shows up with 2 drivers and I try to get the recommended one and it takes like 5 minutes just to come back with this error:

```
Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-commonn
```

So I try again and then it just shows the load bar go back and forth at zero percent... and never does anything else...

I've tried restarting the comp and trying again only to find myself repeating the cycle yet again.

I've also tried adding the drivers to the repository... which gets me this when i try to download them:

> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

does anyone have any solutions, suggestions, or recommended reading?

---

### Post by CynicalPsycho on 2009-05-30
[SIZE="5"]**Solution Found**[/SIZE]
Surfin the net I stumbled across a quick fix, not sure why it works but for some reason if you go into your software sources:
**system>administraion>software sources**
and then uncheck **installable from cdrom**

after that I restarted tried again and it downloaded my driver and worked fine...

---

