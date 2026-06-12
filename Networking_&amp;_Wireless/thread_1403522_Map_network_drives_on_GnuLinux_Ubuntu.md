---
title: "Map network drives on Gnu/Linux Ubuntu"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by jakslev on 2010-02-10
Hi Everybody, 

I have browsed the web to see if there are any details on this. There are some posts but they seem to be older than Ubuntu all of them!

I would therefore like to hear if there is a way to obtain the "good old" MS "map network drive" functionality. 

I would like it to be a pure Gnu/Linux solution that doesn't require Samba (if possible). My home setup is 2 Ubuntu 9.10 machines, 1 Ubuntu 9.10 Media PC and a Gnu/Linux-driven Popcorn Hour A-110 Media Tank. 

My hope would be to have the 2 laptops ending up with two nice icons on the desktop that links directly to a folder on the PH-A110 and the Media PC. 

I am at present able to go to Network and I see all the machines on my network. Reason why I am not happy with clicking and navigating is PURELY because it is less user-friendly.

---

### Post by dmizer on 2010-02-10
Please see the 4th link in my sig.

---

### Post by jakslev on 2010-02-10
You got a sig? Can't get them without a license in Spain..

Oh you meant signature - thought you talked about a Sig sauer ;o)

---

### Post by jakslev on 2010-02-10
> **dmizer said:**
> Please see the 4th link in my sig.

Okay - now I looked through the guide and I see it is 4 years old and has 425 comments. That is exactly what I don't want :D

Ubuntu should really focus on some of the key-things that professional users are using; and I am pretty sure that the "map network drive" feature is one of those things. Give us a script, a plugin an application that will do all this in GUI!!!! Not lines of code that needs to be terminalled in to the system and analyzed online before being edited and attempted again!

Stuff like that is what makes people continue believe that GNU/Linux is still only for super-nerds! 

Just my opinion of course  - and ABSOLUTELY no disrespect or ingratitude to the solution you gave me. I will investigate it in detail tomorrow and see if I can get it to apply to my Popcorn Hour as well :o)

---

### Post by dmizer on 2010-02-10
The solution (though 4 years old) still works. This should indicate to you that once configured, the NFS solution will not need to be tinkered with. In other words, set it up and forget about it.

Also, even though it's CLI, it's extremely easy to accomplish. Of course, you can map drives via GUI, but that means that you'd have to use a Windows network file system (CIFS) instead of a Linux network file system (NFS). Since you indicated you wanted a Linux based network file system, I offered the NFS howto I know works.

---

### Post by jakslev on 2010-02-11
> **dmizer said:**
> The solution (though 4 years old) still works. This should indicate to you that once configured, the NFS solution will not need to be tinkered with. In other words, set it up and forget about it.

Also, even though it's CLI, it's extremely easy to accomplish. Of course, you can map drives via GUI, but that means that you'd have to use a Windows network file system (CIFS) instead of a Linux network file system (NFS). Since you indicated you wanted a Linux based network file system, I offered the NFS howto I know works.

Yeah it does - just trying to figure how I can execute code on the PopCorn hour box. But thanks!

---

### Post by FountainDew on 2010-08-01
Is there really no "click-and-go" solution to something like mapping a network drive? I checked the fourth link and its not the kind of documentation I'm good at understanding... I'm just a concept artist trying to learn Ubuntu for the first time.

Is there a version for the little guy? Thanks.

P.S. This is the first thread in google search when searching how to map a network drive on Ubuntu. So I hope more research can help me figure this out.

---

### Post by dmizer on 2010-08-01
> **FountainDew said:**
> Is there really no "click-and-go" solution to something like mapping a network drive? I checked the fourth link and its not the kind of documentation I'm good at understanding... I'm just a concept artist trying to learn Ubuntu for the first time.

Is there a version for the little guy? Thanks.

P.S. This is the first thread in google search when searching how to map a network drive on Ubuntu. So I hope more research can help me figure this out.

What operating systems are involved with your set up? The OP had only Linux systems involved and NFS was a better choice. If you have Windows systems involved, then you'll probably be better off with the 6th link instead.

---

### Post by FountainDew on 2010-08-01
Ohh, that makes more sense. Thanks for that tip. I'll give it a shot. I'm using Ubuntu on a work machine, and have my files saved on an XP machine that doubles as an HTPC.

---

