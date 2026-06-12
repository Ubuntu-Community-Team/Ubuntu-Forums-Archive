---
title: "Backporting Audacious from 11.10 to 10.4"
date: 2012-03-17
forum: Multimedia Software
---

### Post by Silvernail on 2012-03-17
Oneiric Ocelot
Gnome 3
Audacious 2.4.4

I am giving up for the nonce. For nearly 2 weeks I have searched for a solution to this problem. I seem to be the only one having it.

I like Audacious. It gives me my music the way I want it. I've use it since before 10.4 and know how to work it.

The distribution, 2.4.4, that came with Oneiric does not have the tools/buttons to build, load, save, delete play lists. And while using the import command it will list the playlist  from my old installation, it will do  nothing with them.

I would like to backport to the version I had on Lucid 10.4 if that can be done.  I have never done a backport before and a search of this site for 'audacious backport' was not too helpful.

Can someone direct me to a tutoral on this.
Thanks
Dave

---

### Post by Yellow Pasque on 2012-03-17
The version of audacious (2.4.x) is Oneiric is really outdated ( [https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/889585](https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/889585) ). Rather than trying to build an even older version, you should try and build audacious 3.2.x, which has better support for playlists and more features/fixes.

EDIT: Actually, you don't need to build it. Try it here: [https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

---

### Post by Silvernail on 2012-03-17
Great! Thanks.

---

### Post by Silvernail on 2012-03-17
Works beautifully. Audacious 2.2 sending musci to my ear.

I will say that I must suffer a generational communications gap.
By chance discovery I found that 'Import' and 'Export' now mean 'Load' and 'Save'.

---

