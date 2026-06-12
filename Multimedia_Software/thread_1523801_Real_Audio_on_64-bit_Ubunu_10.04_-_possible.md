---
title: "Real Audio on 64-bit Ubunu 10.04 - possible?"
date: 2010-07-04
forum: Multimedia Software
---

### Post by samalex on 2010-07-04
Hi, 

Our local NPR station only broadcasts in Real Audio format online, but the Real Audio client is not available for 64-bit Linux.  Any suggestions on how to either install it or how to add Real Audio support to mplayer or one of the other media players in Linux?

Edit: Real Audio is available in the repositories, but whenever I try to start a stream it just closes.  I'm troubleshooting it now, but are there any other suggested ways to get RA working? 

Thanks --

Sam

---

### Post by sxmaxchine on 2010-07-04
try installing helix player because real player is made by helix so it might support real audio if not try installing real player using wine.

---

### Post by sxmaxchine on 2010-07-04
you can download realplayer for linux [here]("https://player.helixcommunity.org/")

---

### Post by pommie on 2010-07-04
> **sxmaxchine said:**
> you can download realplayer for linux [here]("https://player.helixcommunity.org/")

The OP asked about a 64bit version, this post from the forum on the site you linked to,
-----------------------------------------------------------

**30 Nov, 2009** 		 		  |  dyek 	 			 	   	 		Hi Andrew,

There is currently nobody working on x86_64 porting project.

Could you try if the following command works in installing some i386  libraries needed (on x86_64 system) by the player?
$ sudo -i
# apt-get install ia32-libs
# dpkg -i RealPlayer11GOLD.deb
------------------------------------------------------------

So no 64bit, just a work around to get the 32bit version working :sad:

Cheers David

---

