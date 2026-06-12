---
title: "Hello. Can't get an Atheros AR8151 LAN card to work"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by jaslamma on 2010-11-17
Hi.

I have used Ubuntu without trouble for quite some time now on my computer (maybe 2 years; recently upgraded to 10.04) and have just bought a new computer for the office.

When I install 10.04 on the new computer it doesn't seem to recognise the lan card, an atheros AR8151 onboard card (on a GA-G41MT-S2 mobo).

Any suggestions?

p.s. phrases such as 'build-essentials', 'sudo' and '.tar.gz' files don't mean anything to me (except the last is a bit like a zip file I think).

Thanks if you can help,
jim

---

### Post by misGnomer on 2010-11-19
While the (eternally) ongoing effort is to make things just work, it is always helpful to familiarize yourself with the basic workings of Linux/Unix.

There are plenty of primers to choose from, e.g.:

[Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/download_main.html") or [Introduction to the Ubuntu Desktop Guide]("http://linux.about.com/od/ubuntu_doc/a/ubuntu_doc_idx.htm") (about.com).


Now, Ubuntu 10.04(.1) Lucid doesn't ship with the AR8151 driver (although if people file bug reports it might get added to upcoming 10.04.0**x** LTS refreshes).

The good news is that you can add the driver yourself and there's a [hand-holding guide for it]("http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential") already (see [msg #7]("http://ubuntuforums.org/showpost.php?p=9738022&postcount=7") specifically).

The bad news is that unless/until the driver gets backported to the 2.6.32.x kernels Lucid uses, you'll have to repeat the process every time the kernel is updated.

Still, after doing it once the process is easier to repeat... I would recommend that you create a folder titled "ar8151" in your home directory and then add a text file titled "ar8151_howto" in it. In that text file you should copy useful URLs (like the link to the ar8151 install guide by 1awesomeguy, above), the location of the Atheros drivers (so you'll get the latest one) and e.g. the complete text of the guide (with URLs in clear text).

Download atheros driver package there as well and cd (change directory) into that directory before untarring/unzipping, building and installing it (the last step in the guide). That helps keep everything neatly in one place.


Other and potentially easier options to building the driver yourself for every new Lucid kernel update are:

#1 trying out a newer backported kernel (e.g. 2.6.35). There ought to be a PPA repository for Lucid somewhere to make the installation painless (although you still need to build and install the driver manually once to get your network going)..., or

#2 trying out Ubuntu 10.10 Maverick which ships with the 2.6.35 kernel and really ought to include ar8151 support out of the box. (maybe someone can confirm this?)

Hope this helps you get started.


PS. In the future consider searching the forum using keywords like "ar8151" prior to starting a new thread... ;)

---

