---
title: "access denied to play DVDs"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by thedivvy on 2007-11-24
Hi this is my first post and I'm a complete newb to (K)Ubuntu (I'm running Gutsy).

I'm having problems getting access to my DVD (playing, managed a copy DVD okay using K3B:confused:), I tried the following command:

:~$ sudo mount /media/cdrom0/ -o unhide

and got:

mount: block device /dev/hdb is write-protected, mounting read-only
mount: /dev/hdb already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdb is already mounted on /media/cdrom0

Can someone help please?
Thanks

---

### Post by deruberhanyok on 2007-11-24
You shouldn't need to run anything at the command line to play a DVD. You're talking about watching a DVD movie, right?

You'll need the "libdvdcss2" package from [Medibuntu]("http://www.medibuntu.org/") to make it play back properly. Once you install that, you should be able to play the movie in Totem (or, since you're using Kubuntu, Kaffeine would be the default app, I think).

[This page](https://help.ubuntu.com/community/Medibuntu) has instructions on how to add the Medibuntu repository to your system (two commands) and tells you what command to run to install the package (one command).

You can also add the repository using the GUI and install via synaptic but I'm not sure what the Kubuntu equivalents of gnome's systems menus are, maybe someone using Kubuntu could help there?

---

### Post by mdpalow on 2007-11-24
... or ... see the link below in my signature for help.

---

