---
title: "Please suggest a photo edit program besides Gimp (for levels)"
date: 2021-01-21
forum: Multimedia Software
---

### Post by jmichaels29 on 2021-01-21
I'm having a problem with the latest version of Gimp and retaining EXIF (see my post at [https://ubuntuforums.org/showthread.php?t=2456876](https://ubuntuforums.org/showthread.php?t=2456876)).

Could users please suggest a photo editor program, that is in Ubuntu Software) that allows me to adjust levels of a photo (I liked to do an "auto levels" in Gimp).

---

### Post by simon-webb on 2021-01-21
In the post to which you linked above, you were advised against building your own copy of the older version of GIMP because "that'll be a hassle". Yes, if you're not used to building from source it will probably take you at least half an hour to figure it out and get it done...but to me, that sounds like a lot less hassle than learning to use a completely different image editor if you're familiar with and comfortable in the GIMP. So, whereas I could point you to Krita (the KDE project's rough equivalent of the GIMP, a fairly full-featured image editor that does have capabilities like auto-levels), I would actually recommend giving the source build of the GIMP a go. The build instructions (for which the link was provided in the reply that advised you not to bother) include a "GIMP Requirements" link: note that those requirements are all in the Ubuntu repositories and so can be installed effortlessly the usual way (apt install foo)...after which it's entirely possible that the source build will "just work" and you'll have a working copy of the older GIMP program after a few minutes of watching it compile (it is a big program so does take a while to build...from memory I think it can take as long as five minutes, maybe even longer on slow hardware).

The only tricky part or "hassle" is that you would need to learn a lot more to package it properly and build it as a .deb that installs to your system like any other Ubuntu package. You don't have to do any of that, though. I grabbed a tarball of GIMP version 2.8.22 just now, and sure enough, the traditional --configure / make / make install steps are all you need to do...so, if you configure it to install as a normal user (somewhere under your /home directory) it may work without problems...you could be back on the version you want in a matter of minutes. The steps are as follows:

1) Unpack the tarball (if it's a .bz2, the exact instruction is tar -xjf gimp-2.8.22.tar.bz2)
2) Go into the directory (cd gimp-2.8.22)
3) Configure to run under a custom directory, let's say my-gimp: (./configure --prefix=/home/yourname/my-gimp)...and obviously create that directory
4) Assuming you've installed all the required packages (the list mentioned earlier) it should configure successfully
5) Compile it by simply typing make
6) Install it (into your custom directory) by typing make install
7) Now you can run it by going into the program directory (e.g. /home/yourname/my-gimp/bin) and typing ./gimp
8) Finally, creating a .desktop file in .local/share/applications will enable you to add it to your desktop menus

If that looks like too much work, maybe give Krita a go...but honestly, from what I know about workflow and familiarity with particular tools, it seems to me as though you could be looking at many hours of learning before you're comfortable in a new image editor, so it might be less hassle just to build your own GIMP.

One final option that you might not have considered is to downgrade your whole OS to Bionic (Ubuntu 18.04 LTS)! I'm certainly not recommending that (and it might only be postponing the same problem anyway, to when you do have to upgrade), but if you've just recently installed Focal (or whatever you're running that uses a more recent GIMP than 2.8.22) and haven't put a lot of time into setting it up yet, it's something to consider: Bionic is still supported until 2023, so there's no hurry to upgrade it...and on Bionic, grabbing a working GIMP 2.8.22 is as easy as apt install gimp.

---

