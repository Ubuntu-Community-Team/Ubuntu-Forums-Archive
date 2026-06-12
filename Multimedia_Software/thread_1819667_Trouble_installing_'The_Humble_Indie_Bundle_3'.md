---
title: "Trouble installing 'The Humble Indie Bundle 3'"
date: 2011-08-06
forum: Multimedia Software
---

### Post by Crackity Jones on 2011-08-06
I am still have trouble installing software on Ubuntu (having just returned to it after a long hiatus).
Three of the games from the [Humble Indie Bundle]("http://www.humblebundle.com/") ('And Yet It Moves', 'Revenge of the Titans' and 'Osmos') were easy installs as I just had to go through the double-click .deb > Software Centre procedure.

However, 'VVVVVV' is a tar.gz, 'Braid' is a run.bin, 'Minecraft' is a .jar (I get its Java, but how do I get it into the games menu?), 'Hammerfight' is a .bin, 'Zombie Atom Smasher' is a .tar and the rest have the same file extensions.

So a few questions: How do I go about installing these? Why aren't they all .deb? And how do you keep the above installs clean?
By clean installation I mean they go to the correctly allotted place (so usr/games rather than the home folder and appear within the Applications > Games menu), are easy to uninstall without leaving crap behind and lastly are easy to update.

I understand that this is a nooby question, but I really want to stick with Ubuntu and as long as I feel completely in control of what I am installing/uninstalling than I will be a lot happier.

Much thanks for any of your help.

---

### Post by BicyclerBoy on 2011-08-06
I have installed/run some of them.
All the previous humble bundles were an odd collection to archives bins debs etc.

Penumbra Overture installs into /user/games/

They all just work if you set the executable bit/flag in the file properties or just double click & let the automatically associated program deal with it..

The .tar.gz  is a compressed tarball (native linux)
The .jar is a compiled java archive.
The .bin  is a ?? but it just works (set the execute flag)

The easiest way to install is just to extract the archives into your /home folder from the GUI tools.
Using the command line tools should let you install into system folders.This may just cause other file access problems. Sorry this does not really address your concerns..
Removal is just deletion.
The only updates will be by patching tools or complete replacement.

The .deb can be managed by synaptic.

Making a .deb package is quite complicated & may not be necessary if the program is self-contained & has no dependencies & has no updates via synaptic.

I'm glad they added the bundle #2 into #3 because I missed that one.
Frozenbyte bundle was not so exciting but worthy of support..

---

