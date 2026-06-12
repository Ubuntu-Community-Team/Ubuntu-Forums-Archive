---
title: "python-packages being removed"
date: 2010-12-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2010-12-20
Hi guys,

for over a week now synaptic wants to uninstall several python-packages (and non-critical dependent packages) when updating like python-gtkhtml2, python-beagle, python-gnome2-desktop, pathon-sexy, python-gnomeprint...

The python 2.7 rebuild should be done by now (at least I think so) and I also cant't find these packages in the natty archive.

Am I right to assume these packages as being deprecated and safe for removal?

---

### Post by Harry33 on 2010-12-20
What is your distro exactly? Natty-alfa1? 32-bit or 64-bit?
How did you try to install synaptic? What version of synaptic?

---

### Post by moviemaniac on 2010-12-20
My distro is listed in my signature and since this is the natty development-board I'm using natty with the latest (installable) updates.

And no, I'm not trying to isntall/update synaptic, I'm using synaptic to update my system, manually selecting the packages because I don't trust (amongst others) the automatic dist-upgrade and safe-upgrade options of apt-get and aptitude (and I never ever use the default update-manager as it blatantly ignores locked packages).

I just want to know whether I can (safely) remove these (old?) packages listed above, because they're breaking dependencies of newer packages depending on python 2.7

---

### Post by Harry33 on 2010-12-20
> **moviemaniac said:**
> Hi guys,

for over a week now synaptic wants to uninstall several python-packages (and non-critical dependent packages) when updating like python-gtkhtml2, python-beagle, python-gnome2-desktop, pathon-sexy, python-gnomeprint...

The python 2.7 rebuild should be done by now (at least I think so) and I also cant't find these packages in the natty archive.

Am I right to assume these packages as being deprecated and safe for removal?

You may remove them.
To be sure nothing unexpected happens, remove them manually with synaptic (complete removal).
Synaptic shows those as local or obsolete, since they are not found in official Natty repos.

---

