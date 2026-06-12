---
title: "Can't see iTunes shared from Rhythmbox"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by nitewing98 on 2006-10-30
I've got a Mac with iTunes 7.0 on my home network. It has iTunes sharing enabled and the proper firewall port open, but I still can't find the shared lib in Rhythmbox 9.5 on my ubuntu machine.  However, I can see the Rhythmbox share in iTunes and it plays files OK.

I've installed all the avahi packages I could find in synaptic, restarted the system, disabled the Bonjour that Gizmo Project recommended for their iPhone service, but still can't get this to work.  I know others have said this works, but perhaps the new version of iTunes broke it?

Any help, ideas, or other input appreciated. No idea is too stupid, I'll try anything! 

Nitewing '98

---

### Post by Rollerbob on 2006-10-30
I'm having the same problem, and I believe Apple have changed something in iTunes 7 which has stopped sharing from working. 

I raised this on the Banshee IRC channel, and I think they're working on it.

---

### Post by nitewing98 on 2006-10-30
Can I assume, then, that Banshee has the same problem? Or does it work with iTunes 7?  Should I switch to Banshee since I now have:
a) Apple's Bonjour for Gizmo Project
b) Avahi for Rhythmbox
and I've heard they conflict with each other, is this true?

---

### Post by doclivingston on 2006-10-31
> **nitewing98 said:**
> Can I assume, then, that Banshee has the same problem? Or does it work with iTunes 7?

With iTunes 7 Apple delibrate broke support for all other clients, including iTunes 6. I'm not aware of any other client that can connect to an iTunes 7 share yet, but as soon as one open-source project gets support the others will shortly follow.


> Should I switch to Banshee since I now have:
a) Apple's Bonjour for Gizmo Project
b) Avahi for Rhythmbox
and I've heard they conflict with each other, is this true?

It isn't possible[0] to run multiple mDNS stacks (which Bonjour and Avahi are) on the one machine. Avahi has a compatability layer which supports the Bonjour/Howl API, so Gizmo could use it.

I'm not completely certain, but I think Banshee uses Avahi too.


[0] well technically you can, but be prepared for trouble like the two fighting and not working correctly while eating all your CPU. So don't.

---

### Post by nitewing98 on 2006-11-01
Thanks, Doc, for the reply.  I'm curious about one more thing, though.  From the Linux box, I can't see ANY of my Apple bonjour items.  But I can see linux items from the Apple.  I have no firewall on the ubuntu machine (since I'm behind a router/firewall) and have the ports on the Apple machine open for the services I'm using.  

What could be causing NONE of the bonjour items from the Ubuntu box from showing on the Mac?

---

