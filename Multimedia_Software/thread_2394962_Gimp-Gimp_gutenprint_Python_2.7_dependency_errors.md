---
title: "Gimp-Gimp gutenprint Python 2.7 dependency errors"
date: 2018-06-24
forum: Multimedia Software
---

### Post by oceola2 on 2018-06-24
First- is with 18.04, Intel processor.currently up to date.

Using Synaptic this morning I installed/tried to,  Gimp.
There were a number of errors and a demand for a Pythin 2.7 package and another no such package Gimp:amd64,
What is odd is Gimp opens and appears to function though a number of packages were not installed:
Those were listed in the error as python2.7; python;gimp; gimp-gap; python gtk2; python gobject2 and python Cairo amd64
An error message was sent.
However, though Gimp opens and appears to function there is no listing in Synaptics history and when opening Ubuntu Software install shows but no remove.

Tried  copying a current Python 2.7 package to /var/cache/archives along with the Python 2.7- minimal but to no avail.
Nothing shows for dependencies/bugs in Launchpad I could find.

Any ideas or thoughts?

---

### Post by Yellow Pasque on 2018-06-24
Is it possible you have a Snap version installed as opposed to standard .deb package?

---

### Post by oceola2 on 2018-06-25
@Temujin -believe it is the one from the Universe repository, best I can remember. Versions: gimp_2.6.22-1_amd64.deb ; gimp-gutenprint_5.2.13-2_amd64.deb
Upside to this is all the packages which supposedly aren't there, are there and functioning including gimp-gutenprint.
This may be some other issue other than supported package, it could be some simple history or dpkg recognition issue by synaptic or the gnome software installer.
It doesn't show as installed but the icon is in the gnome icons and opens files, uses brushes changes things, Guten print is also in the Gimp menu and functions as well.
Beyond me but I'll do a search through the dpkg install listing and see if it's there, which it should be.
Only time something doesn't show is if I install using a tar ball and there will be warnings from synaptic it can't find an update.
This just warned of a no install and the dependency as stated above.

---

### Post by mc4man on 2018-06-25
run this to see
```
snap list
```

---

### Post by oceola2 on 2018-06-25
@mc4man - ran the command this is the response: **No snaps are installed yet. Try "snap install hello-world".**
I didn't think it was a snap.
P.S: Modern problem reading the post on another OS and running the command, I'm not the brightest penny in the roll.

After looking at the problem I dumped Gimp, Gimp-Gap and Gimp-Gutenprint and each time the list of dependencies showed as not being configured or installed. I copied the list and removed them. What was occurring the dependencies, showing as installed but not for some reason leaving the install dumb terminal also affected other packages, one was Thunderbird, which for some reason would not open and gave a message of close the already open Thunderbird. I removed Thunderbird and the listed dependencies, re-installed  Thunderbird and was able to open it without the previous close message.

I may try and install Gimp through the snap process or see what happens down the road.
Tried to install snap and it failed. It was already on the system, all 65+Mbytes of it but for some reason there was a fresh install which was going to exceed that amount and froze at 55 MB. Makes no sense to waste limited bandwidth on trying to make it work.
Did reinstall gimp et al and have the same error showing up in the dumb terminal but all is functioning.
Maybe there needs to be a simple adjustment there instead of of pushing snap

---

