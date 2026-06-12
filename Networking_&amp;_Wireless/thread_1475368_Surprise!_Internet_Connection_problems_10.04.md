---
title: "Surprise! Internet Connection problems 10.04"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by cetacean on 2010-05-06
Seems to be an inordinate amount of activity recently on this one. I can connect on my new Acer dual-boot (Win7 & Lucid) using either ethernet or wirelessly on Atheros AR5B93 under Windows, but only occasionally with the ethernet plug under Lucid.

I run Update Manager whenever I can get on with Ubuntu, but that does not help the wireless problem.

Under Windows, I have downloaded a couple of possible fixes mentioned here and elsewhere, and have a couple of .tar files just sitting there.

How do I get them from my windows downloads folder to where they need to be in my Ubuntu partition, extract them, and install them?

I have a feeling that I possess the solution to my problem, if I can just apply it.

Thanks for your help.

---

### Post by cetacean on 2010-05-13
I have posted at least a dozen questions here, and elsewhere, about getting a wireless signal on my clean new Acer/AMD/Atheros laptop, in various ways, under various user names.

I can boot into Windows and connect via ethernet or wireless, no problem at all, and via ethernet under Ubuntu - but try to connect wirelessly - dead meat.

Quite a few people on this forum have been wonderfully helpful to give me numerous methodologies to fix this - all failed. I have downloaded and installed loads of crap, done Madwifi, I run update manager, sudo apt-get update, Synaptic - pure nada.

I am a newbie here with decades of Microsoft experience. I really like like the Ubuntu concept and just about everything I have tried has worked - sometimes immediately - sometimes after several convoluted iterations. 

I have to admit, I don't really "get it" yet, but this seems to be a gaping chasm that a whole lot of users have fallen into.

"lspci" reports that this situation involves an Atheros AR928X wireless network adapter although other sources name slightly different flavors of hardware.

This is obviously a massively widespread problem since there have been dozens of posts every day with "wireless" and "10.04" in the subject line since April 29.

I am serious about migrating from Windows to Ubuntu but this kind of stumbling block is close to a deal-killer. 

Realistically, what can I expect to happen in the near future?

---

### Post by NUboon2Age on 2010-05-14
It looks like this is a double posting -- also why use multiple user names??? For anyone who'd like to help you (like me) it just makes our work so much harder.

I'm wondering if you have the infamous Broadcom B43xx or B44xx problem.  if I knew what other user names you'd posted under I could tell (but since under this username you haven't provided enough detail to tell I can't).  If so yes this is a major pain in the rear.  It was a problem w/ lack of cooperation of the proprietary manufacturer previously, but the Linux community was able to get it working, but I'm also running into this problem now w/ 10.4.  I signed onto bug #51139.  I would recommend looking on bugs.launchpad.net to see if others are having your problem and if so subscribe to something that sounds similar.  Here's mine:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379)

---

