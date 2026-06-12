---
title: "Latest updates want to remove ubuntu-desktop"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-04-06
Beware! update-manager-core is the offending item.

---

### Post by zika on 2011-04-06
> **Quackers said:**
> Beware! update-manager-core is the offending item.
Not with aptitude safe-upgrade...

---

### Post by Harry33 on 2011-04-06
> **Quackers said:**
> Beware! update-manager-core is the offending item.

Perhaps the package update-manager_0.147.3_all.deb is not yet in repos,
only update-manager-core is.

---

### Post by Quackers on 2011-04-06
> **zika said:**
> Not with aptitude safe-upgrade...

Not with synaptic either :-)

---

### Post by cariboo on 2011-04-06
I just updated using synaptic, it didn't ask to remove ubuntu-desktop, but smbclient is broken.

---

### Post by Quackers on 2011-04-06
Yes, it seems the update-manager-core has been fixed. As you say cariboo907, smbclient is broken. C'est la vie!

---

### Post by ktneely on 2011-04-07
> **Quackers said:**
> Yes, it seems the update-manager-core has been fixed. As you say cariboo907, smbclient is broken. C'est la vie!

I'll just wait until tomorrow to update.  Hopefully by then both smbclient and update-manager-core are fixed.  It's a bit scary, I don't usually look at what's about to be removed.  Thankfully I did this time.

---

### Post by beew on 2011-04-07
I use Synaptic to update too, nothing was removed. However, unless something has changed in 11.04, I think Ubuntu-desktop is a meta package, removing it is not going to literally remove your desktop. I have done it many times before and nothing bad happened (it got removed when I uninstalled file-roller and evince from Lucid, just one release ago these were crappy apps but they have improved tremendously in Maverick,--but Lucid still use the same crap versions,  one reason not to use LTS :)  I did it several times because I had several Lucid installs)

---

### Post by Harry33 on 2011-04-07
> **beew said:**
> I use Synaptic to update too, nothing was removed. However, unless something has changed in 11.04, I think Ubuntu-desktop is a meta package, removing it is not going to literally remove your desktop. I have done it many times before and nothing bad happened (it got removed when I uninstalled file-roller and evince from Lucid, just one release ago these were crappy apps but they have improved tremendously in Maverick,--but Lucid still use the same crap versions,  one reason not to use LTS :)  I did it several times because I had several Lucid installs)

The removal of any or all of these meta packages does not hamper your system:
 - ubuntu-desktop
 - ubuntu-standard
 - ubuntu-minimal

These are needed to make the installation process easier.
If you want to personalise your setup, it is often imperative to remove some of the meta packages.
Meta packages do not contain anything else than dependency rules.

---

