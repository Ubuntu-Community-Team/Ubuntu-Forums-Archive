---
title: "Amarok 2; empty collection"
date: 2009-04-24
forum: Multimedia Software
---

### Post by LoermansA on 2009-04-24
Hi all,

I just did a clean install of Jaunty and installed Amarok for my music playing needs. Problem is no matter how often I rescan my collection, it stays empty. The files are there. Amarok now looks very different from the version I used to have (1.4??). The old version worked flawlessly.

Any ideas? I've installed all the plugins Amarok/KDE advised me to.

Regards,

Arjan

---

### Post by LoermansA on 2009-04-24
I deleted ~/.kde/share/apps/amarok and let Amarok recreate the files within this folder.

Now it seems to work again. Weird.

The 'new' Amarok takes some getting used to though, but I'll figure things out.

Regards,

Arjan

---

### Post by noran on 2011-01-12
I know it's a pretty old post, but I've been stuck with the same problem, until I found [this]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269"). One user suggest installing these packages first:
[INDENT] libdbd-mysql-perl (4.012-1ubuntu1)
libdbi-perl (1.609-1)
libhtml-template-perl (2.9-1)
libnet-daemon-perl (0.43-1)
libplrpc-perl (0.2020-2)
mysql-client-5.1 (5.1.41-3ubuntu6)
mysql-server (5.1.41-3ubuntu6)
mysql-server-5.1 (5.1.41-3ubuntu6)
mysql-server-core-5.1 (5.1.41-3ubuntu6)
[/INDENT]
and then installing Amarok. Worked for me. (I'm a newbie so I don't understand the problem or the fix :D)

---

