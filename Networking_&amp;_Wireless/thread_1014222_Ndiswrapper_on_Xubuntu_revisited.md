---
title: "Ndiswrapper on Xubuntu revisited?"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by FlamingZebra90 on 2008-12-17
I'm trying to set up ndiswrapper on my xubuntu install

i found exactly what i'm looking for here:

[http://ubuntuforums.org/showthread.php?t=476735](http://ubuntuforums.org/showthread.php?t=476735)

But the links are all dead.

I have no wired connection available.

can anyone direct me to the correct links?

Thanks in advance.

---

### Post by Ayuthia on 2008-12-17
> **FlamingZebra90 said:**
> I'm trying to set up ndiswrapper on my xubuntu install

i found exactly what i'm looking for here:

[http://ubuntuforums.org/showthread.php?t=476735](http://ubuntuforums.org/showthread.php?t=476735)

But the links are all dead.

I have no wired connection available.

can anyone direct me to the correct links?

Thanks in advance.
The three links in that thread point to the ndiswrapper packages.

As far as I know, ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk are all on the liveCD.  If you have that, you can add it to your list of repositories:
```
sudo apt-cdrom add
```Insert the CD when asked.  Then do the following:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
sudo apt-get install ndisgtk
```

Hope that helps.

---

